---
layout: page
title: "Contact Us"
permalink: /contact/
---

<form id="contact-form"
      action="https://contact-email-worker.centennialsoft.workers.dev"
      method="POST"
      class="contact-form"
      novalidate>
  <label>
    Name
    <input type="text" name="name" required placeholder="Arthur Dent">
  </label>

  <label>
    Email
    <input type="email" name="email" required placeholder="you@company.com">
  </label>

  <label>
    Message
    <textarea name="message" rows="6" required placeholder="I'm trying to..."></textarea>
  </label>

  <!-- Honeypot -->
  <input type="text" name="_gotcha" tabindex="-1" autocomplete="off" style="display:none">

  <!-- Turnstile widget -->
  <div class="cf-turnstile" data-sitekey="0x4AAAAAABunTwkI4HUAc6Xb"></div>

  <button type="submit">Send</button>
  <p class="form-status" role="status" aria-live="polite"></p>
</form>

<script src="https://challenges.cloudflare.com/turnstile/v0/api.js" async defer></script>

<script>
(function () {
  const form = document.getElementById('contact-form');
  if (!form) return;

  const status = form.querySelector('.form-status');
  const button = form.querySelector('button[type="submit"]');
  const setStatus = (msg, ok) => {
    status.textContent = msg;
    status.classList.remove('ok','err');
    status.classList.add(ok ? 'ok' : 'err');
  };

  form.addEventListener('submit', async (e) => {
    e.preventDefault();
    if (!form.checkValidity()) {
      setStatus('Please fill out all required fields.', false);
      form.reportValidity && form.reportValidity();
      return;
    }

    // Ensure Turnstile token exists
    const tokenInput = form.querySelector('input[name="cf-turnstile-response"]');
    if (!tokenInput || !tokenInput.value) {
      setStatus('Please complete the verification.', false);
      return;
    }

    button.disabled = true;
    setStatus('Sending…', true);

    try {
      const data = new FormData(form);   // no custom headers → no CORS preflight
      const res = await fetch(form.action, { method:'POST', body:data });

      if (res.ok) {
        form.reset();
        window.turnstile && window.turnstile.reset && window.turnstile.reset();
        setStatus('Thanks! We received your message.', true);
      } else {
        const json = await res.json().catch(()=> ({}));
        setStatus(json.error || 'Something went wrong. Please try again.', false);
        window.turnstile && window.turnstile.reset && window.turnstile.reset();
      }
    } catch {
      setStatus('Network error. Please try again.', false);
      window.turnstile && window.turnstile.reset && window.turnstile.reset();
    } finally {
      button.disabled = false;
    }
  });
})();
</script>
