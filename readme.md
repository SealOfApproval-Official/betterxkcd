Just copy & paste this code or download the file and put it in tampermonkey as a new script.

```javascript
    // ==UserScript==
    // @name         Better XKCD
    // @namespace    *://xkcd.com/
    // @version      0.1
    // @description  Adds the click-text to the screen!
    // @author       SealProgrammer
    // @match        *://xkcd.com/*
    // @match        *://what-if.xkcd.com/*
    // @exclude      *://xkcd.com/archive/
    // @icon         https://www.google.com/s2/favicons?sz=64&domain=tampermonkey.net
    // @grant        none
    // ==/UserScript==

    (function() {
        'use strict';

        const comic = document.getElementById('comic');
        const comics = document.getElementsByClassName('illustration');
        if(comic) {
            let p = document.createElement('p');
            p.append(comic.children[0].title);
            comic.append(p);
        } else if(comics) {
            for(let i=0;i<comics.length; i++) {
                let c = document.createElement('center');
                let ital = document.createElement('i');
                ital.style.fontSize = "small";
                ital.append('"' + comics[i].title + '"');
                c.append(ital);
                comics[i].parentElement.insertBefore(c, comics[i].nextSibling);
                comics[i].parentElement.insertBefore(document.createElement('br'), c.nextSibling)
            }
        }
})();
```
