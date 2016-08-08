# Introduction ##
#### A brief introduction of how to use [Macaca](macacajs.github.io/macaca/) to run [Appium](http://appium.io/) test

Appium has been around for 5 years, yet I couldn't find any alternative solution until Macaca was introduced last year. This repo provides simple instructions on setup Macaca locally to run your existed Appium tests.


## Installation ##
* Install [Node.js >= v0.12.x and npm](http://nodejs.org/)
* Create a new folder:
```bash
$ mkdir macaca-tryout
$ cd macaca-tryout
```
* Install macaca client:
```bash
$ npm install macaca-cli
```
And that's it, all setup is done.

## Usage ##

* Start macaca server on Appium server port:

```bash
$ ./node_modules/.bin/macaca --verbose server -p 4723
```

* Now you can run your Appium test just as it is, Macaca server replaces Appium server, and you are all set to see your tests running with XCUItest instead of the deprecated UIAutomator underlayer.

