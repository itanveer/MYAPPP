# Phonegap--Generic-Boilerplate #
A generic boilerplate for constructing PhonegapApps

*The blog post on this code is [here](http://codesnippets.altervista.org/blog/2015/BLOG.2015-06-10.jssnippets.html).*

There are two (2) big differences to note between HTML5 and previous versions of HTML, and one (1) important point about Phonegap.

The first is the new opening element for [*html5*](http://www.w3schools.com/tags/tag_doctype.asp) is:

```
	<!DOCTYPE html>
```

The second important element sets the device parameters. It tells the mobile device I know how to detect the device screen size (and I don't assume the screen has a width of 1024px). Mozilla has a [bit to say](https://developer.mozilla.org/en-US/docs/Mozilla/Mobile/Viewport_meta_tag), but you'll also want to read [this technical essay](http://www.quirksmode.org/blog/archives/2010/04/a_pixel_is_not.html) from PPK. That element is:

```
	<meta name="viewport" content="width=device-width">
```

The third is the listener. Many beginners trip on this part. It is important for this listener to be added. It allows the phonegap library to prepare all the devices on the phone before you call any of the libraries. Details are available in the [phonegap documentation](http://docs.phonegap.com/en/4.0.0/cordova_events_events.md.html#deviceready)

```
	// Wait for PhoneGap to load
	document.addEventListener("deviceready", onDeviceReady, false);
	//
	function onDeviceReady() {
```

If however, you are not going to use the hardware on the mobile device, you should at least have an [onload=loaded()](http://www.w3schools.com/jsref/event_onload.asp); such as,

```
	<body onload=loaded()>
```

## Android and iOS Extension ##
2015-06-18

Somehow I missed this in the first release. 

**Android Extension**
To extend the base properties of the App you need to add those properties in the AndroidManifest.xml. In this case, because it is Phonegap, extend the property in the header and add those extended properties in the body of the XML. For more details, SEE: [Config File Elements](http://docs.build.phonegap.com/en_US/configuring_config_file_element.md.html#Config%20File%20Elements)
and this [Official Blog Post](http://phonegap.com/blog/2014/01/30/customizing-your-android-manifest-and-ios-property-list-on-phonegap-build/
)

*Added to header of XML*
```
        xmlns:android   = "http://schemas.android.com/apk/res/android"
```

*Added to body of XML*
```
        <gap:config-file platform="android" parent="/manifest/application" >
            <!-- Add Android extensions here. SEE: ... -->
        </gap:config-file>
```

**iOS Extension**
In iOS you need to add those property extensions to the Info.plist. However, unlike the Android version, those properties only need to be added to the body. See the phongap documentation for examples.

