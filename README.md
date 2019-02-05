# Flurry Analytics Plugin for Cordova #
Adds support for Flurry Analytics to your Cordova or PhoneGap apps.

This plugin was heavily inspired by https://github.com/jfpsf/flurry-phonegap-plugin.  Big thanks to its creators.

## How do I install it? ##

If you're like me and using [Cordova CLI](http://cordova.apache.org/):
```
cordova plugin add cordova-plugin-flurryanalytics2
```


TODO: add manual installation steps

## How do I use it? ##

TODO: complete usage documentation

```javascript
// Set your options
var options = {
    version: 'my_custom_version',           // overrides the version of the app
    continueSessionSeconds: 3,              // how long can the app be paused before a new session is created, must be less than or equal to five for Android devices
    userId: 'blakgeek',
    gender: 'm',                            // valid values are "m", "M", "f" and "F"
    age: 38,
    logLevel: 'ERROR',                      // Set the log level of the internal Flurry SDK logging. (VERBOSE, DEBUG, INFO, WARN, ERROR)
    enableEventLogging: false,              // Whether to enable internal logging for the Flurry SDK. Defaults to true
    setReportLocation: false,               // Set whether Flurry should record user location if your app has permission. Defaults to true.
    enableCaptureUncaughtExceptions: true,  // Android only: True to enable the ability to catch all uncaught exceptions and have them reported back to Flurry. Defaults to false.
    enableCrashReporting: true,             // iOS only: Enable automatic collection of crash reports. Defaults to false
    enableBackgroundSessions: true,         // iOS only: Enable reporting of errors and events when application is running in background. Defaults to false.
    reportSessionsOnClose: false,           // iOS only: Report session data to Flurry when the app is closed. Defaults to true.
    reportSessionsOnPause: false            // iOS only: Report session data to Flurry when the app is paused. Dfaults to true.
}

// create a new instance directly
options.appKey = '<your app key>';
flurryAnalytics = new FlurryAnalytics(options);

// or create and init it
flurryAnalytics = new FlurryAnalytics();
flurryAnalytics.init('<your app key>', options, function(){
    console.log('Initialised');
}, function(err) {
   console.error(['WTF?', err]);
});

// sets userId for this session
flurryAnalytics.setUserId('OwnUser', function() {
    console.log('Cool!');
}, function(err) {
    console.error(['WTF?', err]);
});

// sets user's age for this session
flurryAnalytics.setAge(25, function() {
    console.log('Ah yeah!');
}, function(err) {
    console.error(['WTF?', err]);
});


// sets user's for this session
flurryAnalytics.setGender('FEMALE', function() {
    console.log('woop woop!');
}, function(err) {
    console.error(['WTF?', err]);
});



// log an event to flurry
flurryAnalytics.logEvent('dinner time', function() {
    console.log('Nice!');
}, function(err) {
    console.error(['WTF?', err]);
});

// log an event to flurry with custom parameters
var ovenParams = {
    temp: 350,
    mode: 'convection',
    rackPosition: 'center'
}
flurryAnalytics.logEvent('set oven', ovenParams, function() {
    console.log('Schweet!');
}, function(err) {
    console.error(['WTF?', err]);
});

// start a timed event
flurryAnalytics.startTimedEvent('bake chicken', function() {
    console.log('Hmmmm chicken');
}, function(err) {
    console.error(['WTF?', err]);
});

// start a timed event with custom parameters
var riceParams = {
    salt: '2tsp',
    pepper: 'dash',
    water: '2cups'
}
flurryAnalytics.startTimedEvent('prep rice', riceParams, function() {
    console.log('Rice is prep started');
}, function(err) {
    console.error(['WTF?', err]);
});

// complete a timed event
flurryAnalytics.endTimedEvent('bake chicken', function() {
    console.log('Winner winner chicken dinner');
}, function(err) {
    console.error(['WTF?', err]);
});

// complete a timed event and change the value of parameters
var newRiceParams = {
    butter: '2pads'
}
flurryAnalytics.endTimedEvent('prep rice', newRiceParams, function() {
    console.log('Winner winner chicken dinner');
}, function(err) {
    console.error(['WTF?', err]);
});

// log an error
flurryAnalytics.logError('NO_EtOH', "We're out of wine and beer", function() {
    console.log('The authorities have been alerted');
}, function(err) {
    console.error(['WTF?', err]);
});

// log a page view
flurryAnalytics.logPageView(function() {
    console.log('I see you playa');
}, function(err) {
    console.error(['WTF?', err]);
});

// set the location for the event (this is will only be used for very course grained statistics like city
var location = {
    latitude: 17.2500,
    longitude: -62.6667,
    verticalAccuracy: -1, // optional iOS only
    horizontalAccuracy: 1440 // optional iOS only
}
flurryAnalytics.setLocation(location, function() {
    console.log('Party over here');
}, function(err) {
    console.error(['WTF?', err]);
});

```


