#MCem style guide

MCem (Module Component element modificator) is a ideology for creating app's structure (web etc).

Where

* module = some components
* component = some elements

---NAMES---

* Lenght of all names would be about 7-9 symbols.
* Names of modules and components would start with a capital letter.
* Names may include "_" as separators.
* Set "-" between elements and modificators in file names.

Examples (files):

* email_form.js
* email_form-theme-light.css
* email_form-theme-dark.css

Examples (html):

* Module: <div name="module About" id="module_About"></div>
* OR use other style (HTML5 tag "section"): <section name="About" id="About"></section>
* Component: <div class="EmailForm" id="EmailForm"></div>
* Element: <input class="firstname" id="EmailForm-firstname"></div>
* Modificator: <input class="firstname hide" id="EmailForm-firstname"></div> // hide

---FILE STRUCTURE---

* /components
  * /news
  * /weather
  * /calendar
* /modules
  * /main
    * controller.js
    * template.html
  * /news
    * controller.js
    * template.html
* /about
  * controller.js
  * search.html
* /skins
  * /SkinName
    * /css
    * /js
    * /img
* index.html
* app.js