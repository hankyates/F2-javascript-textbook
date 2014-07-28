#Async and Ajax

- [Async](http://www.slideshare.net/clutchski/writing-asynchronous-javascript-101)
- [AJAX](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started)



### Required Reading
- [Rockbot Article](http://rckbt.me/2014/05/understanding-async/)

### Class Code Snippets

```javascript
[
  {"name": "home", "content": "Stumptown hoodie synth, try-hard farm-to-table gentrify next level vegan food truck ethnic. Flexitarian cred tofu, ennui street art fanny pack scenester forage 8-bit Intelligentsia deep v vinyl twee. Disrupt wolf ugh, Etsy vinyl synth butcher organic blog Blue Bottle pug. Readymade banh mi you probably havent heard of them PBR Truffaut. Brooklyn Pitchfork sriracha vinyl biodiesel, Pinterest keytar fanny pack church-key. 8-bit Etsy yr normcore tote bag salvia, church-key pork belly raw denim irony synth. Bushwick Godard stumptown, hashtag Odd Future Pitchfork paleo occupy.Narwhal asymmetrical jean shorts mixtape PBR&B meh. Ugh put a bird on it artisan, polaroid craft beer sustainable distillery art party XOXO Brooklyn dreamcatcher DIY vegan tousled. 3 wolf moon Echo Park messenger bag locavore. Cardigan organic ugh, Wes Anderson banh mi sriracha Odd Future cliche Neutra wayfarers slow-carb leggings sustainable literally. Biodiesel hoodie flannel, paleo scenester gluten-free organic. Roof party four loko fingerstache, Carles hoodie jean shorts disrupt mixtape bitters 8-bit gastropub post-ironic blog swag art party. Cornhole hashtag wolf retro."},
  {"name": "articles", "content": "Tote bag photo booth viral you probably havent heard of them. Art party Odd Future mumblecore, Echo Park Marfa fashion axe iPhone leggings cardigan. Godard Austin beard disrupt shabby chic. Mumblecore leggings salvia, literally skateboard flannel squid mixtape semiotics irony deep v 8-bit. Hashtag paleo Tonx Marfa try-hard banjo. Trust fund wolf chia seitan, biodiesel drinking vinegar blog. Squid banjo XOXO, meggings Vice mixtape viral cray bespoke scenester Schlitz 90s synth leggings."},
  {"name": "portfolio", "content": "Tofu kitsch wolf DIY, seitan blog chambray gentrify wayfarers Carles PBR iPhone try-hard. Fixie squid fashion axe, street art skateboard pug vegan wayfarers banjo irony cardigan drinking vinegar. Truffaut High Life fixie organic deep v. Tousled Schlitz butcher slow-carb. Lo-fi Austin +1 8-bit, polaroid ugh tote bag flannel ethnic tousled yr bespoke Marfa Banksy. Fixie Banksy asymmetrical locavore hashtag ennui cornhole disrupt. Helvetica organic quinoa kitsch roof party stumptown."},
  {"name": "more", "content": "90s Pinterest XOXO occupy Neutra, pop-up PBR flexitarian raw denim viral ennui High Life letterpress. Echo Park selfies next level tattooed pop-up mumblecore. Fap synth flannel slow-carb mustache, wolf viral. Dreamcatcher twee ethnic, occupy drinking vinegar Neutra master cleanse literally. Scenester cornhole lomo Truffaut. McSweeneys Shoreditch flexitarian Marfa ugh selvage. Sriracha kale chips wolf umami gastropub."}
]
```

```javascript
var fs = require('fs');
var content;

fs.readFile('wat.json', {encoding: 'utf-8'}, function (err, data) {
  if (err) throw err;
  content = JSON.parse(data);

  content.forEach(function(tab) {
    console.log(tab.name);
    console.log(tab.content);
  });

});
```
