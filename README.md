Firefox-Chrome-Share-Comparison
===============================

Comparison of WebRTC share features across Firefox and Chrome. Both Mozilla and Google are making great progress bringing plugin free HTML5 browsing to everyone.  This document attempts to compare the share portion of WebRTC and hopes to keep the information as current as possible.

Chrome can share the desktop using getUserMedia in a HTTPS web page when the startup parameter --enable-usermedia-screen-capturing is used. Google recommends doing share using a Chrome App, formally known as Chrome packaged application which will enable the app to do much more including screen and application selection.  This doc describes Chrome share as using a Chrome App and Firefox as a normal Web Application.

For Firefox it is possible to use both a HTTPS web page and a Firefox extension for screen share. Using the extension means you don't require the use of two about:flags options described below in the section: "Firefox Preferences for Share".

Some of the information on this table may be incorrect as more features get developed.

### WebRTC share Comparison

| Compare        | Firefox           | Chrome | Note |
| ------------- |-------------|-------------|-------------|
| Versions | All (Release, Beta, Central, Aurora) | All (Release, Beta, Canary, Dev) |  |
| Deployment method | Drive by web, Extension | Chrome App, Extension | See Extension note |
| Preference needed | Two for web app, none for extension | No | See note below for Firefox pref details |
| HTTPS | Yes, page must use HTTPS | Not required but can use HTTPS |  |
| Feature: Screen Share | Yes | Yes |  |
| Feature: Screen Selection (Multiple VDUs attached) | Yes | Yes |  |
| Feature: Window Share | Yes  | Yes |  |
| Feature: Window Selection | Yes  | Yes |  |
| Feature: Tab Capture \ Share | No  | Yes, using chrome.tabCapture or chrome.chooseDesktopMedia | Allowed in extensions and legacy packaged apps not chrome apps |
| Constraint for screen share | mediaSource: 'screen' | chooseDesktopMedia: 'screen' | |
| Constraint for window share | mediaSource: 'window' | chooseDesktopMedia: 'window' | |
| Constraint for application share | mediaSource: 'application' | Not Supported | |
| Constraint for tab share | Not Implemented  | chooseDesktopMedia: 'tab' | Behind flag since Chrome 50 |
| User consent required | Yes, similar to Audio and Video  | Yes, alert message, yes or no |  |
| Audio + Video + Share, Num PeerConnections  | Need two when talking to Chrome  | One or two when talking to Firefox  | See note below |
| Selection UI | Drop down box similar to camera selection | Separate UI popout  | see images below |
| UI when sharing | Small window at top of screen  | Strip below browser  | See note |


#### Chrome extension selection
It is possible to do share in either an extension or a packages application. It is not possible to do both audio \ video capture and share in an extension but this is possible using a packaged application. In the case of an extension then share could be done in the extension and audio \ video done on the drive by web page which uses the extension.


####  Firefox Preferences for Share

- media.getusermedia.screensharing.enabled                       set this to true
- media.getusermedia.screensharing.allowed_domains (whitelist)   e.g. ‘mozilla.github.io, 10.53.67.77’


####  Peer Connections to signal media

If an application wants to have an Audio \ Video stream as well as Share and work across Firefox and Chrome there are some difficulties. There are differences in the session descriptions which make them incompatable.  This is not the case when only Audio and Video is used or when only Share is used, one PeerConnection will suffice.  There are two possible solutions until Chrome finishes the implementation of Unified Plan.  1).  Can use two PeerConnections accross both browsers, one for audio and video and one for share.  2). There is a polyfill called sdp-interop which can be used to make the session descriptions common across both browsers and prevent usage of two Peer Connections. 


### Firefox Window selection UI
![Firefox Window Share UI](https://github.com/emannion/Firefox-Chrome-Share-Comparison/blob/master/firefox_window_share_ui.png "Firefox Window Share UI")


### Chrome Window, Screen and Tab selection UI
![Chrome Window Share UI](https://github.com/emannion/Firefox-Chrome-Share-Comparison/blob/master/chrome_window_share_ui.png "Chrome Window Share UI")

#### Chrome Inline Installation

To make using a Chrome extension easier in a Web Site it is possible to add a link to a page header and install using one click.

```javascript
<link rel="chrome-webstore-item" 
   href="https://chrome.google.com/webstore/detail/..."
/>
```

Then add something like this to the JavaScript.
```javascript
chrome.webstore.install(
    'https://chrome.google.com/webstore/detail/...',
    function (arg) {
        // needs a reload
        window.location.reload();
    },
    function (err) {
        // handle error
    }
);
```
