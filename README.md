Firefox-Chrome-Share-Comparison
===============================

Compare WebRTC share features across Firefox and Chrome, both Mozilla and Google are making great progress bringing plugin free HTML5 browsing to everyone. 


### Comparison

| Compare        | Firefox           | Chrome | Note |
| ------------- |-------------|-------------|-------------|
| Version | Nightly Aurora | All |  |
| Method | Drive by | Packaged App |  |
| Preference needed | Yes, two | No | See note below for pref details |
| HTTPS | Yes, page must use HTTPS | No, packaged app is local |  |
| Screen Share | Yes | Yes |  |
| Screen Selection | No | Yes |  |
| Window Share | Yes  | Yes |  |
| Window Selection | Yes  | Yes |  |
| Tab Share | No  | Yes |  |
| Constraints |  |  |
| Audio + Video + Share, 1 PeerConnection  | No, Need two  | Yes  |
|  |  |  |




Firefox Preferences for Share

media.getusermedia.screensharing.enabled                     set this to true
media.getusermedia.screensharing.allowed_domains    e.g. ‘mozilla.github.io’
