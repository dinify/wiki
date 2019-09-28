## Intro
This page describes the aspects of delivering a native experience in a web environment. Progressive Web App manifest and offline worker cache is just the tip of the iceberg.
Overall desired result is to make our react frontends a feel more native on the platform they are running on.

## Terms
Progressive Web App (PWA)  
REPL pattern  

## Tools
**Lighthouse**: PWA benchmarking tool  
Run in browser — https://web.dev/measure  
Chrome plugin — https://developers.google.com/web/tools/lighthouse/

## Overview
Most of the things listed below are not implemented natively in the browser. By piecing together existing open source Javascript implementations, and apply them to the DOM and browser APIs, it's possible to achieve a native experience.

### Bottom navigation component
iOS Safari: https://www.eventbrite.com/engineering/mobile-safari-why/
Persistent lateral navigation state  
Transitions and animations (see google drive iOS app)  

### Checklist
Overflow scroll image effect  
Webassembly realtime QR scanner  
Screen transitions, with and without shared elements  
GPU accelerated circular reveal transition  
Gestures (drag, pinch to zoom, swipe to navigate)  
Platform specific UI an UX  
Service workers and efficient caching strategy  
Test and develop android pie 9.0 and iOS 13 PWA features  
Responsive typography  
Responsive images with app engine image serving CDN  
More efficient i18n and l10n with CLDR data  
Quadratic gradient scrims  
Keyboard avoiding view  
Recycler view  

### Cross platform native components
Bottom navigation / tab bar  
Leave-behinds (Swipe Actions) in lists  
Bottom sheet / action sheet  
Modals, alert dialogs  
Persistent bottom sheet / Touch   

## Existing solutions
https://github.com/necolas/react-native-web  
https://github.com/vincentriemer/react-native-dom  
Demo — https://rndom-movie-demo.now.sh/  

Dialog / modal:  
https://github.com/reactjs/react-modal  
https://github.com/Dekoruma/react-native-web-modal  
https://github.com/react-native-community/react-native-modal  
https://www.npmjs.com/package/@rmwc/dialog  
https://www.npmjs.com/package/@material/dialog  

## Sources
>Article comparing Android and iOS Native components  
>https://medium.com/@chunchuanlin/android-vs-ios-compare-20-ui-components-patterns-part-1-ad33c2418b45