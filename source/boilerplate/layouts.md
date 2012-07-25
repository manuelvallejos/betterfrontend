# Main application layout

The main layout of an application should be called,
`application.html.haml`

We don't recommend using any other name for the "main" layout due to
consistency. Frameworks like Ruby on Rails already default to using
"application" for anything top-level, we should respect the same
convention on the front-end layer.

## application.html.haml

```
<!doctype html>
/ paulirish.com/2008/conditional-stylesheets-vs-css-hacks-answer-neither/
/[if lt IE 7] <html class="no-js lt-ie9 lt-ie8 lt-ie7" lang="en">
/[if IE 7] <html class="no-js lt-ie9 lt-ie8" lang="en">
/[if IE 8] <html class="no-js lt-ie9" lang="en">
/ Consider adding a manifest.appcache: h5bp.com/d/Offline
/ [if gt IE 8]><!
%html.no-js{:lang => "en"}
  / <![endif]
  %head
    %meta{:charset => "utf-8"}/
    /
      Use the .htaccess and remove these lines to avoid edge case issues.
      More info: h5bp.com/i/378
    %meta{:content => "IE=edge,chrome=1", "http-equiv" => "X-UA-Compatible"}/
    %title= data.page.title || "The Middleman"
    %meta{:content => "", :name => "description"}/
    / Mobile viewport optimized: h5bp.com/viewport
    %meta{:content => "width=device-width, initial-scale=1.0", :name => "viewport"}/
    / Place favicon.ico and apple-touch-icon.png in the root directory: mathiasbynens.be/notes/touch-icons
    = stylesheet_link_tag "application"
    / More ideas for your <head> here: h5bp.com/d/head-Tips
    /
      All JavaScript at the bottom, except this Modernizr build.
      Modernizr enables HTML5 elements &amp; feature detects for optimal performance.
      Create your own custom Modernizr build: www.modernizr.com/download/
    = javascript_include_tag 'top/modernizr.foundation'
  %body{:class => page_classes}
    /
      Prompt IE 6 users to install Chrome Frame. Remove this if you support IE 6.
      chromium.org/developers/how-tos/chrome-frame-getting-started
    /[if lt IE 7] <p class=chromeframe>Your browser is <em>ancient!</em> <a href="http://browsehappy.com/">Upgrade to a different browser</a> or <a href="http://www.google.com/chromeframe/?redirect=true">install Google Chrome Frame</a> to experience this site.</p>
    %header{:role => "banner"}
    %div.content{:role => "main"}
      = yield
    %footer{:role => "contentinfo"}
    / JavaScript at the bottom for fast page loading
    = javascript_include_tag  "application"
    / end scripts
    :javascript
      hljs.initHighlightingOnLoad();
    /
      Asynchronous Google Analytics snippet. Change UA-XXXXX-X to be your site's ID.
      mathiasbynens.be/notes/async-analytics-snippet
    :javascript
      var _gaq=[['_setAccount','UA-XXXXX-X'],['_trackPageview']];
      (function(d,t){var g=d.createElement(t),s=d.getElementsByTagName(t)[0];
      g.src=('https:'==location.protocol?'//ssl':'//www')+'.google-analytics.com/ga.js';
      s.parentNode.insertBefore(g,s)}(document,'script'));
```