# remove-comments-from-fb
Remove comments from facebook profile.

FB allows you to see all of your past comments. You may want to clear them out. 
  
Go to (replace YOURTAGHERE): https://www.facebook.com/YOURTAGHERE/allactivity?entry_point=www_top_menu_button&privacy_source=activity_log&log_filter=cluster_116&category_key=commentscluster
  
Hit f12 to open the developers console, and then hit Console.  
  
Drop this piece of code into the console:  

```javascript
function get_rid_of_em() {
    window.scrollBy(0, 10000) 

    elements = document.getElementsByClassName('oajrlxb2 tdjehn4e qu0x051f esr5mh6w e9989ue4 r7d6kgcz rq0escxv nhd2j8a9 j83agx80 p7hjln8o kvgmc6g5 cxmmr5t8 oygrvhab hcukyx3x jb3vyjys rz4wbd8a qt6c0cv9 a8nywdso i1ao9s8h esuyzwwr f1sip0of lzcic4wl l9j0dhe7 abiwlrkh p8dawk7l bp9cbjyn s45kfl79 emlxlaya bkmhp75w spb7xbtv rt8b4zig n8ej3o3l agehan2d sk4xxmp2 taijpn5t tv7at329 thwo4zme') // Or insert the classname you find in your inspector!
    for (element in elements) {
        try {
            elements[element].click()
            console.log('clicked?')
        } catch(e) {
            console.log(e)
        }
    }

    deletes = document.getElementsByClassName('oajrlxb2 g5ia77u1 qu0x051f esr5mh6w e9989ue4 r7d6kgcz rq0escxv nhd2j8a9 j83agx80 p7hjln8o kvgmc6g5 oi9244e8 oygrvhab h676nmdw cxgpxx05 dflh9lhu sj5x9vvc scb9dxdr i1ao9s8h esuyzwwr f1sip0of lzcic4wl l9j0dhe7 abiwlrkh p8dawk7l bp9cbjyn dwo3fsh8 btwxx1t3 pfnyh3mw du4w35lb') // Or insert the classname you find in your inspector!
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
}

setInterval(get_rid_of_em, 0.1)
```
Note that the class names may change may change.  
To fix this, replace those classnames by right clicking on the element on the screen that you want to click,  
hit 'Inspect Element' (which should go to the elements tab of the dev console), and look for 'class=X'. 

Also note that there may be an error window that shows the text 'Could not complete query'. Ignore it. It's just due to new comments not being totally loaded in yet.The script will keep working, regardless.
