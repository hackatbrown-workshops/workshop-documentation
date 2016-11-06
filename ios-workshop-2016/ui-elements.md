# More UI Elements

iOS has a ton of different controls to use in your apps. Apple's [Human Interface Guidelines][hig] have a more complete
list, but we'll cover a couple more useful ones here. As you get more familiar with iOS, it'll get easier and easier
to start using new controls. The ones we cover here give a general sense of the pattern.

## UIImageView

As you might have guessed, `UIImageView` displays images. It's a pretty handy component that lots of apps end up using
somewhere.

Before we can use it, we need some images to display. In Xcode, open the `Assets.xcassets` file. This is an *asset catalog*,
a special bundle of resource files like images and game data. It can store different versions of a file for each
kind of device. Usually, you'll have versions for different screen resolutions, but you can also break it down
by the kind of device (iPhone, Apple TV, etc.), graphics capabilities, and more. Once you have an image you want to display,
drag it onto the catalog. A new entry should pop up on the catalog sidebar and the image should appear.

Now that we have an image, we can finally show it off. Back in your storyboard, find an image view by searching in the
Object Library and drag it onto the view. In the Attributes inspector (4th tab in the right sidebar), click on the
"Image" dropdown under the "Image View" heading (it'll be the first one). The dropdown will list all the images in your
asset catalog, and once you pick one, it should appear in the image view. There are other properties you can change, such
as how the image is scaled to fit, but the defaults are fine for now.

Run the app again, and your image will appear on the screen!

Image views can also be controlled from code (such as with an `@IBOutlet`). The most useful property is `image`, which
is the image being displayed. This is an instance of `UIImage`, which is the class iOS uses to represent images in
all kinds of situations. There are a couple ways to get a `UIImage`, like from a file, by programmatically drawing it,
or from the camera. Images included with your app in the asset catalog can be loaded by name using the `UIImage(named:)`
initializer.

If you had an image view `myImageView`, you could set its image like this:

```swift
myImageView.image = UIImage(named: "some-image")
```

We won't get into it here, but `UIImageView`s can also animate a sequence of images. Check out the documentation to
see how!

## UISwitch

`UISwitch` controls are on-off switches you toggle by tapping. They have an `isOn` property that indicates whether or
not the switch is on. You can also set the state of the switch with `setOn(true/false, animated: true/false)` (the
`animated` parameter controls whether the sliding animation will be shown).

In your view controller, add this `@IBAction`:

```swift
@IBAction func switchToggled(sender: UISwitch!) {
    print("Switch changed to \(sender.isOn)")
}
```

Back in your storyboard add a switch (you can find it in the Object Library by searching for "switch"). Now, connect
its "Value Changed" event to the `switchToggled` method. When you run the app, tapping the switch will print a message
in the console.

## WKWebView

The `WKWebView` class lets you embed a browser in your app. Unfortunately, it's not supported by Interface Builder yet,
so we have to add it through code.

At the top of your view controller file, add `import WebKit` to load the WebKit module, which provides `WKWebView`.

Then, in your `viewDidLoad` method, add the following:

```swift
let webView = WKWebView(frame: self.view.frame)
webView.load(URLRequest(url: URL(string: "https://apple.com")!))
self.view.addSubview(webView)
```

This will create a web view taking up the whole screen and load the 2017 Hack@Brown website in it. There are two main
ways to load pages with a web view. You can load a URL via a `URLRequest` like we did above, or you can pass in an HTML
string directly with `loadHTMLString`.

```swift
webView.loadHTMLString("<h1>Hello, World!</h1><p>I'm HTML</p>", baseURL: URL(string: "http://2017.hackatbrown.org"))
```

The `baseURL` parameter is used to resolve relative URLs in the HTML
(so a link to `test.html` would resolve to `http://2017.hackatbrown.org/test.html`). On recent versions of iOS,
apps can only load pages over HTTPS, so websites that don't support it won't work.

[hig]: https://developer.apple.com/ios/human-interface-guidelines/
