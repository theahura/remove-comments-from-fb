# remove-comments-from-fb
Remove comments from facebook profile.

FB allows you to see all of your past comments. You may want to clear them out. 
  
Find your FB tag -- your tag is the part after facebook.com in the url when you go to your profile.

Go to this URL (replace YOURTAGHERE with the tag found above): https://www.facebook.com/YOURTAGHERE/allactivity?entry_point=www_top_menu_button&privacy_source=activity_log&log_filter=cluster_116&category_key=commentscluster
  
Hit f12 to open the developers console, and then hit Console.  
  
Drop this piece of code into the console:  

```javascript
function get_rid_of_em() {
    window.scrollBy(0, 10000) 

    const elements = document.querySelectorAll('[aria-label="Action options"]') // Or insert the classname you find in your inspector!
    for (const idx in elements) {
        try {
            elements[idx].click()
        } catch(e) {
            console.log(e)
        }
    }

    const deletes = document.querySelectorAll('[role="menuitem"]') // Or insert the classname you find in your inspector!
    for (const idx in deletes) {
        try {
            deletes[idx].click()
        } catch(e) {
            console.log(e)
        }
    }
}

setInterval(get_rid_of_em, 0.1)
```
Note that the class names may change may change.  
To fix this, replace those classnames by right clicking on the element on the screen that you want to click,  
hit 'Inspect Element' (which should go to the elements tab of the dev console), and look for 'class=X'. 

Also note that there may be an error window that shows the text 'Could not complete query'. Ignore it. It's just due to new comments not being totally loaded in yet. The script will keep working, regardless. At some point you should probably refresh to make sure the comments are actually being deleted, it doesn't show up otherwise.
