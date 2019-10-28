# EachNavigationBar

[![CI Status](http://img.shields.io/travis/Pircate/EachNavigationBar.svg?style=flat)](https://travis-ci.org/Pircate/EachNavigationBar)
[![Version](https://img.shields.io/cocoapods/v/EachNavigationBar.svg?style=flat)](http://cocoapods.org/pods/EachNavigationBar)
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![License](https://img.shields.io/cocoapods/l/EachNavigationBar.svg?style=flat)](http://cocoapods.org/pods/EachNavigationBar)
[![Platform](https://img.shields.io/cocoapods/p/EachNavigationBar.svg?style=flat)](https://cocoapods.org/pods/EachNavigationBar)
[![中文文档](https://woolson.gitee.io/npmer-badge/-007ec6-%E4%B8%AD%E6%96%87%E6%96%87%E6%A1%A3-007ec6-github-ffffff-square-gradient-shadow.svg)](https://github.com/Pircate/EachNavigationBar/blob/master/README_CN.md)

[中文文档](https://github.com/Pircate/EachNavigationBar/blob/master/README_CN.md)

## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

## Requirements

* iOS 9.0
* Swift 4.2

## Installation

EachNavigationBar is available through [CocoaPods](http://cocoapods.org) or [Carthage](https://github.com/Carthage/Carthage). To install
it, simply add the following line to your Podfile or Cartfile:

#### Podfile

```ruby
pod 'EachNavigationBar'
```

#### Cartfile
```ruby
github "Pircate/EachNavigationBar"
```

## Overview

![](https://github.com/Pircate/EachNavigationBar/blob/master/demo_new.gif)
![](https://github.com/Pircate/EachNavigationBar/blob/master/demo_push.gif)

## Usage

### Import

Swift
``` swift
import EachNavigationBar
```
Objective-C
``` ObjC
@import EachNavigationBar;
```

### Enable

Swift
``` swift
let nav = UINavigationController(rootViewController: vc)
nav.navigation.configuration.isEnabled = true
```

Objective-C
``` ObjC
UINavigationController *nav = [[UINavigationController alloc] initWithRootViewController:vc];
nav.navigation_configuration.isEnabled = YES;
```

### Setting
#### Global

Swift
``` swift
nav.navigation.configuration.titleTextAttributes = [.foregroundColor: UIColor.blue]

nav.navigation.configuration.barTintColor = UIColor.red

nav.navigation.configuration.shadowImage = UIImage(named: "shadow")

nav.navigation.configuration.backBarButtonItem = .init(style: .image(UIImage(named: "back")), tintColor: UIColor.red)

nav.navigation.configuration.setBackgroundImage(UIImage(named: "nav"), for: .any, barMetrics: .default)
```

Objective-C
``` ObjC
nav.navigation_configuration.titleTextAttributes = @{NSForegroundColorAttributeName: UIColor.blueColor};

nav.navigation_configuration.barTintColor = UIColor.redColor;

nav.navigation_configuration.shadowImage = [UIImage imageNamed:@"shadow"];

nav.navigation_configuration.backBarButtonItem = [[BackBarButtonItem alloc] initWithImage:[UIImage imageNamed:@"back"]];

[nav.navigation_configuration setBackgroundImage:[UIImage imageNamed:@"nav"] for:UIBarPositionAny barMetrics:UIBarMetricsDefault];
```

#### Each view controller
##### Normal

Swift
``` swift
navigation.bar  -> EachNavigationBar -> UINavigationBar
navigation.item -> UINavigationItem

// hide navigation bar
navigation.bar.isHidden = true

// set bar alpha
navigation.bar.alpha = 0.5

// set title alpha
navigation.bar.setTitleAlpha(0.5)

// set barButtonItem alpha
navigation.bar.setTintAlpha(0.5)
// if barButtonItem is customView
navigation.item.leftBarButtonItem?.customView?.alpha = 0.5
// if barButtonItem customized tintColor
navigation.item.leftBarButtonItem?.tintColor = navigation.item.leftBarButtonItem?.tintColor?.withAlphaComponent(0.5)

// remove blur effect
navigation.bar.isTranslucent = false

// hides shadow image
navigation.bar.isShadowHidden = true

// set status bar style
navigation.bar.statusBarStyle = .lightContent

// set back bar button item
navigation.bar.backBarButtonItem = .init(style: .title("Back"), tintColor: .red)

// allow back
navigation.bar.backBarButtonItem.shouldBack = { item in
    // do something
    return false
}

// handler before back
navigation.bar.backBarButtonItem.willBack = {
    // do something
}

// handler after back
navigation.bar.backBarButtonItem.didBack = {
    // do something
}

// if you want change navigation bar position
navigation.bar.automaticallyAdjustsPosition = false

// navigation bar additional height
navigation.bar.additionalHeight = 14

// navigation bar additional view
navigation.bar.additionalView = UIView()

// item padding
navigation.bar.layoutPaddings = UIEdgeInsets(top: 0, left: 8, bottom: 0, right: 8)

// shadow
navigation.bar.shadow = Shadow(
    color: UIColor.black.cgColor,
    opacity: 0.5,
    offset: CGSize(width: 0, height: 3))
```

Objective-C
``` ObjC
self.navigation_bar.xxx
self.navigation_item.xxx
```

##### LargeTitle(iOS 11.0+)

UINavigationController
``` swift
// enable
nav.navigation.prefersLargeTitles()
```
UIViewController
```swift
// show or hide
navigation.bar.prefersLargeTitles = true

// alpha
navigation.bar.setLargeTitleAlpha(0.5)
```

## Author

Pircate, gao497868860@163.com

## License

EachNavigationBar is available under the MIT license. See the LICENSE file for more info.
