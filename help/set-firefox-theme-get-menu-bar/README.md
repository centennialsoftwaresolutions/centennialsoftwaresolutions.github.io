# Change Firefox's background color, see the File, Edit, and View menu & understand what's happening

## How do I set the Firefox background color?
Change the current Theme to change Firefox's background color. Change the Theme by selecting **Tools > Extensions and Themes** and selecting Enable on a theme, like *Cheers - Soft*. You can also type **Ctrl + Shift + A** on Windows or Linux (or **Cmd + Shift + A** on a Mac) to set the theme. 

> **More precisely asked: How do I set the color of Firefox's chrome?** > Chrome (which doesn't mean the Google Chrome browser) is the "UI Container."

### The "UI Container"
The entire user interface (UI) that contains and surrounds the webpage is called **Browser Chrome**.

*Note: Going "chromeless" means hiding the "UI." When you want to "set Firefox's background color," you're setting the chrome color. Browsers call this the Theme. In Firefox you'd go to Tools > Extensions and Themes and select one.* The UI Container is in the Window Frame.

### The Window Frame / OS Shell (The Application Container)
The box on the computer screen that contains the entire Firefox program is called the **Application Window**. The Application Window is wrapped by the **Window manager**, which is part of the OS Shell.

The Window Manager handles the minimize, maximize, resize, move, and close buttons at the very top, along with a drop shadow around the edges. Incidentally, on Windows and Linux **Alt-space** brings up a drop-down in the upper left where these functions, move, resize can be selected. This is super useful if you don't want to leave the computer keyboard to adjust a window. *Alt-space doesn't work with Mac's Windows Manager, its handled differently.* > **Related: a "Content Container" displays the website in a Viewport**
> The physical space where the website is displayed is called the Viewport.

The Viewport is the blank physical canvas on the screen. A Rendering Engine (Gecko) is the software machine that paints onto the blank physical canvas.

* **The Rendering Engine (The "Drawer")** is the software engine that reads the downloaded code (HTML, JavaScript, CSS) and calculates how to draw all the boxes, text, etc. In Firefox, this engine is called **Gecko** (Google Chrome uses Blink, and Safari uses WebKit).
* **The Content Area / Viewport (The "Canvas")** is the physical space where Gecko paints the boxes, and "paints text" is called the Content Area or the Viewport.

The actual code for a website (like Google.com) is wrapped in `<html> ... </html>` tags on the website's server.

Firefox's `<browser>` tag is the blank "portal" like a TV screen. A website's code is not between `<browser>` tags, instead, Firefox points that tag at a web address (e.g., `<browser src="https://google.com" />`), and the rendering engine fetches the website's `<html>` code and projects it onto that `<browser>` screen.

**The hierarchy:**
An "Application Container" (a Window Frame / OS Shell instance) contains a "UI Container" (the chrome,) which contains a "Content Container" (a Viewport instance).

---

## Where are File, Edit, View, etc. in Firefox?
Firefox hides the File, Edit, View Menubar by default. "Right-click" on the "top" of the UI, where the tabs are, aka the Toolbar, and select **Menu Bar** to see (and use it).

> **More precisely asked: How do I get the Menu Bar tag to show up on the UI container?**
> The thing that owns the Menu Bar aka contains it is in the hierarchy of the XUL/HTML UI tags.

In Firefox’s source code, the Menu Bar is nested inside a specific hierarchy of containers.
From the outside in:

1. **The `<toolbox>` (The Master Top-Bar Container)**
   At the very top of the Firefox UI architecture is a master container called the `<toolbox>` (specifically, `<toolbox id="navigator-toolbox">`).
   This is the massive box that "owns" every toolbar at the top of your screen. The Menu Bar, the Tab Bar, the Navigation/Address Bar, and the Bookmarks Toolbar all live inside this one giant toolbox.
2. **The `<toolbar>` (The Menu Bar's Direct Wrapper)**
   Inside that master toolbox, the space dedicated specifically to the Menu Bar is a tag called `<toolbar>` (specifically, `<toolbar type="menubar" id="toolbar-menubar">`).
   Firefox changes the CSS visibility of the specific `<toolbar>` container from hidden to visible after selecting "Show Menu Bar" after "right-clicking" Firefox's chrome, aka Firefox's UI.
3. **The `<menubar>` (The Actual Menus)**
   The actual `<menubar>` tag (specifically, `<menubar id="main-menubar">`) is inside that toolbar wrapper is. This is the element that actually contains the "File," "Edit," "View," "History," etc. dropdown items.

> **Related: Where is the menubar code located?**
> Firefox doesn't list the code for every dropdown menu in the main window's text file. Instead, the `<menubar>` and its dropdowns are in a separate file called `browser-menubar.inc.xhtml`. When Firefox launches, the rendering engine grabs that separate file and injects it right into the middle of the `<toolbox>` structure.





