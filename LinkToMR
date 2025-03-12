// ==UserScript==
// @name         MuckRack Button (Force Injection)
// @namespace    http://tampermonkey.net/
// @version      1.7
// @description  Adds a button to open MuckRack
// @match        *://*/*
// @run-at       document-end
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    function forceAddButton() {
        console.log("🔄 Trying to add the MuckRack button...");

        // Remove any existing button first
        let oldBtn = document.getElementById("muckrack-btn");
        if (oldBtn) oldBtn.remove();

        let btn = document.createElement("button");
        btn.id = "muckrack-btn";
        btn.innerText = "Open MuckRack";
        btn.style.position = "fixed";
        btn.style.bottom = "20px";
        btn.style.right = "20px";
        btn.style.background = "#0073E6";
        btn.style.color = "white";
        btn.style.padding = "10px";
        btn.style.borderRadius = "5px";
        btn.style.cursor = "pointer";
        btn.style.zIndex = "100000";
        btn.onclick = function() {
            window.open("https://muckrack.com/mradmin/scraper/link/bookmarklet/?q=" + encodeURIComponent(window.location.href), "_blank");
        };

        document.body.appendChild(btn);
        console.log("✅ MuckRack button added!");
    }

    // Retry every 3 seconds in case the page modifies elements
    let attempts = 0;
    let interval = setInterval(() => {
        if (document.body) {
            forceAddButton();
            clearInterval(interval); // Stop after success
        }
        attempts++;
        if (attempts > 10) clearInterval(interval); // Stop after 10 tries
    }, 3000);
})();
