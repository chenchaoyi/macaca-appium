# Introduction ##
#### A brief introduction of 
* How to use [Macaca](macacajs.github.io/macaca/) to run [Appium](http://appium.io/) test
* How to work around Appium to use XCUItest underlayer

This repo provides simple instructions on setup Macaca locally to run your existed Appium tests, as well as [setup Appium to use XCUItest underlayer](#setup-appium-to-use-xcuitest) if you would like to stick with Appium.

## Note ##
Disconnect your VPN before starting Macaca or Appium XCUItest server, it confuses on network interfaces otherwise.

## Why ##

Appium has been around for 5 years, yet I couldn't find any alternative solution until Macaca was introduced last year. 

* The Automation instrument has been removed from Instruments since Xcode 8 beta 2. While Appium still struggles to migrate to XCUItest underlayer, Macaca has already done the switch.

* Macaca supports multiple selenium sessions in single test.

The following instruction is for **iOS** for now.

## Installation ##
* Install [Node.js >= v0.12.x and npm](http://nodejs.org/)
* Create a new folder:
```bash
$ mkdir macaca-tryout
$ cd macaca-tryout
```
* Install macaca client locally:
```bash
$ npm install macaca-cli
```
* Install macaca iOS driver locally
```bash
$ npm install macaca-ios
```

And that's it, all setup is done.

## Usage ##

* Start macaca server on Appium server port:

```bash
$ ./node_modules/.bin/macaca server --verbose -p 4723
```

* Now you can run your Appium test just as it is. Macaca server replaces Appium server, and you are all set to see your tests running with XCUItest instead of the deprecated UIAutomator underlayer.

## Macaca Inspector ##
Macaca provides a [Web based inspector]
(macacajs.github.io/macaca/inspector.html) for you to locate App elements,
just like the Appium UI inspector.

To try it out:

* Create a new folder:
```bash
$ mkdir macaca-inspector
$ cd macaca-inspector
```
* Install macaca client (I don't recommend to install it globally):
```bash
$ npm install app-inspector
```
* Use it (for iOS)
```bash
# Get the UDID of your simulator
$ xcrun simctl list
# Start your selected simulator
$ open -a Simulator --args -CurrentDeviceUDID "${this.deviceId}"
# Start Macaca inspector, then point your browser to the address as showed in the terminal
$ ./node_modules/.bin/app-inspector -u "${this.deviceId}"
```

## Setup Appium to use XCUItest ##
### Start Appium from latest source ###
```bash
# Clone Appium repo and install node modules
$ git clone git@github.com:appium/appium.git
$ cd appium
$ npm install
$ ./node_modules/.bin/gulp transpile
# Install webpack
$ npm install webpack-dev-server -g
# Start Appium server
$ node .
```
### Run test with XCUItest ###
* Add `"automationName": "xcuitest"` to capabilities, then you are ready to run your Appium test with XCUItest underlayer.
* For XPath, the previous `UIA` class name needs to be changed to `XCUIElementType` class name. e.g.: UIATableCell -> XCUIElementTypeCell
 
For a full list of reference, please refer to [this](http://masilotti.com/xctest-documentation/Constants/XCUIElementType.html).
