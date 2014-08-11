Firefox-Chrome-Share-Comparison
===============================

Compare WebRTC share features across Firefox and Chrome, both Mozilla and Google are making great progress bringing plugin free HTML5 browsing to everyone.  This document attempts to compare the share portion of WebRTC and hopes to keep the information as current as possible.

Chrome can share the desktop using getUserMedia in a HTTPS web page and using the flag (chrome://flags/#enable-usermedia-screen-capture) but Google recommends doing share using an extension or packaged application which enables the app to do much more including screen and application selection.  This doc describes Chrome share as using a packaged application or extension.

### Comparison

| Compare        | Firefox           | Chrome | Note |
| ------------- |-------------|-------------|-------------|
| Versions | Nightly & Aurora | All |  |
| Deployment method | Drive by web | Packaged App, Extension | See Extension note |
| Preference needed | Yes, two | No | See note below for Firefox pref details |
| HTTPS | Yes, page must use HTTPS | No, packaged app or extension is local |  |
| Feature: Screen Share | Yes | Yes |  |
| Feature: Screen Selection | No | Yes |  |
| Feature: Window Share | Yes  | Yes |  |
| Feature: Window Selection | Yes  | Yes |  |
| Feature: Tab Share | No  | Yes |  |
| Constraint for screen share | mediaSource: "screen" | chromeMediaSource: 'screen' | |
| Constraint for window share | mediaSource: ”window" | chromeMediaSource: ’desktop' | |
| Audio + Video + Share, Num PeerConnections  | Need two  | One  | See note below |
| Selection UI | Drop down box similar to camera selection | Separate UI popout  | see images below |
| UI when sharing | Small window at top of screen  | Strip below browser  | See note |


#### Chrome extension selection
It is possible to do share in either an extension or a packages application. It is not possible to do both audio \ video capture and share in an extension but this is possible using a packaged application. In the case of an extension then share could be done in the extension and audio \ video done on the drive by web page which uses the extension.


####  Firefox Preferences for Share

- media.getusermedia.screensharing.enabled            set this to true
- media.getusermedia.screensharing.allowed_domains    e.g. ‘mozilla.github.io’


####  Peer Connections to signal media

If an application wants to have an audio \ video stream as well as share this is possible on Chrome using one PeerConnection JavaScript object but Firefox requires two, one for Audio \ Video and another one for share.


### Firefox Window selection UI
![Firefox Window Share UI](https://github.com/emannion/Firefox-Chrome-Share-Comparison/blob/master/firefox_window_share_ui.png "Firefox Window Share UI")


### Chrome Window and Screen selection UI
![Chrome Window Share UI](https://github.com/emannion/Firefox-Chrome-Share-Comparison/blob/master/chrome_window_share_ui.png "Chrome Window Share UI")

