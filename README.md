Firefox-Chrome-Share-Comparison
===============================

Compare WebRTC share features across Firefox and Chrome, both Mozilla and Google are making great progress bringing plugin free HTML5 browsing to everyone.  This document attempts to compare the share portion of WebRTC and hopes to keep the information as current as possible.

Chrome can share the desktop using getUserMedia in a HTTPS web page when the startup parameter --enable-usermedia-screen-capturing is used. Google recommends doing share using a Chrome App, formally known as Chrome packaged application which will enable the app to do much more including screen and application selection.  This doc describes Chrome share as using a Chrome App and Firefox as a normal Web Application.

It is possible to use a Firefox extension for screen share which gives a number of advantages over a web application including not requiring the use of two about:flags options described below in the section: "Firefox Preferences for Share".

Some of the information on this table may be incorrect as more features get developed.

### WebRTC share Comparison

| Compare        | Firefox           | Chrome | Note |
| ------------- |-------------|-------------|-------------|
| Versions | All (Release, Beta, Central, Aurora) | All (Release, Beta, Canary, Dev) |  |
| Deployment method | Drive by web | Chrome App, Extension | See Extension note |
| Preference needed | Yes, two | No | See note below for Firefox pref details |
| HTTPS | Yes, page must use HTTPS | No, Chrome App or extension is local |  |
| Feature: Screen Share | Yes | Yes |  |
| Feature: Screen Selection (Multiple VDUs attached) | No | Yes |  |
| Feature: Window Share | Yes  | Yes |  |
| Feature: Window Selection | Yes  | Yes |  |
| Feature: Tab Capture \ Share | No  | Yes, using chrome.tabCapture | Allowed in extensions and legacy packaged apps not chrome apps |
| Constraint for screen share | mediaSource: "screen" | chooseDesktopMedia: 'screen' | |
| Constraint for window share | mediaSource: ”window" | chooseDesktopMedia: ’window' | |
| Constraint for tab share |  | chooseDesktopMedia: ’tab' | Not implemented yet |
| User consent required | Yes, similar to Audio and Video  | Yes, alert message, yes or no |  |
| Audio + Video + Share, Num PeerConnections  | Need two  | One  | See note below |
| Selection UI | Drop down box similar to camera selection | Separate UI popout  | see images below |
| UI when sharing | Small window at top of screen  | Strip below browser  | See note |


#### Chrome extension selection
It is possible to do share in either an extension or a packages application. It is not possible to do both audio \ video capture and share in an extension but this is possible using a packaged application. In the case of an extension then share could be done in the extension and audio \ video done on the drive by web page which uses the extension.


####  Firefox Preferences for Share

- media.getusermedia.screensharing.enabled                       set this to true
- media.getusermedia.screensharing.allowed_domains (whitelist)   e.g. ‘mozilla.github.io’


####  Peer Connections to signal media

If an application wants to have an audio \ video stream as well as share this is possible in Chrome using one PeerConnection JavaScript object but Firefox requires two, one for Audio \ Video and another one for share.  To make Chrome and Firefox talk together for both share and Audio \ Video streams two peerconnectons should be used on both sides.


### Firefox Window selection UI
![Firefox Window Share UI](https://github.com/emannion/Firefox-Chrome-Share-Comparison/blob/master/firefox_window_share_ui.png "Firefox Window Share UI")


### Chrome Window and Screen selection UI
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
