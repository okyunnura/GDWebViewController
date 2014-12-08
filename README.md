GDWebViewController
===================

A simple view controller for navigating web pages using WKWebView

![App Screenshots](https://cloud.githubusercontent.com/assets/3193877/5335431/6512a96c-7e5e-11e4-9631-2b7eb8e49657.gif)

## Description
- A browser-like view controller to support web pages navigation in your Swift app.
- Supports back-forward navigation and page refresh action.
- Has built-in activity indicators (both progress view and activity indicator).

## Installation
Just grab two files `GDWebViewController.swift` and `GDWebViewNavigationToolbar.swift` into your project.<br />
You can download `GDWebBrowserClient` project as well to see how it can be used.

## Interface
####Properties
`weak var delegate: GDWebViewControllerDelegate?`<br />
An object to serve as a delegate which conforms to GDWebViewNavigationToolbarDelegate protocol.

`var progressIndicatorStyle: GDWebViewControllerProgressIndicatorStyle = .Both`<br />
The style of progress indication visualization. Can be one of four values: .ActivityIndicator, .ProgressView, .Both, .None

`var allowsBackForwardNavigationGestures: Bool`<br />
A Boolean value indicating whether horizontal swipe gestures will trigger back-forward list navigations. The default value is false.

`var showToolbar: Bool`<br />
A boolean value if set to true shows the toolbar; otherwise, hides it.

`var showRefreshControl: Bool`<br />
A boolean value if set to true shows the refresh control on the toolbar; otherwise, hides it.

`var toolbar: GDWebViewNavigationToolbar`<br />
The navigation toolbar object (read-only).
####Methods
`func loadURLWithString(URLString: String)`<br />
Navigates to an URL created from provided string.

`func loadURL(URL: NSURL, cachePolicy: NSURLRequestCachePolicy = .UseProtocolCachePolicy, timeoutInterval: NSTimeInterval = 0)`<br />
Navigates to the URL.

`func showToolbar(show: Bool, animated: Bool)`<br />
Shows or hides toolbar.

####GDWebViewControllerDelegate Methods
```
@objc protocol GDWebViewControllerDelegate {
    optional func webViewController(webViewController: GDWebViewController, didChangeURL newURL: NSURL?)
    optional func webViewController(webViewController: GDWebViewController, didChangeTitle newTitle: NSString?)
    optional func webViewController(webViewController: GDWebViewController, decidePolicyForNavigationAction navigationAction: WKNavigationAction, decisionHandler: (WKNavigationActionPolicy) -> Void)
    optional func webViewController(webViewController: GDWebViewController, decidePolicyForNavigationResponse navigationResponse: WKNavigationResponse, decisionHandler: (WKNavigationResponsePolicy) -> Void);
    optional func webViewController(webViewController: GDWebViewController, didReceiveAuthenticationChallenge challenge: NSURLAuthenticationChallenge, completionHandler: (NSURLSessionAuthChallengeDisposition, NSURLCredential!) -> Void);
}
```

Notice:<br />
You must do `import WebKit` if you use last three methods from `GDWebViewControllerDelegate` description.
