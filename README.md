Firefox-Chrome-Share-Comparison
===============================

Compare WebRTC share features across Firefox and Chrome, both Mozilla and Google are making great progress bringing plugin free HTML5 browsing to everyone.  This document attempts to compare the share portion WebRTC and hopes to keep the information as current as possible.


### Comparison

| Compare        | Firefox           | Chrome | Note |
| ------------- |-------------|-------------|-------------|
| Versions | Nightly & Aurora | All |  |
| Deployment method | Drive by web | Packaged App |  |
| Preference needed | Yes, two | No | See note below for pref details |
| HTTPS | Yes, page must use HTTPS | No, packaged app is local |  |
| Feature: Screen Share | Yes | Yes |  |
| Feature: Screen Selection | No | Yes |  |
| Feature: Window Share | Yes  | Yes |  |
| Feature: Window Selection | Yes  | Yes |  |
| Feature: Tab Share | No  | Yes |  |
| Constraint for screen share | mediaSource: "screen" | chromeMediaSource: 'screen' | |
| Constraint for window share | mediaSource: ”window" | chromeMediaSource: ’desktop' | |
| Audio + Video + Share, Num PeerConnections  | Need two  | One  | See note below |
| Selection UI | Drop down box similar to camera selection | Separate UI popout  | see images below |
| UI when sharing | Small window at tom of screen  | Strip below browser  | See note |




####  Firefox Preferences for Share

- media.getusermedia.screensharing.enabled                     set this to true
- media.getusermedia.screensharing.allowed_domains    e.g. ‘mozilla.github.io’


####  Peer Connections to signal media

If an application wants to have an audio \ video stream as well as share this is possible on Chrome using one PeerConnection JavaScript object but Firefox requires two, one for Audio \ Video and another one for share.


![Firefox Window Share UI](https://github.com/emannion/Firefox-Chrome-Share-Comparison/blob/master/firefox_window_share_ui.png "Firefox Window Share UI")


