## Intoduction
Default navigation in a progressive web app environment prodives a web experience. The implementation needs to feel like a native app, that is a more complex navigation tree, rather than the forward and back behavior on the web. Some concepts were introduced early on in the development of mobile operating systems, like Android and iOS that implement lateral navigation, deep linking, and navigation gestures between screens.

## Overview

A good conceptual overview of the implementation of navigation in native environments:  
https://material.io/design/navigation/understanding-navigation.html
https://developer.apple.com/design/human-interface-guidelines/ios/app-architecture/navigation
https://reactnavigation.org/docs/en/custom-navigator-overview.html

## Terms
Refer to: https://reactnavigation.org/docs/en/glossary-of-terms.html

### Component
Refers any of the interface elements, at any level in the view hierarchy of the UI. 

### Page
The term "page" usually occurs within a web context, because it's scrolling verically by default. It is surrounded by browser interface elements that interface with the pages, on the user's screen.  

### Screen
A "screen" is directly referring to the user's entire screen space, meaning that there is no UI surrounding it within the bounds of the hardware. All components within a screen do not react to touch or gestures by default, and those child components have to explicitly declare their behavior, including scolling behavior.  
Native apps use the operating system's built in functionality to deliver a familiar user experience, such as:
- pull to refresh
- persisted screen state (scroll position, ui controls, etc.)
- navigation gestures
- animation of the header component and transitions between screens
  
_Screen header:_ Also known as navigation header, navigation bar, navbar, and probably many other things. This is the rectangle at the top of the screen that contains the back button and the title for the screen.   
* **iOS** — _Navigation bar_  
https://developer.apple.com/design/human-interface-guidelines/ios/bars/navigation-bars
* **Android** — _Top app bar_  
https://material.io/components/app-bars-top


### App environment
The environment determines the navigation capabilities.
- **iOS** — swipe gesture
- **Android** — back button
- **Web** — browser implementation
    - iOS Safari: swipe gesture, back button in the bottom toolbar
    https://developer.apple.com/design/human-interface-guidelines/ios/bars/toolbars/
    - iOS Chrome: back button and back swipe arrow animation
    - Android Chrome: back button

**App Container**
https://reactnavigation.org/docs/en/app-containers.html
App Containers are responsible for:
- managing app state and linking the top-level navigator to the app environment
- persist navigation state
- provides a common interface over the different navigation API of a given app environment

**Navigator**


Destination  
Action  

## Graph


## Repositories
Possible solutions to the navigation framework for all of our frontends running on the web.

http://maisano.github.io/react-router-transition/animated-switch/demo

https://github.com/jcoreio/react-router-transition-switch