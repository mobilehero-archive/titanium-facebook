<a href="https://brenton.house/saying-goodbye-to-axway-amplify-titanium-31a44f3671de">
	<h1 align="center">
	🪦 RIP Axway Amplify Titanium (2010 - 2022)
	</h1>
</a>
<a href="https://brenton.house/saying-goodbye-to-axway-amplify-titanium-31a44f3671de">
	<p align="center">
		<img src="https://cdn.secure-api.org/images/RIP-Axway-Amplify-Titanium.png" alt="RIP Axway Amplify Titanium (2010 - 2022)" width="80%" />
	</p>
</a>
<a href="https://brenton.house/saying-goodbye-to-axway-amplify-titanium-31a44f3671de">
	<p align="center">
		🪦 &nbsp; RIP Axway Amplify Titanium (2010 - 2022)
	</p>
</a>
<p>&nbsp;</p>
<a href="https://brenton.house/saying-goodbye-to-axway-amplify-titanium-31a44f3671de">
	<h2 align="center">
		🛑 This project is no longer being maintained 🛑
	</h2>
</a>
<p>&nbsp;</p>
<hr>
<p>&nbsp;</p>
<p>&nbsp;</p>



# @titanium/facebook

[![@titanium/facebook](https://img.shields.io/npm/v/@titanium/facebook.png)](https://www.npmjs.com/package/@titanium/facebook)
[![Dependabot Status](https://api.dependabot.com/badges/status?host=github&repo=brentonhouse/titanium-facebook)](https://dependabot.com)


> Native modules that allows you to use Facebook SDK with Axway Titanium native mobile apps.

* [📝 Description](#-description)
* [🚀 Getting Started](#-getting-started)
	* [Install `@titanium/facebook` in root of project](#install-titaniumfacebook-in-root-of-project)
* [✨Features](#features)
* [Getting Started](#getting-started)
	* [iOS 10 Compatibility](#ios-10-compatibility)
	* [Android Key Hash for Facebook Developer Profile](#android-key-hash-for-facebook-developer-profile)
	* [Proxy required per Android activity](#proxy-required-per-android-activity)
	* [Facebook Login and Authorization](#facebook-login-and-authorization)
	* [Requesting read and publish permissions](#requesting-read-and-publish-permissions)
	* [Refreshing Permissions](#refreshing-permissions)
	* [Facebook Graph API](#facebook-graph-api)
	* [Share Dialog](#share-dialog)
	* [Invite Dialog](#invite-dialog)
	* [Messenger Dialogs (iOS)](#messenger-dialogs-ios)
		* [Share links:](#share-links)
		* [Share media:](#share-media)
	* [Send Requests Dialog](#send-requests-dialog)
	* [Messenger Button](#messenger-button)
	* [Deferred App links](#deferred-app-links)
	* [Log App Events](#log-app-events)
	* [Log Purchases](#log-purchases)
	* [Notes](#notes)
	* [Events and error handling](#events-and-error-handling)
	* [Credits](#credits)
* [📚Learn More](#learn-more)
* [📣 Feedback](#-feedback)
* [©️ Legal](#️-legal)


## 📝 Description

> This is a repackaging of the compiled iOS and Android modules for [Titanium Facebook](https://github.com/appcelerator-modules/ti.facebook) to allow for installation via npm.


## 🚀 Getting Started


### Install `@titanium/facebook` in root of project


```bash
npm install @titanium/facebook
```


## ✨Features

* [x] Includes Titanium native iOS module: `facebook 7.0.0`
* [x] Includes Titanium native Android module: `facebook 8.0.0`
* [x] Logging in to Facebook and authorizing your application
* [x] Requesting read and publish permissions
* [x] Refreshing existing permission
* [x] Making requests through the Facebook Graph API using the requestWithGraphPath method
* [x] Posting web and native share dialogs
* [x] Posting send request dialogs



## Getting Started

```
You will need a Facebook App ID ready. To create a Facebook App ID, go to the Facebook Developer App: developers.facebook.com/apps

On the iOS platform, add the following property to the \<ios\>\<plist\>\<dict\> section in tiapp.xml:
```xml
<key>FacebookAppID</key>
<string>1234567890123456</string>
<key>FacebookDisplayName</key>
<string>SomeName</string>
```
where SomeName is exactly as appears in the Facebook developer settings page

Also make sure you have a URL Scheme in tiapp.xml that looks like fb1234567890123456. See Facebook docs for details on this. Add an entry to \<ios\>\<plist\>\<dict\> that looks like this, modify it for your app:
```xml
<key>CFBundleURLTypes</key>
<array>
    <dict>
        <key>CFBundleURLName</key>
        <string>com.appcelerator.kitchensink</string>
        <key>CFBundleURLSchemes</key>
        <array>
            <string>kitchensink</string>
            <string>fb1234567890123456</string>
        </array>
    </dict>
</array>
```

To define a url scheme suffix for multiple apps sharing the same facebook app ID, simply add the suffix (in lower case and must start with a letter) to the relevant string under the CFBundleURLSchemes key. In this example, it will look like fb1234567890123456foo if you are adding the suffix foo. This will also require additional configurations in the facebook dashboard, see https://developers.facebook.com/docs/ios/troubleshooting#sharedappid for details.

To enable the use of Facebook dialogs (e.g., Login, Share), you also need to include the following key and values in tiapp.xml to handle the switching in and out of your app:
```xml
<key>LSApplicationQueriesSchemes</key>
    <array>
        <string>fbapi</string>
        <string>fb-messenger-api</string>
        <string>fbauth2</string>
        <string>fbshareextension</string>
    </array>
```

For iOS 9+ and Titanium 5.0.0.GA and above, App Transport Security is disabled by default so you don't need these keys.
If you choose to enable it, you have to set the following keys and values in tiapp.xml:
```xml
<key>NSAppTransportSecurity</key>
    <dict>
        <key>NSExceptionDomains</key>
            <dict>
                <key>facebook.com</key>
                    <dict>
                        <key>NSIncludesSubdomains</key> 
                        <true/>        
                        <key>NSExceptionRequiresForwardSecrecy</key> 
                        <false/>
                    </dict>
                <key>fbcdn.net</key>
                    <dict>
                        <key>NSIncludesSubdomains</key> 
                        <true/>
                        <key>NSExceptionRequiresForwardSecrecy</key>  
                        <false/>
                    </dict>
                <key>akamaihd.net</key>
                    <dict>
                        <key>NSIncludesSubdomains</key> 
                        <true/>
                        <key>NSExceptionRequiresForwardSecrecy</key> 
                        <false/>
                    </dict>
            </dict>
    </dict>
```

### iOS 10 Compatibility

**Note**: The paragraph about custom capabilities was only necessary between Titanium SDK 5.5.0 and 6.0.0. Since 6.0.1.GA, we add the 
required capabilities automatically, so you don't need to curate your own entitlements file anymore, which will avoid possible issues 
with concurring values. Please ensure to use both SDK and CLI 6.0.1 (or later).

On the android platform, in tiapp.xml or AndroidManifest.xml you must declare the following inside the `<application/>` node 
```xml
<activity android:name="com.facebook.FacebookActivity" android:theme="@android:style/Theme.Translucent.NoTitleBar" android:label="YourAppName" android:configChanges="keyboard|keyboardHidden|screenLayout|screenSize|orientation" />
```
You must also reference the string containing your Facebook app ID, inside the `<application/>` node as well: 
```xml
<meta-data android:name="com.facebook.sdk.ApplicationId" android:value="@string/app_id"/>
```
The app id goes into the the file `/platform/android/res/values/strings.xml` (classic) or ``app/platform/android/res/values/strings.xml``, where you should define:
```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <!-- ... -->
    <string name="app_id">1234567890123456</string>
    <!-- ... -->
</resources>
```
where the number is of course the app ID. The app ID is not set programmatically.

Finally, if using sharing capabilities, you should add the content provider settings as well:
```xml
<provider android:name="com.facebook.FacebookContentProvider"
          android:authorities="com.facebook.app.FacebookContentProvider<YOUR_APP_ID>"
          android:exported="true" />
```

### Android Key Hash for Facebook Developer Profile

Facebook requires you to add the Key Hash of the Android app in order for you to use the module. Steps to get the Key Hash as follows. Alternatively, if you do not have the correct Key Hash on the Android App, the App will give an error message when you login with the Key Hash of the App which you can then copy.

Use the following command to generate and receive the key-hashpath of your app. 
To do do, replace `<sdk-version>` with your SDK-version and run:
```
keytool -exportcert -alias tidev -storepass tirocks -keystore ~/Library/Application\ Support/Titanium/mobilesdk/osx/<sdk-version>/android/dev_keystore | openssl sha1 -binary | openssl base64
```

If you use your own keystore, update the alias, password and name of your keystore file of course.

You would also require, to fill up the `Google Play Package Name` which is the Application ID and the `Class Name` which is the Application ID followed by the Application Name concatenated with the word `Activity`. Example, an App called `Kitchensink` with Application ID of `com.appcelerator.kitchensink` will have the Class Name as `com.appcelerator.kitchensink.KitchensinkActivity`. Alternatively, you can check the Class Name in `/build/android/AndroidManifest.xml` which is generated when you build the project. The launcher activity is the Class Name of the Application.

For more info, please see https://developers.facebook.com/docs/android/getting-started

### Proxy required per Android activity


Unlike iOS, where the entire app is active in memory, in Android only a single Activity is active at any time. In Titanium, an Activity corresponds to a standalone (i.e. not a Tab window) `Ti.UI.Window` or `Ti.UI.TabGroup`. The Facebook SDK contains tools to synchronize state between the various activities in the app, and this module implements that functionality, but for this to work we need to tell the module which is the currently active Activity. Thus the following is required:

All Windows/TabGroup in your app must create a proxy, e.g. : 
```js
myWindow.fbProxy = fb.createActivityWorker({
    lifecycleContainer: myWindow
});
```
where fb is the required module.
We must pass to the proxy the Ti.UI.Window or Ti.UI.TabGroup that will be using the proxy, so that the proxy can attach itself to the window's or tabgroup's activity.
The proxy object must be created prior to calling open() on the window or tabgroup in order to make sure the Activity onCreate event is captured correctly.
This proxy has no APIs (new since version 3.20.05), its sole function is to signal the Facebook SDK for the various Activity transitions. So just create it and attach it to the window/tabgroup.

### Facebook Login and Authorization


To use Facebook, a user must log in to Facebook and explicitly authorize the application to perform certain actions, such as accessing profile information or posting status messages.

Before calling `authorize()` it is possible to set the behavior that facebook will try to use when logging users in.
The following behaviors are available:
 * LOGIN_BEHAVIOR_BROWSER
 * LOGIN_BEHAVIOR_NATIVE
 * LOGIN_BEHAVIOR_SYSTEM_ACCOUNT (iOS only)
 * LOGIN_BEHAVIOR_WEB (iOS only)
 * LOGIN_BEHAVIOR_NATIVE_WITH_FALLBACK (Android only - NATIVE will attempt to fallback on iOS)
 * LOGIN_BEHAVIOR_DEVICE_AUTH (Android only)
 
These constants correspond to the ones exposed the by the Facebook SDK on each platform - for more information, see the Facebook documentation.

```js
    var fb = require('@titanium/facebook');
    fb.initialize();
    fb.setLoginBehavior(fb.LOGIN_BEHAVIOR_NATIVE);
    fb.permissions = ['email'];
    fb.authorize();
```

There are two ways to initiate the login process:

Create a Facebook LoginButton to allow the user to log in if desired. You can also add either readPermissions or publishPermissions, otherwise the default is request for `public_profile`. Doing so will let the LoginButton request for permissions when logging in. Note that Facebook does not support setting both parameters at the same time to the LoginButton. For a complete list of permissions, see the official Facebook Permissions Reference.

```javascript
    var fb = require('@titanium/facebook');
    fb.initialize();
    var loginButton = fb.createLoginButton({
        readPermissions: ['read_stream','email']
    });
```

Call authorize to prompt the user to login and authorize the application. This method can be considered if you prefer to use custom UI instead of the loginButton.

```javascript
    var fb = require('@titanium/facebook');
    fb.initialize(); 
    fb.permissions = ['email'];
    facebook.authorize();
```
Which approach you take depends on your UI and how central Facebook is to your application. Both approaches fire a `login` event.

### Requesting read and publish permissions


For a complete list of permissions, see the official Facebook Permissions Reference.

`requestNewReadPermissions`

```javascript
var fb = require('@titanium/facebook');
fb.requestNewReadPermissions(['read_stream','user_hometown', etc...], function(e){
    if(e.success) {
        fb.requestWithGraphPath(...);
    } else if (e.cancelled) {
        ....
    } else {
        Ti.API.debug('Failed authorization due to: ' + e.error);
    }
});
```

`requestNewPublishPermissions`

You must use the audience constants from the module, either AUDIENCE_NONE, AUDIENCE_ONLY_ME, AUDIENCE_FRIENDS, or AUDIENCE_EVERYONE. Note that it is not an error for the user to 'Skip' your requested permissions, so you should check the module's permissions property following the call.

```javascript
var fb = require('@titanium/facebook');
fb.requestNewPublishPermissions(['read_stream','user_hometown', etc...], fb.AUDIENCE_FRIENDS, function(e) {
    if (e.success) {
        fb.requestWithGraphPath(...);
    } else if (e.cancelled) {
    ....
    } else {
        Ti.API.debug('Failed authorization due to: ' + e.error);
    }
});
```

### Refreshing Permissions


Facebook now grants total control over granted permissions, and if the user modified the permissions outside of your app your cached token may not be updated. To get the current permissions from Facebook's servers you can call fb.refreshPermissionsFromServer(). You may listen for the tokenUpdated event to be notified of this operation's successful completion.

### Facebook Graph API


The Facebook Graph API is the preferred method for getting information about a user's friends, news feed, and so on. Each object in the Facebook social graph is represented by a graph API object, such as a user, photo, or status message. The Graph API allows you to make requests on behalf of the user, such as posting a picture or status message. Use the requestWithGraphPath method to make a request to the Graph API.

For details on each of the Graph API objects and the supported operations, see the official Facebook Graph API documentation.
Note: fql is no longer supported by Facebook beginning April 2015, so this module does not support fql. This module supports Facebook Graph API v2.2 and above.

Example 1:

```javascript
    var fb = require('@titanium/facebook');
    fb.requestWithGraphPath('me/groups', {}, 'GET',  function(e) {
        if (!e.success) {
            if (e.error) {
                alert(e.error);
            } else {
                alert("call was unsuccessful");
            }
            return;
        }
        var result = JSON.parse(e.result).data;
    }
```
Example 2:

```javascript
    var fb = require('@titanium/facebook');
    fb.requestWithGraphPath('me/picture', {'redirect': 'false'}, 'GET',  function(e) {
        if (!e.success) {
            if (e.error) {
                alert(e.error);
            } else {
                alert("call was unsuccessful");
            }
            return;
        }
        var result = JSON.parse(e.result)
    }
```

### Share Dialog


You don't need permissions. You can either use presentShareDialog which requires facebook app to be preinstalled, or presentWebStareDialog that uses the web browser instead. Both approaches fire a `shareCompleted` event.
To share a user's status just call fb.share({});
To share a link call fb.share({url: 'http://example.com' });
To share more information, example:

```javascript
    var fb = require('@titanium/facebook');
    fb.presentShareDialog({
        link: 'https://appcelerator.com/',
        title: 'great product',
        description: 'Titanium is a great product',
        picture: 'http://www.appcelerator.com/wp-content/uploads/scale_triangle1.png'
    });
```

### Invite Dialog


Opens a supported Facebook Invite dialog from the Facebook App. To monitor if the share request succeeded 
or not, listen to the `shareCompleted` event. Example:

```javascript
    var fb = require('@titanium/facebook');
    fb.presentInviteDialog({
        appLink: "https://fb.me/xxxxxxxx",
        appPreviewImageLink: "https://www.mydomain.com/my_invite_image.jpg"
    });
```

### Messenger Dialogs (iOS)


You can share content (including links and places) using the `presentMessengerDialog` method and 
share media including images, GIF's and videos using the `shareMediaToMessenger` method. 

#### Share links:

```javascript
    var fb = require('@titanium/facebook');
    fb.presentMessengerDialog({
        title: "Appcelerator Titanium rocks!", // The title of the link
        description: "Shared from my Titanium application", // The description of the link
        link: "https://appcelerator.com", // The link you want to share
        referal: "ti_app", // The referal to be added as a suffix to your link
        placeID: "my_id", // The ID for a place to tag with this content
        to: [] // List of IDs for taggable people to tag with this content
    });
```

#### Share media:

```javascript
    var fb = require('@titanium/facebook');
    var btn = Ti.UI.createButton({
        title: "Share media to messenger"
    });
    btn.addEventListener("click", function(e) {
        var media = [
            Ti.UI.createView({height: 30,width:30,backgroundColor: "#ff0"}).toImage(), // Image blob
            Ti.Filesystem.getFile(Ti.Filesystem.resourcesDirectory, "test.gif").read(), // GIF Blob
            Ti.Filesystem.getFile(Ti.Filesystem.resourcesDirectory, "movie.mp4").read() // Video Blob
        ];

        var options = Ti.UI.createOptionDialog({
            options: ["Photo", "GIF", "Video", "Cancel"],
            cancel: 3
        });
        options.addEventListener("click", function(e) {
            if (e.index == 3) {
                return;
            }
            fb.shareMediaToMessenger({
                media: media[e.index],
                metadata: "Ti rocks!",
                link: "https://appcelerator.com", 
                renderAsSticker: true // Only for photos e.g. selfies
            });
        });
        options.show();
    });
```

### Send Requests Dialog


Sends an application request. Fires a `sendRequestCompleted` event. You can optionally include a `title` key with the title string, or customized parameters in the `data` dictionary. To preselect users to send the invite to, you can optionally add a `to` key with a string of values containing the facebook ids, seperated by commas. See below for example.
See official Facebook Dialogs documentation for more details.

```javascript
    var fb = require('@titanium/facebook');
    fb.presentSendRequestDialog({
        message: 'Go to https://appcelerator.com/',
        title: 'Invitation to Appcelerator',
        recipients: ['123456789', '123456788'],
        data: {
            badge_of_awesomeness: '1',
            social_karma: '5'
        }
    });
```

### Messenger Button


The Messenger button provides a quick mechanism for users to share content to the Facebook Messenger. 
A click on the button can share the content to multiple users.

To create a Messenger button, call the `createMessengerButton` method. Example: 

```javascript
    var fb = require('@titanium/facebook');
    var messengerButton = fb.createMessengerButton({
        mode: fb.MESSENGER_BUTTON_MODE_RECTANGULAR
        style: fb.MESSENGER_BUTTON_STYLE_BLUE
    });
    win.add(messengerButton);
```

### Deferred App links


Deferred deep linking allows you to send people to a custom view after they installed your app via the app store.

You can simply call fetchDeferredAppLink on startup to open eventually incoming app links.

```javascript
var fb = require('@titanium/facebook');
fb.fetchDeferredAppLink(function(e) {
    if (e.success) {
        // Dispatch internal routes
    }
});
```

### Log App Events

```js
fb.logCustomEvent('handsClapped'); // Pass a string for the event name, view the events on Facebook Insights
```

### Log Purchases

```js
fb.logPurchase(13.37, 'USD'); // Pass a number of the amound and a string for the currency.
```

### Notes

* The FBSDKCoreKit.framework, FBSDKLoginKit.framework, FBSDKShareKit.framework directory is the prebuilt Facebook SDK directly downloaded from Facebook, zero modifications. 
* Facebook is moving away from the native iOS login, and towards login through the Facebook app. The default behavior of this module is the same as in the Facebook SDK: app login with a fallback to webview. The advantages of the app login are: User control over individual permissions, and a uniform login experience over iOS, Android, and web.
* AppEvents are automatically logged. Check out the app Insights on Facebook. We can also log custom events for Insights.
* Choose to use the LoginButton, rather than a customized UI, since it's directly from Facebook and it's easier in maintaining Facebook sessions.

### Events and error handling


The error handling adheres to the new Facebook guideline for events such as `login`, `shareCompleted` and `requestSendCompleted`. Here is how to handle `login` events:
```javascript
    var fb = require('@titanium/facebook');
    fb.addEventListener('login', function(e) {
        // You *will* get this event if loggedIn == false below
        // Make sure to handle all possible cases of this event
        if (e.success) {
            alert('login from uid: '+e.uid+', name: '+JSON.parse(e.data).name);
            label.text = 'Logged In = ' + fb.loggedIn;
        } else if (e.cancelled) {
            // user cancelled 
            alert('cancelled');
        } else {
            alert(e.error);         
        }
    });
    fb.addEventListener('logout', function(e) {
        alert('logged out');
        label.text = 'Logged In = ' + fb.loggedIn;
    });
```

### Credits

Big shout-out to [@mokesmokes](https://github.com/mokesmokes) for the initial version of this module, great work! :rocket:



## 📚Learn More

- [Ti.Animation GitHub Repo](https://github.com/m1ga/ti.animation) - Repo for Ti.Animations modules
- [LottieFiles](http://www.lottiefiles.com/) - Free Lottie animations


## 📣 Feedback

Have an idea or a comment?  [Join in the conversation here](https://github.com/brentonhouse/titanium-lottie/issues)! 

## ©️ Legal

Modules are licensed under Apache 2.0 from https://github.com/appcelerator-modules/titanium-lottie

Alloy is developed by Appcelerator and the community and is Copyright © 2012-Present by Appcelerator, Inc. All Rights Reserved.

Alloy is made available under the Apache Public License, version 2. See their license file for more information.

Appcelerator is a registered trademark of Appcelerator, Inc. Titanium is a registered trademark of Appcelerator, Inc. Please see the LEGAL information about using trademarks, privacy policy, terms of usage and other legal information at http://www.appcelerator.com/legal.