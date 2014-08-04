# ActionBarExtras

This module provides some extra functionality to configure the ActionBar that Titanium doesn't offer. It lets you set a subtitle to the ActionBar title, it forces to show the Overflow menu button on devices with hardware menu buttons and gives you the opportunity to change the ActionBar font (of both, title and subtitle or separately).

![example](documentation/example.png)

## Features
  * Title and Subtitle
  * Sharing Action Provider
  * force overflow
  * backgroundColor
  * custom fonts
  * font color
  * disable icon

## Get it [![gitTio](http://gitt.io/badge.png)](http://gitt.io/component/com.alcoapps.actionbarextras)
Download the latest distribution ZIP-file and consult the [Titanium Documentation](http://docs.appcelerator.com/titanium/latest/#!/guide/Using_a_Module) on how install it, or simply use the [gitTio CLI](http://gitt.io/cli):

`$ gittio install com.alcoapps.actionbarextras`

## Using it

First require it:

	var abextras = require('com.alcoapps.actionbarextras');

At this point the feature for forcing the "menu overflow" has been attached to your Activity, so if that's the only thing you were looking for, you're set.

To set the ActionBar custom features, simply call the **setExtras** method:

```javascript
// setting extras
abextras.setExtras({
    title:'This is the title',
    subtitle:'This is the subtitle',
    font: 'my_custom_font.otf',
    backgroundColor:'#ff4f00',
    color: 'red'
});
```

To add a sharing action to the ActionBar call `addSharingAction`:
```javascript
// this should be done within the onCreateOptionsMenu
// because we need to pass a reference to the menu

activity.onCreateOptionsMenu = function(e){

    // at first, create a basic share intent
    var intent = Ti.Android.createIntent({
       action: Ti.Android.ACTION_SEND,
       type: 'text/plain'
    });
    intent.putExtra(Ti.Android.EXTRA_TEXT, 'Hello world!');

    // now pass over the menu and the intent like this
    abextras.addShareAction({
        menu: e.menu,
        intent: intent
    });
};
```

## Contribuitors

* [Ricardo Alcocer](https://github.com/ricardoalcocer)
* [Timan Rebel](https://github.com/timanrebel)
* [Manuel Lehner](https://github.com/manumaticx)

## License
MIT License - [http://alco.mit-license.org](http://alco.mit-license.org)
