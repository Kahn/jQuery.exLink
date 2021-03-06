jQuery exLink
===

The jQuery exLink plugin simplifies the task of opening external links and documents in a new tab. This plugin supports configurable options, document type filtration, dialog warnings to notify users that they are leaving the site or opening a document, and customizable messages/visuals. 

This plugin is distributed as is, and does not include any official support. However, if you come across an issue or need any assistance deploying exLink, just let me know! I'd be happy to help.

Also, if you'd like to contribute to the plugin, that's cool too. Just fork and start creating!

**Current Version:** 2.3.0

**Release Date:** November 20, 2015


Usage
===

exLink is incredibly light weight, and very easy to setup. This plugin will function without anything beyond jQuery.



1). Include the exLink Javascript, and optionally the stylesheet. Don't include the stylesheet if you will not be using the modal warnings (linkWarning: false, fileWarning: false)

```javascript

<script type="text/javascript" src="/exLink/jquery.exLink.js"></script>


```

```html

<link rel="stylesheet" href="/exLink/jquery.exLink.css">

```

To download using npm, just run this command from your project directory:

```javascript

sudo npm install exlink

```

2). After the required files have been included in your document, usage is incredibly easy! For the default case, just initiate the exLink plugin. This uses all of the default options.

```javascript

exLink.init();

```

In versions prior to 2.1.0, initaite exLink with the '$.fn.' declaration.

```javascript

$.fn.exLink();

```

If you'd like to customize the plugin (which most people do), then you'll need to specify the options you want to change. Here is an initialization with ALL possible options. 

```javascript

exLink.init({
 	protocols: ['http', 'https'],
	filetypes: ['pdf', 'xls', 'docx', 'doc', 'ppt', 'pptx'],
	linkWarning: true,
	hostCompare: false,
	noFollow: false,
	fancyBoxIgnore: true,
	linkCallback: null,
    fileCallback: null,
    gaTracking: false,
    gaTrackLabel: 'External Links',
    gaTrackOld: false,
	linkWarningBody: 'You are about to leave this website and navigate to the link below. Would you like to continue?',
	fileWarning: true,
	fileWarningBody: 'You are about to open the file below. Do you wish to continue?',
	dialogConfirm: '#006600',
	dialogCancel: '#CC0000',
	dialogConfirmText: '#fff',
	dialogCancelText: '#fff',
	dialogCancelButton: 'Cancel',
	dialogConfirmButton: 'Continue',
	modalWidth: "320px",
	modalHeight: "240px",
	modalDisplayBG: true,
	externalColor: '',
    documentColor: '',
    clickedColor: '',
    newWindow: false,
    widthWindow: '500',
    heightWindow: '400',
    titleWindow: 'exLink by YupItsZac.com'
});

```

Options
===

######Functionality Options

**protocols** - Specify specific protocols you would like to catch. This is useful if you only want to warn about non-secure links, but don't care about secure links. By default, http and https protocols are enabled. Ex: protocols: ['http', 'https', 'ftp', 'ftps']

**filetypes** - Specify a an array of document formats you want to catch. Similar to protocols, but matching the extension of the document linked. Ex: filetypes: ['doc', 'pdf', 'xlx', 'docx', 'ppt'] NOTE: Do not include the leading dot

**navigateCallback** - New in version 2.3.0, if set, this exLink will make the callback to the desired function with the element clicked, if the link was a file (1) or external website (2), and if a warning dialog was displayed (true) or not (false). 

**navigateState** - New in version 2.3.0, this options enables a callback for each link opened by exLink. Included in the callback is the link clicked and if the link was opened in a new window (1) or a new tab (2).

**linkWarning** - Removed in version 2.3.0: Display a warning notifying the user that they are navigating to an external link. By default, this is enabled. Ex: linkWarning: true

**fileWarning** - Removed in version 2.3.0: Similar to linkWarning, this notifies the user that they are opening a document and asks for confirmation ot proceed. By default, this is also enabled. Ex: fileWarning: true

**hostCompare** - New in version 1.2.0, set this as true to identify external links based on a hostname comparison. If false, which is the default case, exLink will identify the external links based on protocol information. By default, this is disabled. Ex: hostCompare: true
 
