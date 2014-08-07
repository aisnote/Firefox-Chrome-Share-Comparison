Firefox-Chrome-Share-Comparison
===============================

Compare WebRTC share features across Firefox and Chrome, both Mozilla and Google are making great progress bringing plugin free HTML5 browsing to everyone.  This document attempts to compare the share portion WebRTC and hopes to keep the information as current as possible.


### Comparison

| Compare        | Firefox           | Chrome | Note |
| ------------- |-------------|-------------|-------------|
| Versions | Nightly Aurora | All |  |
| Method | Drive by web | Packaged App |  |
| Preference needed | Yes, two | No | See note below for pref details |
| HTTPS | Yes, page must use HTTPS | No, packaged app is local |  |
| Screen Share | Yes | Yes |  |
| Screen Selection | No | Yes |  |
| Window Share | Yes  | Yes |  |
| Window Selection | Yes  | Yes |  |
| Tab Share | No  | Yes |  |
| Constraint for screen |  |  |
| Constraint for window |  |  |
| Audio + Video + Share, 1 PeerConnection  | No, Need two  | Yes  | See note below |
| Selection UI |  |  | |
| UI when sharing | Small window at tom of screen  | Strip below browser  | See note |




####  Firefox Preferences for Share

- media.getusermedia.screensharing.enabled                     set this to true
- media.getusermedia.screensharing.allowed_domains    e.g. ‘mozilla.github.io’


####  Peer Connections to signal media

If an application wants to have an audio \ video stream as well as sending share this is possible on Chrome using one PeerConnection JavaScript object but Firefox required two, one for Audio \ Video and anothe rone for share.

