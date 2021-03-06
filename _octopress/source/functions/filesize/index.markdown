---
layout: page
title: "JavaScript filesize function"
comments: true
sharing: true
footer: true
sidebar: false
alias:
- /functions/view/filesize:401
- /functions/view/filesize
- /functions/view/401
- /functions/filesize:401
- /functions/401
---
<!-- Generated by Rakefile:build -->
A JavaScript equivalent of PHP's filesize

{% codeblock filesystem/filesize.js lang:js https://raw.github.com/kvz/phpjs/master/functions/filesystem/filesize.js raw on github %}
function filesize (url) {
  // http://kevin.vanzonneveld.net
  // +   original by: Enrique Gonzalez
  // +      input by: Jani Hartikainen
  // +   improved by: Kevin van Zonneveld (http://kevin.vanzonneveld.net)
  // +   improved by: T. Wild
  // %        note 1: This function uses XmlHttpRequest and cannot retrieve resource from different domain.
  // %        note 1: Synchronous so may lock up browser, mainly here for study purposes.
  // *     example 1: filesize('http://kevin.vanzonneveld.net/pj_test_supportfile_1.htm');
  // *     returns 1: '3'
  var req = this.window.ActiveXObject ? new ActiveXObject("Microsoft.XMLHTTP") : new XMLHttpRequest();
  if (!req) {
    throw new Error('XMLHttpRequest not supported');
  }

  req.open('HEAD', url, false);
  req.send(null);

  if (!req.getResponseHeader) {
    try {
      throw new Error('No getResponseHeader!');
    } catch (e) {
      return false;
    }
  } else if (!req.getResponseHeader('Content-Length')) {
    try {
      throw new Error('No Content-Length!');
    } catch (e2) {
      return false;
    }
  } else {
    return req.getResponseHeader('Content-Length');
  }
}
{% endcodeblock %}

 - [view on github](https://github.com/kvz/phpjs/blob/master/functions/filesystem/filesize.js)
 - [edit on github](https://github.com/kvz/phpjs/edit/master/functions/filesystem/filesize.js)

### Example 1
This code
{% codeblock lang:js example %}
filesize('http://kevin.vanzonneveld.net/pj_test_supportfile_1.htm');
{% endcodeblock %}

Should return
{% codeblock lang:js returns %}
'3'
{% endcodeblock %}


### Other PHP functions in the filesystem extension
{% render_partial _includes/custom/filesystem.html %}
## Legacy comments
These were imported from our old site. Please use disqus below for new comments
<div style="overflow-y: scroll; max-height: 500px;">
{% render_partial functions/filesize/_comments.html %}
</div>
