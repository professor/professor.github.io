---
layout: post
title: "Legitimate cross site scripting (CSX) with AJAX"
date: 2009-07-14 15:50
comments: false
categories:    
alias: [/journal/2009/7/14/legitimate-cross-site-scripting-csx-with-ajax.html]
---
How do you do legitimate cross site scripting?

If you control the servers involved, this is how you can do cross site scripting with AJAX.
 

I recently came across a situation where I wanted to do an AJAX load from one server to another server. Internally to our campus, our students use a wiki and a ruby on rails web application. I wanted information contained in our rails application to show up on the wiki. My first impulse was to use jquery's load method, however, I received the following error:

<red>Access to restricted URI denied" code: "1012</red>

My first work around is just to avoid the AJAX load and use an iframe. However, inspiration hit me a few weeks ago and I tried a different solution. Since the AJAX load can retrieve information from the same website, maybe I should request a special url on the same machine and use apache to hide the fact that the content is coming from a different domain name. This can be accomplished with the apache ProxyPass command.

Let me give a concrete example. Say you have two websites: a static site that serves html pages through apache from the filesystem (http://static.sv.cmu.edu) and a dynamic site using an application server with a database (http://dynamic.sv.cmu.edu). You want some of the information from the dynamic site to show up on the static site. You want to allow users to add comments to a static webpage where the comments are rendered by the dynamic site.
Your first attempt might be:
```
$('#comments').load('http://dynamic.sv.cmu.edu/comments');
```
Which results in the error.
In static.sv.cmu.edu's httpd.conf file add the following line:
```
ProxyPass /comments http://dynamic.sv.cmu.edu/comments
```
Now from your browser window, test to see if you can access the dynamic data from the static machine: http://static.sv.cmu.edu/comments should give you the same information as would http://dynamic.sv.cmu.edu/comments
Now your AJAX code will work.
```javascript
<script type="text/javascript" src="http://code.jquery.com/jquery-latest.js"></script>
<script type="text/javascript">
 //<![CDATA[
$(document).ready(function(){
 $('#comments').load('http://dynamic.sv.cmu.edu/comments');
});
//]]>
</script>  
```


  
