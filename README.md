# remove-comments-from-fb
Remove comments from facebook profile.

FB allows you to see all of your past comments. You may want to clear them out. 
  
Go to (replace YOURTAGHERE): https://www.facebook.com/YOURTAGHERE/allactivity?entry_point=www_top_menu_button&privacy_source=activity_log&log_filter=cluster_116&category_key=commentscluster
  
Hit f12 to open the developers console, and then hit Console.  
  
Drop this piece of code into the console:  

```javascript
window.scrollBy(0, 10000) // Do this a bunch to load the relevant dom elements.

elements = document.getElementsByClassName('_42ft _42fu _4-s1 _2agf _4o_4 _p _42gx')
for (element in elements) {
	try {
    	elements[element].click()
		console.log('clicked?')
    } catch(e) {
		console.log(e)
	}
}
deletes = document.getElementsByClassName('_54nc')
for (d in deletes) {
	try {
		if (deletes[d].innerHTML.includes('Report')) {
			console.log('Skipping report button');
        } else {
			deletes[d].click()
			console.log('Deleted');
        }
    } catch(e) {
		console.log(e)
    }
}
```
Note that the class names may change may change.  
To fix this, replace those classnames by right clicking on the element on the screen that you want to click,  
hit 'Inspect Element' (which should go to the elements tab of the dev console), and look for 'class=X'. 

Further, note that you will have to do some scrolling to load all of the relevant buttons, so this may still take some time.
