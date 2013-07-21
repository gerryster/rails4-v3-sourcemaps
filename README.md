# SASS Version 3 Source Map in Rails

This application exists to get [version 3 source maps](https://docs.google.com/document/d/1U1RGAehQwRypUTovF1KRlpiOFze0b-_2gc6fAH0KY0k/edit#heading=h.75yo6yoyk7x5) working with SASS in a Rails application.  I have had no luck with the Rails application.  Even though I am using a version of the sass gem which supports version 3 source maps, I believe the current problem is that the sass-rails gem lacks support for creating and knowing how to serve the "*.css.map files".

## Sanity Check

To make sure I understood how the v3 source maps work, I created a little mini static application in the "static-world" directory where I compiled the one SCSS file directly with the following comment run from withing the static-world directory:

```bash
$ be sass --watch --sourcemap styles.css.scss
```

I then started a static web server in the same directly via:

```bash
$ ruby -rwebrick -e'WEBrick::HTTPServer.new(:Port => 3002, :DocumentRoot => Dir.pwd).start'
```

This works great in the Chrome Canary but to my surprise does not work at all in Chrome 28.0.1500.71.  This also does not work in Firefox 22 but I have not tried any bleeding edge builds of Firefox.  From what I can tell, [v3 source maps may be supported in Firefox 23](https://wiki.mozilla.org/DevTools/Features/SourceMap).  [This plugin](https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/) may also get Firefox stable working.

## Other Findings

Sass 3.3 does not play well with compass (0.12.2) as documented [here](https://github.com/chriseppstein/compass/issues/1339).
