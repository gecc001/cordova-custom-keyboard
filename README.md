# cordova-custom-keyboard

> This plugin provides the `Keyboard` object which has some functions to customize and control the keyboard.

This plugin has only been tested in Cordova 3.2 or greater, and its use in previous Cordova versions is not recommended (potential conflict with keyboard customization code present in the core in previous Cordova versions). 

If you do use this plugin in an older Cordova version (again, not recommended), you have to make sure the HideKeyboardFormAccessoryBar and KeyboardShrinksView preference values are *always* false, and only use the API functions to turn things on/off.
# Installation

From github latest (may not be stable)

`cordova plugin add https://github.com/gecc001/cordova-custom-keyboard`


# Supported Platforms
- iOS

It also supports the __HideKeyboardFormAccessoryBar__ (boolean) and __KeyboardShrinksView__ (boolean) preferences in config.xml.


- Android 

## Preferences

### KeyboardResize

> Boolean (true by default)

#### Possible values
- `true`: Showing/hiding the keyboard will trigger some kind of resizing of the app (see KeyboardResizeMode)
- `false`: Web will not be resized when the keyboard shows up.

```xml
<preference name="KeyboardResize" value="true" />
```

### KeyboardResizeMode

> String ('native' by default)

#### Possible values

- `native`: The whole native webview will be resized when the keyboard shows/hides, it will affect the `vh` relative unit.
- `body`: Only the html `<body>` element will be resized. Relative units are not affected, because the viewport does not change.
- `ionic`: Only the html `ion-app` element will be resized. Only for ionic apps.

```xml
<preference name="KeyboardResizeMode" value="native" />
```


