# What is this?

This is a simple example of using a recent node nightly build to demonstrate the
recent `--inspect` flag allowing chrome debugging of node, as described in
https://github.com/nodejs/node/issues/7072.

Download a recent nightly build, e.g.

    wget https://nodejs.org/download/nightly/v7.0.0-nightly20160604de0aa23ad7/node-v7.0.0-nightly20160604de0aa23ad7-darwin-x64.tar.gz

Uncompress the tar.gz file:

    tar -xvzf node-v7.0.0-nightly20160604de0aa23ad7-darwin-x64.tar.gz

Install the test app:

    cd test && npm install

Run the test node app:

    cd test && npm start

You should then see something like:

    $ npm start

    > test@1.0.0 start /Users/jasondarwin/workspace/node2/test
    > ../node-v7.0.0-nightly20160604de0aa23ad7-darwin-x64/bin/node --inspect index.js

    Debugger listening on port 5858.
    To start debugging, open the following URL in Chrome:
        chrome-devtools://devtools/remote/serve_file/@521e5b7e2b7cc66b4006a8a54cb9c4e57494a5ef/inspector.html?experiments=true&v8only=true&ws=localhost:5858/node
    Example app listening on port 3000!

Visit the URL in a chrome tab, and check the `sources` tab -- you can place a breakpoint, say, on line 5

    res.send('Hello World!');

Now, visit http://localhost:3000/ in another tab to trip the breakpoint -- you should see the breakpoint tripped
in the devtools tab, and in the tab with your app at http://localhost:3000/ you'll see it still spinning.

In the devtools tab, bring up the console and enter:

    res.send('Bonjour el Mundo!');

In your app tab, you should now see this appear.