**noFollow** - New in version 1.2.5, set this to true to prevent search engines from following the identified external URLs. If false, search engines will recurse as expected thorugh the external links. By default, this is false. Ex: noFollow: false

**fancyBoxIgnore** - New in version 1.2.6, this enables pages to still use the popular Fancy Box plugin to open content in modal dialogs without opening in a new tab as well. Set this to true if you use the fancyBox plugin, and to false if you do not. Set to true by default. Ex: fancyBoxIgnore: true

**gaTracking** - Introduced in version 2.0.2, this option enables a Google Analytics event to trigger when any of the links are clicked. Classic and Universeral analytics supported. This is a boolean value set to false by default. Ex: gaTracking: false

**gaTrackLabel** - If you you enable gaTracking, set this to customize the event label. This is a string value set to 'External Links' by default. Ex: gaTrackLabel: 'External Links'

**gaTrackOld** - Set this to true if you are using the classic version of Google Analytcis (ga.js). If you are using the new universal tracking (analytics.js), you don't need to use this option. This is a boolean value set to false by default. Ex: gaTrackOld: false

**newWindow** - New in version 2.1.0, when set to true, exLink forces all external links and documents to open in a new window, not the default 'tab' behavior. Ex: newWindow: true

**widthWindow** - The width of the new window specified via the newWindow option. String value. Ex: widthWindow: '500'

**heightWindow** - The height of the window specified via the newWindow option. String value. Ex: heightWindow: '400'

*titleWindow** - The title of the window specified via the newWindow option. String value. Ex: titleWindow: 'My Window Title'

######Visual Options

**linkWarningBody** - This is a string containing the message you would like to display to users when they click an external link. linkWarning must be set to true for this to work. Al HTML markup is accepted.

**fileWarningBody** - This is a string containing the message you would like to display to users when they click on a document link. fileWarning must be set to true for this to work. All HTML markup is accepted.

**dialogConfirm** - The background color of the 'confirm' button on the warning dialog. This is a hex code set to #006600 by default.

**dialogCancel** - The background color of the 'cancel' button on the warning dialog. This is a hex code set to #CC0000 by default.

**dialogCancelText** - The font color of the 'cancel' button on the warning dialog. This is a hex code set to #fff by default.

**dialogConfirmText** - The font color of the 'confirm' button on the warning dialog. This is a hex code set to #fff by default.

**dialogCancelButton** - The text label of the 'cancel' button on the warning dialog. This is a string set to 'Cancel' by default.

**dialogConfirmButton** - The text label of the 'confirm' button on the warning dialog. This is a string set to 'Continue' by default.

**modalWidth** - The width of the warning box. This is a string. Ex: modalWidth: "500px"

**modalHeight** - The height of the warning box. This is a string. Ex: modalHeight: "200px"

**modalDisplayBG** - New in version 1.2.3, if set to true, this will display the dark background over the page when the modal is present. This is a boolean set to true by default. Ex: modalDisplayBG: true

**externalColor** - New in version 1.2.7, this option lets you change the color of all external links identified. If left blank, this defaults to the colors defined in the stylesheet or by the browser. This is a hex code left blank by default. Ex: externalColor: #0645AD

**documentColor** - New in version 1.2.7, this option lets you change the color of all document links identified. If left blank, this defaults to the colors defined in the stylesheet or by the browser. This is a hex code left blank by default. Ex: externalColor: #0645AD

**clickedColor** - New in version 1.2.8, this option lets you change the color of all external and document links that have been clicked. If left blank, this defaults to the colors defined in the stylesheet or by the browser. This is a hex code left blank by default. Ex: externalColor: #0645AD

######Deprecated Options & Methods

**linkCallback** - Removed in version 2.3.0: Added in version 1.2.7, this enables developers to execute a function each time an external link has been clicked. This returns the object clicked, and an indication if a warning dialog was displayed or not. This is null by default. (Replaced by navigateCallback) Ex: linkCallback: callback

