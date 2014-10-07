KINWebBrowser
==========

KINWebBrowser is a web browser module for your apps.

Powered by [WKWebView](https://developer.apple.com/library/IOs/documentation/WebKit/Reference/WKWebView_Ref/index.html) on iOS 8. Backwards compatible with iOS 7 using [UIWebView](https://developer.apple.com/library/ios/documentation/Uikit/reference/UIWebView_Class/index.html).

![KINWebBrowser Screenshots](http://i.imgur.com/z1jkWKG.png)

Features
------------------------
* iOS 7 & 8 support for iPhone and iPad devices
* Safari-like interface
* Animated progress bar
* Customizable UI including tint color
* Portrait and landscape orientation support
* Use with existing UINavigationController or present modally
* Delegate protocol for status callbacks
* Action button to allow users to copy URL, share, or open in Safari & Google Chrome
* Supports subclassing
* Installation with [CocoaPods](http://cocoapods.org/)

Overview
------------------------
KINWebBrowser consists of a single component:

`KINWebBrowserViewController` - a `UIViewController` that contains a full featured web browser.

*`KINWebBrowserViewController` must be contained in a UINavigationController.*

**Pushing to the navigation stack:**
```objective-c
KINWebBrowserViewController *webBrowser = [KINWebBrowserViewController webBrowserViewController];
[self.navigationController pushViewController:webBrowser animated:YES];
[webBrowser loadURLString:@"http://www.example.com"];
```

**Presenting Modally:**
```objective-c
UINavigationController *webBrowserNavigationController = [KINWebBrowserViewController navigationControllerWithWebBrowser];
[self presentViewController:webBrowserNavigationController animated:YES completion:nil];

KINWebBrowserViewController *webBrowser = [webBrowserNavigationController rootWebBrowserViewController];
[webBrowser loadURLString:@"http://www.example.com"];
```

Installation With CocoaPods
------------------------

[CocoaPods](http://cocoapods.org) is a dependency manager for Objective-C, which automates and simplifies the process of using 3rd-party libraries in your projects. See the ["Getting Started" for more information](http://guides.cocoapods.org/using/getting-started.html).

#### Podfile

```ruby
platform :ios, '7.0'
pod 'KINWebBrowser'
```

Customizing the User Interface
------------------------

```@property (nonatomic, strong) UIColor *tintColor;```

The tint color to apply to the bar items and progress view.

```@property (nonatomic, assign) BOOL actionButtonHidden;```

Shows the action button. When enabled the action button launches a UIActivityViewController with the URL to copy to the clipboard, share, or launch Safari or Google Chrome. This displays in a UIPopoverController on iPad devices.


```@property (nonatomic, assign) BOOL showsURLInNavigationBar;```

Once loading is complete, shows the <title> of the URL in the UINavigationBar

```@property (nonatomic, assign) BOOL showsPageTitleInNavigationBar;```

During loading, shows the URL in the UINavigationBar







Implementing `KINWebBrowserDelegate` Protocol
------------------------
`KINWebBrowserDelegate` is a set of `@optional` callback methods to inform the `delegate` of status changes.

```- (void)webBrowser:(KINWebBrowserViewController *)webBrowser didStartLoadingURL:(NSURL *)URL;```

```- (void)webBrowser:(KINWebBrowserViewController *)webBrowser didFinishLoadingURL:(NSURL *)URL;```

```- (void)webBrowser:(KINWebBrowserViewController *)webBrowser didFailToLoadURL:(NSURL *)URL withError:(NSError *)error;```


