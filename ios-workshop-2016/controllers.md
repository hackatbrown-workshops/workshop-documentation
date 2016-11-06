# UI Controllers

We've implemented our own view controller, but iOS comes with a bunch of others that make our lives easier. For now,
let's go over two that have to do with navigating between other view controllers. These aren't the only kinds of
controllers iOS provides however, and others do everything from managing tables and lists to showing popup views.

## Tab Bar Controllers

Tab view controllers manage tab bars like the one in the Music app.

We can add one to our app by searching for "Tab Bar
Controller" in the Object Library and dragging it onto the scene. We'll need to change our storyboard to start with
this instead of our view controller. On the panel on the right, select the Attributes Inspector (the middle option in
tab bar at the top). Under the "View Controller" section, there should be an option for "Is Initial View Controller".
Make sure it's checked so that iOS will start with the tab bar controller.

![Initial View Controller](initial-view-controller.png)

By default, Xcode creates two new scenes with new view controllers for your tab bar.
Click on one of them and find the corresponding Tab Bar Item in the scene on the
left panel (it'll look like a white square with a blue star). Give it an icon
by choosing one from the "System Item" dropdown (you can also use an icon of your own).

![Tab Bar Item options](tab-bar-item.png)

Drag a label onto the view and add some text to it. Do the same to the other new view so
we can tell them apart. Try running the app and switching between the two tabs!

We can also add our existing view controller as a tab. Select the Tab Bar Controller scene
and go to the Connections inspector. Next to "view controllers" under "Triggered Segues"
you should see two view controller entries - the ones added by Xcode. Drag from the filled
circle (which should change to a plus when you hover over it) all the way over to your view controller.

![Connecting your view controller](connecting-view-controllers.png)

This will create an item in your view controller's scene, where you can tweak the icon
and text.

Run the app again and you should be able to get to all three view controllers!

Besides being a useful way to get around in your apps, tab bar controllers show how a lot
of view controllers, particularly the Apple-provided ones, work with other view controllers
to make all sorts of magic happen 🎉

## Navigation Controllers
