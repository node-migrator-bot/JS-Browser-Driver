# BrowserDriver

## Installation
    npm install browser-driver

## How to use
If you have installed the npm package globally then you can do:

    browser-driver configFileName="path/to/xxx.conf.json"
    
or if not then go to the package directory and start it with node like:

    node server/server.js configFileName="path/to/xxx.conf.json"

# Browser set up
Within the conf.json config file, you need to provide an absolute link to each browser. Predictably, this isn't particularly easy as there can be various conflicts with browser windows that are already open. We have gone through this pain many times, so here's a guide for the major browsers:

- Chrome

    Thankfully Chrome is relatively straightforward, you just need to direct the user data to temp. 
    
    - OS X, simply point the user data dir to /tmp
        
            {
                "name":"Chrome",
                "app":"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome",
                "args":["--user-data-dir=/tmp"]
            }
        
    - Windows, puppies are crying already...
    
            {
                "name":"Chrome",
                "app":"",
                "args":[]
            }

- Firefox

    With Firefox, you unfortunately need to create a new profile first, via their Profile Manager. You can do this through the settings, or from the command line you pass the `-ProfileManager` switch to the executable. Lets assume that the profile name you allocate is something really original like *test*:
    
    - OS X, simply point the user data dir to /tmp
        
            {
                "name":"Chrome",
                "app":"/Applications/Firefox.app/Contents/MacOS/firefox",
                "args":["-P test"]
            }
        
    - Windows, puppies are crying already...
    
            {
                "name":"Firefox",
                "app":"",
                "args":[]
            }

## Examples
Ok, so enough with all the waffle, lets run some pre made tests! Depending on how your `npm` is set up, you need to direct the browser driver to the location of the example tests config file. Before you try to action this, please ensure that you have set up at least 1 browser inside that config file - see above for the gory details. 

Ok, so in this example, we will fire up the browser drive on OS X, by pointing to the example tests config:

    browser-driver configFileName="/usr/local/lib/node_modules/browser-driver/examples/sampleTestSuit/testing.conf.json"
    
If all is well, you should see the Browser Driver start up:

    testing server started
    reading configuration file /usr/local/lib/node_modules/browser-driver/examples/sampleTestSuit/testing.conf.json
    Server listening on port 8090 at localhost
    Go to http://localhost:8090/manager/manager.html to manage and run tests

Time to go to the above location, `http://localhost:8090/manager/manager.html` and see the shiny config page. From here, you can select the browser(s) that you set up, connect to them, then pick the tests you want to run and you will see the feedback in real-time. 