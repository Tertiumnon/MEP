#M-C_E-M (module-component_element-modificator) style guide for web

MEm is a ideology for creating app's structure (web etc).

module(page) = some modules
components = some elements

---FILE STRUCTURE---

/components
	/news
	/weather
	/calendar
/modules
	/main
		controller.js
		template.html
	/news
		controller.js
		template.html
	/about
		controller.js
		search.html
/skins
	/SkinName
		/css
		/js
		/img
index.html
app.js

---FILES---

*html*

	<body>
		<div class="ModuleName">
		    <div class="row">
		    	<div class="row-cell">
		    		<div class="block ComponentName" id="ComponentName">
			    		<label>
			    			<input type="text" class="ComponentName_name" id="ComponentName_name" value="Some text">
			    		</label>
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