# Authsafe-iOS-2-

**Description :-**
AuthSafe sdk helps us to detect suspicious activities in real time and provides device fingerprinting, behavioral analysis, and client-side event monitoring.

**Configuretion Requirements**
---
* iOS 9.0+<br>
* Xcode 9.0+

**Installation**
---
Authsafe iOS SDK is available through CocoaPods.

**CocoaPods**

```
pod "Authsafe", "1.0.0"
```

**Manually**

Download the zip file from the github release, unzip and drag Authsafe.xcframework to the Frameworks, Libraries and Embedded Content section of the target. They should all be set to Embed & Sign.


**Implementation Steps**
---

// Place the below code in your AppDelegate didFinishLaunchingWithOptions method

**Objective-C**

```
[Authsafe configure:@"Your secret key"];
[Authsafe trackAppEvent:@"open"];
```

**Swift**

```
  Authsafe.configure("your secret key")
  Authsafe.trackAppEvent("open")
```

The AuthSafe SDK collects device fingerprints from the device and sends this data directly to Authsafe Dashboard.

**Events**

1. Application Event: - In the application event Authsafe track your application lifecycle.<br>
Implement below all methods in your AppDelegete.

**Objective-C**

```
- (void)applicationDidBecomeActive:(UIApplication *)application{
	[Authsafe trackAppEvent:@"active"];
}

- (void)applicationWillResignActive:(UIApplication *)application{
	[Authsafe trackAppEvent:@"inactive"];
}

- (void)applicationDidEnterBackground:(UIApplication *)application{
	[Authsafe trackAppEvent:@"background"];
}

- (void)applicationWillEnterForeground:(UIApplication *)application{
	[Authsafe trackAppEvent:@"foreground"];
}

- (void)applicationWillTerminate:(UIApplication *)application{
	[Authsafe trackAppEvent:@"terminate"];
}
```

**Swift**

```
    func applicationDidBecomeActive(_ application: UIApplication) {
        Authsafe.trackAppEvent("active")
    }
    
    func applicationWillResignActive(_ application: UIApplication) {
    	Authsafe.trackAppEvent("inactive")
    }

    func applicationDidEnterBackground(_ application: UIApplication) {
        Authsafe.trackAppEvent("background")
    }
    
    func applicationWillEnterForeground(_ application: UIApplication) {
        Authsafe.trackAppEvent("foreground")
    }
 
    func applicationWillTerminate(_ application: UIApplication) {
        Authsafe.trackAppEvent("terminate")
    }
    
```

2. Click Events: - In the click events Authsafe sdk is tracking your every click event. Authsafe will handle the whole functionality and working itself like gyroscope cord., screen orientation with screen X Y coordinates you just need to call the methods.
There are two main parts of click events.

 * Gyroscope X Y Z coordinates<br>
 * Screen X Y coordinates with screen orientation

// Place the below code in your Every ViewController viewDidLoad method

**Objective-C**

```
  UITouch *touch = [[UITouch alloc]init];
  [Authsafe trackClickEvent:@"Current Screen Name" screenOrientation:self.supportedInterfaceOrientations view:self.view touch:touch]; 
```

**Swift**

```
   let touch = UITouch()
   Authsafe.trackClickEvent("Current Screen Name", screenOrientation:UIApplication.shared.statusBarOrientation, view: self.view, touch:touch)
```

3. Location Event: -This event useful for fast geo track location.
In this event you need to get permission from the user, then you need call the below method.
Add these lines in your info.plist 

```
 <key>NSLocationAlwaysAndWhenInUseUsageDescription</key>
 <string>Application requires user’s location for better user experience.</string>

 <key>NSLocationAlwaysUsageDescription</key>
 <string>Application requires user’s location for better user experience.</string>

 <key>NSLocationWhenInUseUsageDescription</key>
 <string>Application requires user’s location for better user experience.</string>
   
```

**Objective-C**

```
//For logging location event, three parameter required screen name, latitude, longitude.
 [Authsafe trackLocationEvent:@"Current Screen Name" latitude:location.coordinate.latitude longitude:location.coordinate.longitude]; 
```

**Swift**

```
//For logging location event, three parameter required screen name, latitude, longitude.
 Authsafe.trackLocationEvent("Current Screen Name", latitude: location?.coordinate.longitude, longitude: location?.coordinate.longitude)
```


4. Login Event: -For tracking login event you need to send the authafe token and bundle id name with your login request.

**Objective-C**

```
key = "request_token"
value = [Authsafe getLoginRequestToken:_latitute longitude:_longitude];

NSString *bundleID = [[NSBundle mainBundle] bundleIdentifier];
key = "package"
value = bundleID

```

**Swift**

```
key = "request_token"
value = AuthSafe.getLoginRequestToken(latitude, longitude: longitude)


var bundleID:String = Bundle.main.bundleIdentifier!
key = "package"
value = bundleID

```


Thank you!
Copyright@Authsafe.ai


