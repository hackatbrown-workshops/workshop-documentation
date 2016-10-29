# Using Web APIs in iOS Apps

There's a whole world of useful data and services out there for your app to use, and
[APIs (Application Programming Interfaces)][what-is-an-api] are how it can access it all.

Many APIs, like those for Facebook and Twitter, have iOS clients that you can use in your code. We'll get to those in a
bit, but first, let's start from the basics of how you can make a request to *any* API.

## NSURLSession

The set of classes for making web requests on iOS is called `NSURLSession`. We'll use the Brown [Laundry API][laundry-api].

You first need to create an instance of `NSURLSession`. This manages ongoing requests and describes how they should
be made (like where cookies are kept).

```swift
// Create a NSURLSession with the default configuration, which works like a browser would
let mySession = NSURLSession(configuration: NSURLSession.defaultSessionConfiguration())
```

Once you have a session, you can start loading data with it!

```swift
// Most APIs use a client ID to keep track of who's using them.
// You can sign up for a Brown API client ID here: https://api.students.brown.edu/signup
let myClientId = "..."

// List all the machines in the Perkins laundry room
let perkinsUrl = NSURL(string: "https://api.students.brown.edu/laundry/rooms/1429235/machines?client_id=\(myClientId)&get_status=true")!

let task = mySession.dataTaskWithUrl(perkinsUrl) {
    data, response, error in

    // Did something go wrong making the request?
    if let error = error {
        print(error.localizedDescription)
    } else if let httpResponse = response as? NSHTTPURLResponse {
        // In the HTTP protocol, a status code of 200 indicates that everything's ok
        if httpResponse.statusCode == 200 {
            // Parse the results
            let json = try? JSONSerialization.jsonObject(with: data, options: [])
            if let root = json as? [String: Any] {
                if let machines = root["results"] as? [Any] {
                    print(machines)
                }
            }
        }
    }
}

// All tasks start out suspended, so start the task with resume()
task?.resume()
```

There's a lot going on here, so we'll break it down piece-by-piece.

First, we construct the URL to request. Whatever API you choose will have documentation describing what kinds of data
you can fetch and what URLs to use. In this case, we set `perkinsUrl` to the URL for the list of machines in the
Perkins laundry room (with ID `1429235`).

Next, we start a data task for the URL with our `NSURLSession`. In order to not slow down the UI, iOS makes network
requests in the background, and it models these as tasks that can be started and stopped and have an associated
completion handler. That handler is the block of code after the `dataTaskWithUrl` call. The handler will be called
with the data fetched, any error that occurred, and the response object.

In the handler, the first thing we do is check if an error occurred and print out a message if it did. Then, if there
was no error, we check the status code of the HTTP response. This indicates different kinds of errors than the `error`
parameter. A HTTP error would mean there was something wrong with the request we made, or something happened on the server
so it couldn't send us data back. The `error` parameter is for things like network failures where we can't even get
anything back from the server.

If the response we got back is ok, we can parse our data! The Laundry API, like many others, uses [JSON][json] to encode
results. Because it's so common, iOS has the `JSONSerialization` class to parse JSON into Swift objects like
dictionaries and arrays. We'll parse the JSON and extract the array of machines (in the `results` key), which we then
print. In a real app, you could use this data to update the UI.

## Facebook

Facebook has an entire library of code you can use in iOS apps for things like letting people sign in with their Facebook
accounts, sharing things in Messenger, and searching the Facebook graph. There's too much to cover here, but check
out their [getting started guide](https://developers.facebook.com/docs/ios/getting-started/)!

## Firebase

[Firebase][firebase] is a bit different from other APIs. It's a [backend-as-a-service][BaaS], which provides server
features like user management and push notifications without you having to write backend code. Because of all this
flexibility and power, it has a steeper learning curve and takes more setup. Fortunately, Firebase has a super comprehensive
[getting started guide](https://firebase.google.com/docs/ios/setup) and [walkthrough](https://codelabs.developers.google.com/codelabs/firebase-ios-swift/#0) that goes through downloading
and using it.

## Other Resources

* [NSURLSession Tutorial: Getting Started](https://www.raywenderlich.com/110458/nsurlsession-tutorial-getting-started)

[what-is-an-api]: https://medium.freecodecamp.com/what-is-an-api-in-english-please-b880a3214a82#.7stsdgmga
[laundry-api]: https://api.students.brown.edu/docs/laundry
[json]: https://en.wikipedia.org/wiki/JSON
[BaaS]: https://en.wikipedia.org/wiki/Mobile_backend_as_a_service
[firebase]: https://firebase.google.com/
