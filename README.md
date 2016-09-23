#MCem style guide

MCem (Module Component element modificator) is a ideology for creating app's structure (web etc).

Where
* module = some components
* component = some elements

---NAMES---

Lenght of all names would be about 7-9 symbols.

Names of modules and components would start with a capital letter.

---FILE STRUCTURE---

* /components
    /news
    /weather
    /calendar
* /modules
    /main
      controller.js
      template.html
    /news
      controller.js
      template.html
* /about
    controller.js
    search.html
* /skins
    /SkinName
      /css
      /js
      /img
* index.html
* app.js

---FILES---

*html*

	<body>
		<div class="module ModuleName">
		    <div class="row">
		    	<div class="row-cell">
		    		<div class="component ComponentName" id="ComponentName">
			    		<div class="form-group name">
			    			<label for="ComponentName_name">Name</label>
			    			<input type="text" class="ComponentName_name_input" id="ComponentName_name_input" value="Some text" />
			    		</div>
		    		</div>
		    	</div>
		    </div>
		</div>
	</body>

*css/less*

	/* default html elements */
	body {}
	input {}

	/* default elements */
	.row {
		.row-cell {
			.block {
				/* exception */
				&.componentName {}
			}
		}
	}


	/* header */
	...

	/* components */
	.componentName

		/* elements */
		.componentName_name

	/* footer */
	...