**fileCallback** - Removed in version 2.3.0: New in version 1.2.7, this enables developers to execute a function each time a document link has been clicked. This returns the object clicked, and an indication if a warning dialog was displayed or not. This is null by default. (Replaced by navigateCallback) Ex: fileCallback: docCallback

**exLink.init('re')** - Removed in version 2.3.0: The need to re-initialize exLink after new content has been added via AJAX is no longer necessary. exLink automatically detects these changes.

exLink Demo & Other Stuffs
==

jQuery.exLink has had more downloads than I expected, which is pretty cool! Almost 800 right now. I've put together a basic demo (which I probably should've done from the beginning) and published it on my website. Also, exLink has been featured or shared to some other websites, and I feel like I should say thanks.

- [exLink on npm](http://www.npmjs.com/package/exlink)
- [exLink on jQuer.in](http://www.jquer.in/helpful-jquery-plugins-for-html5-websites/exlink/)
- [exLink on Github](http://www.github.com/YupItsZac/jQuery.exLink) / Just in case you aren't reading this on Github

Also, if you find this plugin useful (or even if you don't), please connect with me!

- [Github](http://www.github.com/YupItsZac)
- [Twitter](http://www.twitter.com/YupItsZac)
- [LinkedIn](http://www.linkedin.com/in/yupitszac)
- [Facebook](http://www.fb.me/yupitszac)


Notes & Hints
===

1). In order for exLink to determine which links are external and which are internal using the protocol detection option, use relative paths for all of your internal links. Otherwise, all of your internal links will also be detected as external. 

```html

	<a href="/path/to/internal/resource">Internal Link</a>

```

2). If you decide to use the hostname detection over the protocol detection, you will need to ensure you use absolute urls for all of your internal links. Otherwise, your internal links will be detected as external since the hostname comparison will return false. 

```html

	<a href="http://www.external.link">External Link</a>

	<a href="http://www.internal.link">Internal Link</a>

```

3). DEPRECATED 2.3.0: If you are loading content via AJAX or will be adding any content after exLink has been initialized, you'll need to reinitialize the plugin. If you specify the string 're' as your options, then the options will not be affected and all external links/documents will be redetected to account for your new additions. 

```javascript

	$.fn.exLink('re');

```

4). Prior to version 2.1.0, if you want to target a single internal link as well, simply add the appropriate class to the link in your content. 

```html

   <a href="#" class="exLink">Linky Link</a>

```

5). The introduction of the noFollow option is geared towards sites that aren't heavily reliant upon SEO. It is not reccommended you use this option unless the external websites you're linking to do not provide any value for your content (this is very rare).

6). Prior to version 2.3.0, if you choose to use the linkCallback or fileCallback options, your callback function may look something like this:

```javascript

  //obj is the object that was clicked. warning is true if a warning dialog was displayed, false if not.
  function callback(obj, warning)  {
  	console.log('The object clicked: '+obj);
  	console.log('Warning displayed: '+warning);
  }
```

7). After version 2.3.0, if you choose to use the navigateCallback option, your callback might look something like this:

```javascript

 //obj is the object clicked
 //type is the type of link clicked: 1 = file, 2 = external website
 //warn indicates if a warning dialog was displayed - true/false

 function callback(obj, type, warn) {
 	console.log('Object: '.obj);
 	console.log('Link Type: '.type);
 	console.log('Warning: '.warn);
 }

```

7). After version 2.3.0, if you choose to use the navigateState option, your callback might look something like this:

```javascript

 //href is the link opened
 //type is the type of link: 1 = file, 2 = external website

 function callback(obj, type, warn) {
 	console.log('Link Href: '.href);
 	console.log('Link Type: '.type);
 }

```


Help & Support
===

This plugin doesn't come with any specific support plan, but I absolutely love helping out where I can. If you encounter any trouble with it at all, please don't hesitate ot let me know. Just head on over to http://fb.me/yupitszac and let me know. Youc an also just open an issue on Github at https://github.com/YupItsZac/jQuery.exLink

If you use jQuery.exLink on your website, let me know! I'd like to see what you did with it and I'll share your link! Post your address to http://fb.me/yupitszac and I'll check it out. 

Also, I'd love to know what additional features you might want in a plugin like this. Let me know! http://fb.me/yupitszac