#### IOS Quick Example
- [Methods IOS](#methods-ios)
    - [Keyboard.shrinkView](#ios-keyboardshrinkview)
    - [Keyboard.hideFormAccessoryBar](#ios-keyboardhideformaccessorybar)
    - [Keyboard.disableScrollingInShrinkView](#ios-keyboarddisablescrollinginshrinkview)
    - [Keyboard.hide](#ios-keyboardhide)
- [Properties](#ios-properties)
    - [Keyboard.isVisible](#ios-keyboardisvisible)
    - [Keyboard.automaticScrollToTopOnHiding](#ios-keyboardautomaticscrolltotoponhiding)
- [Events](#io-sevents)
    - [keyboardDidShow](#ios-keyboarddidshow)
    - [keyboardDidHide](#ios-keyboarddidhide)
    - [keyboardWillShow](#ios-keyboardwillshow)
    - [keyboardWillHide](#ios-keyboardwillhide)
    - [keyboardHeightWillChange](#ios-keyboardheightwillchange)


#### Android Quick Example
- [Methods Android](#methods-android)
    - [Keyboard.hideFormAccessoryBar](#android-keyboardhideformaccessorybar)
    - [Keyboard.hide](#android-keyboardhide)
    - [Keyboard.show](#android-keyboardshow)
- [Properties](#android-properties)
    - [Keyboard.isVisible](#android-keyboardisvisible)
- [Events](#android-events)
    - [keyboardDidShow](#android-keyboarddidshow)
    - [keyboardDidHide](#android-keyboarddidhide)
    - [keyboardWillShow](#android-keyboardwillshow)
    - [keyboardWillHide](#android-keyboardwillhide)



# Methods IOS

## IOS Keyboard.shrinkView

Shrink the WebView when the keyboard comes up.

    Keyboard.shrinkView(value, successCallback);

#### Description

Set to true to shrink the WebView when the keyboard comes up. The WebView shrinks instead of the viewport shrinking and the page scrollable. This applies to apps that position their elements relative to the bottom of the WebView. This is the default behaviour on Android, and makes a lot of sense when building apps as opposed to webpages.


#### Supported Platforms

- iOS

#### Quick Example

    Keyboard.shrinkView(true);
    Keyboard.shrinkView(false);
    Keyboard.shrinkView(null, function (currentValue) { console.log(currentValue); });

## IOS Keyboard.hideFormAccessoryBar

Hide the keyboard toolbar.

    Keyboard.hideFormAccessoryBar(value, successCallback);

#### Description

Set to true to hide the additional toolbar that is on top of the keyboard. This toolbar features the Prev, Next, and Done buttons.


#### Supported Platforms

- iOS

#### Quick Example

    Keyboard.hideFormAccessoryBar(true);
    Keyboard.hideFormAccessoryBar(false);
    Keyboard.hideFormAccessoryBar(null, function (currentValue) { console.log(currentValue); });

## IOS Keyboard.disableScrollingInShrinkView

Disable scrolling when the the WebView is shrunk.

    Keyboard.disableScrollingInShrinkView(value, successCallback);

#### Description

Set to true to disable scrolling when the WebView is shrunk.


#### Supported Platforms

- iOS

#### Quick Example

    Keyboard.disableScrollingInShrinkView(true);
    Keyboard.disableScrollingInShrinkView(false);
    Keyboard.disableScrollingInShrinkView(null, function (currentValue) { console.log(currentValue); });
 
## IOS Keyboard.hide

Hide the keyboard

    Keyboard.hide();

#### Description

Call this method to hide the keyboard

#### Supported Platforms

- iOS

#### Quick Example

    Keyboard.hide();

# IOS Properties

## Keyboard.isVisible

Determine if the keyboard is visible.

    if (Keyboard.isVisible) {
        // do something
    }

#### Description

Read this property to determine if the keyboard is visible.


#### Supported Platforms

- iOS

## Keyboard.automaticScrollToTopOnHiding

Specifies whenether content of page would be automatically scrolled to the top of the page
when keyboard is hiding.

    Keyboard.automaticScrollToTopOnHiding = true;

#### Description

Set this to true if you need that page scroll to beginning when keyboard is hiding.
This is allows to fix issue with elements declared with position: fixed,
after keyboard is hiding.


#### Supported Platforms

- iOS

# IOS Events

## IOS keyboardDidShow

This event is fired when keyboard fully shown.

    window.addEventListener('keyboardDidShow', function () {
        // Describe your logic which will be run each time keyboard is shown.
    });

#### Description

Attach handler to this event to be able to receive notification when keyboard is shown.


#### Supported Platforms

- iOS

## IOS keyboardDidHide

This event is fired when the keyboard is fully closed.

    window.addEventListener('keyboardDidHide', function () {
        // Describe your logic which will be run each time keyboard is closed.
    });

#### Description

Attach handler to this event to be able to receive notification when keyboard is closed.


#### Supported Platforms

- iOS

## IOS keyboardWillShow

This event fires before keyboard will be shown.

    window.addEventListener('keyboardWillShow', function () {
        // Describe your logic which will be run each time when keyboard is about to be shown.
    });

#### Description

Attach handler to this event to be able to receive notification when keyboard is about to be shown on the screen.


#### Supported Platforms

- iOS

## IOS keyboardWillHide

This event is fired when the keyboard is fully closed.

    window.addEventListener('keyboardWillHide', function () {
        // Describe your logic which will be run each time when keyboard is about to be closed.
    });

#### Description

Attach handler to this event to be able to receive notification when keyboard is about to be closed.


#### Supported Platforms

- iOS

## IOS keyboardHeightWillChange

This event is fired when the keyboard is fully closed.

    window.addEventListener('keyboardHeightWillChange', function (event) {
        // Describe your logic which will be run each time when keyboard is about to be closed.
        console.log(event.keyboardHeight);
    });

#### Description

Attach handler to this event to be able to receive notification when keyboard is about to be closed.


#### Supported Platforms

- iOS




# Methods Android

## Android Keyboard.hideFormAccessoryBar

> Hide the keyboard toolbar.

Set to true to hide the additional toolbar that is on top of the keyboard. This toolbar features the Prev, Next, and Done buttons.

```js
Keyboard.hideFormAccessoryBar(value, successCallback);
```

##### Quick Example

```js
Keyboard.hideFormAccessoryBar(true);
Keyboard.hideFormAccessoryBar(false);
Keyboard.hideFormAccessoryBar(null, (currentValue) => { console.log(currentValue); });
```

### Keyboard.hide

> Hide the keyboard

Call this method to hide the keyboard

```js
Keyboard.hide();
```


### Keyboard.show

> Show the keyboard

Call this method to show the keyboard.

```js
Keyboard.show();
```

## Android Properties

### Android Keyboard.isVisible

> Determine if the keyboard is visible.

Read this property to determine if the keyboard is visible.

```js
if (Keyboard.isVisible) {
    // do something
}
```

## Android Events

### Android keyboardDidHide

> This event is fired when the keyboard is fully closed.

Attach handler to this event to be able to receive notification when keyboard is closed.

```js
window.addEventListener('keyboardDidHide', () => {
    // Describe your logic which will be run each time keyboard is closed.
});
```

### Android keyboardDidShow

> This event is fired when the keyboard is fully open.

Attach handler to this event to be able to receive notification when keyboard is opened.

```js
window.addEventListener('keyboardDidShow', (event) => {
    // Describe your logic which will be run each time when keyboard is about to be shown.
    console.log(event.keyboardHeight);
});
```

### Android keyboardWillShow

> This event fires before keyboard will be shown.

Attach handler to this event to be able to receive notification when keyboard is about to be shown on the screen.

```js
window.addEventListener('keyboardWillShow', (event) => {
    // Describe your logic which will be run each time when keyboard is about to be shown.
    console.log(event.keyboardHeight);
});
```

### Android keyboardWillHide

> This event is fired when the keyboard is fully closed.

Attach handler to this event to be able to receive notification when keyboard is about to be closed.

```js
window.addEventListener('keyboardWillHide', () => {
    // Describe your logic which will be run each time when keyboard is about to be closed.
});
```


