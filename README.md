# gh_pages_bookmarklet
A bookmarklet that opens a GH pages hosted branch of a repo in a new window.

How it works: Using some basic JavaScript, the script finds the username of the repo owner and repo name to build the .github.io address, and what directory it should open to (based on what directory of the repo you are looking at on GitHub). So if you are looking at the /images directory of a repo, it will open to *username.github.io/reponame/images*

Since linking JavaScript is not allowed with Github's markdown, you have to do a couple things to make the bookmarklet:

  1. Drag the 'Open in GH-pages' link (below) to your bookmark bar. Or, whatever means you use to save a bookmark.
  2. Edit the bookmark and replace the url with the script below.
  3. Test it on a repo with a GH-Pages branch. (Such as this one)
  4. Profit.



<a href="https://github.com/bkerickson/gh_pages_bookmarklet">Open in GH-Pages</a>


##### The Code
```
javascript:var http = 'http://';var github = '.github.io';var username = document.querySelector('.author a span').innerText;var ghPages = http + username + github + '/';var baseUrl = document.querySelectorAll('.breadcrumb [itemprop]');if(baseUrl){for(i=0, max=baseUrl.length;i<max;i++){if((username+github) != baseUrl[i].innerText){ghPages = ghPages + baseUrl[i].innerText + '/';}}};var endUrl = document.querySelectorAll('.breadcrumb .final-path');if(endUrl){for(i=0, max=endUrl.length;i<max;i++){ghPages = ghPages + endUrl[i].innerText + '/'}}window.open(ghPages);
```
