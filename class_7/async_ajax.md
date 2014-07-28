#Async and Ajax
- [$.ajax](http://api.jquery.com/jquery.ajax/)
- [$.getJSON](http://api.jquery.com/jquery.getjson/)
- [node fs.readFile](http://nodejs.org/api/fs.html#fs_fs_readfile_filename_options_callback)

### Required Reading
- [Rockbot Async Article](http://rckbt.me/2014/05/understanding-async/)
- [MDN AJAX Article](https://developer.mozilla.org/en-US/docs/AJAX)
- [Promises](https://www.promisejs.org/)

### Class Code Snippets

#### content.json
```javascript
[
  {"name": "home", "content": "Stumptown hoodie synth, trRoof party four loko fingerstache, Carles hoodie jean shorts disrupt mixtape bitters 8-bit gastropub post-ironic blog swag art party. Cornhole hashtag wolf retro."},
  {"name": "articles", "content": "Tote bag photo bol cray bespoke scenester Schlitz 90s synth leggings."},
  {"name": "portfolio", "content": "Tofu kitsch wolf DIYa organic quinoa kitsch roof party stumptown."},
  {"name": "more", "content": "90s Pinterest XOXO ocmblecore.
```
#### getContent.js
```javascript
var fs = require('fs');
var content;

fs.readFile('content.json', {encoding: 'utf-8'}, function (err, data) {
  if (err) throw err;
  content = JSON.parse(data);

  content.forEach(function(tab) {
    console.log(tab.name);
    console.log(tab.content);
  });

});
```
