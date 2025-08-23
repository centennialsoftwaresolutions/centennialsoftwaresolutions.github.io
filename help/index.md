---
layout: default
title: Help
---

<!-- Search UI -->
<div id="kb-search" style="max-width: 720px; margin: 1rem 0;">
  <label for="q" style="display:block; font-weight:600; margin-bottom:.25rem;">Search help</label>
  <input id="q" type="search" placeholder="Type to search…" style="width:100%; padding:.65rem; border:1px solid #ddd; border-radius:.5rem;">
  <div id="results" aria-live="polite" style="margin-top:1rem;"></div>
</div>

<!-- Lunr.js (CDN) -->
<script src="https://cdn.jsdelivr.net/npm/lunr/lunr.min.js"></script>

<script>
(function () {
  var q = document.getElementById('q');
  var resultsEl = document.getElementById('results');
  var base = "{{ '' | relative_url }}"; // respects baseurl
  var docs = [];
  var idx;

  // Render helpers
  function esc(s){ return (s||'').replace(/[&<>"]/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c])); }
  function snippet(txt, term){
    if(!txt) return '';
    var i = txt.toLowerCase().indexOf(term.toLowerCase());
    if(i < 0) return esc(txt.slice(0, 160)) + '…';
    var start = Math.max(0, i - 60), end = Math.min(txt.length, i + term.length + 60);
    var pre = esc(txt.slice(start, i));
    var hit = '<mark>' + esc(txt.slice(i, i+term.length)) + '</mark>';
    var post = esc(txt.slice(i+term.length, end));
    return (start>0?'…':'') + pre + hit + post + (end<txt.length?'…':'');
  }

  function render(list, term){
    if(!list.length){ resultsEl.innerHTML = '<p>No results found.</p>'; return; }
    resultsEl.innerHTML = list.map(function (ref) {
      var d = docs.find(x => x.url === ref.ref) || {};
      return (
        '<div style="padding:.75rem 0;border-top:1px solid #eee;">' +
          '<a href="'+ esc(d.url) + '"><strong>'+ esc(d.title || d.url) +'</strong></a>' +
          '<div style="color:#555; font-size:.95rem; margin-top:.25rem;">' + snippet(d.content || '', term) + '</div>' +
        '</div>'
      );
    }).join('');
  }

  // Fetch index and build lunr
  fetch(base + '/pages.json')
    .then(r => r.json())
    .then(function (json) {
      docs = json;
      idx = lunr(function () {
        this.ref('url');
        this.field('title', { boost: 10 });
        this.field('content');
        json.forEach(doc => this.add(doc), this);
      });
    });

  // Simple debounce
  var t;
  q.addEventListener('input', function () {
    clearTimeout(t);
    var term = q.value.trim();
    if(!term){ resultsEl.innerHTML = ''; return; }
    t = setTimeout(function () {
      try {
        var hits = idx.search(term + '*'); // prefix matching
        render(hits, term);
      } catch(e){
        // If lunr throws on special chars, fall back to contains filter
        var fallback = docs.filter(d => (d.title+d.content).toLowerCase().includes(term.toLowerCase()))
                           .map(d => ({ ref: d.url }));
        render(fallback, term);
      }
    }, 120);
  });
})();
</script>

# Help

<ul>
  {% for page in site.html_pages %}
    {% if page.path contains '/' %}
      {% unless page.url contains 'style.css'
            or page.url contains '/about/'
            or page.url == '/help/'
            or page.url == '/help/index.html'
            or page.url == '/index.html'
            or page.url == '/404.html' %}
        {% assign basename = page.url | split:'/' | last | replace:'.html','' %}
        <li><a href="{{ page.url | relative_url }}">{{ basename }}</a></li>
      {% endunless %}
    {% endif %}
  {% endfor %}
</ul>
