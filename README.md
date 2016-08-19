#M_E M (module_element modificator) style guide for web

MEm is a ideology for creating app's structure (web etc).

page = some modules
module = some elements

---FILE STRUCTURE---

index.html
/modules
	/news
	/weather
	/calendar
/templates
	index.html
	news.html
	search.html
	about.html

---FILES---

*html*

	<body>
		<div class="pageController">
		    <div class="row">
		    	<div class="row-cell">
		    		<div class="block moduleName" id="moduleName">
			    		<label>
			    			<input type="text" class="moduleName_name" id="moduleName_name" value="Some text">
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
				&.moduleName {}
			}
		}
	}


	/* header */
	...

	/* modules */
	.moduleName

		/* elements */
		.moduleName_name

	/* footer */
	...