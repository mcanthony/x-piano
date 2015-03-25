x-piano
=========
  
Web Components for Web Audio API
  
## Overview
  
&lt;x-piano&gt; is GUI parts library (Web Components) for Web Applications that use Web Audio API.
&lt;x-piano&gt; has has the following features.
  
* Rich UI by Simple tag
* Play the One-Shot Audio
* Create Sound
* Simple Effector (Envelope Generator, Transpose, Glide)
  
## Demo
  
* [Non Polymer](http://korilakkuma.github.io/x-piano/demo/import.html)
* [Use Polymer](http://korilakkuma.github.io/x-piano/demo/import-polymer.html)
  
## Browser Support
  
|![Chrome](https://cloud.githubusercontent.com/assets/398893/3528328/23bc7bc4-078e-11e4-8752-ba2809bf5cce.png)|![Opera](https://cloud.githubusercontent.com/assets/398893/3528330/27ec9fa8-078e-11e4-95cb-709fd11dac16.png)|![Firefox](https://cloud.githubusercontent.com/assets/398893/3528329/26283ab0-078e-11e4-84d4-db2cf1009953.png)|![Safari](https://cloud.githubusercontent.com/assets/398893/3528331/29df8618-078e-11e4-8e3e-ed8ac738693f.png)|
|----------|----------|----------|----------|
| Latest ✔ | Latest ✔ | Latest ✔ | Latest ✔ |
   
## Installation
  
    $ bower install --save-dev x-piano
  
## Usage
  
&lt;x-piano&gt; tag can be used by the following HTML.
  
    <script type="text/javascript">
    <!--
        // This is invoked when import HTML is success.
        var onLoadCallback = function(event) {
            // do something for main document
        };

        // This is invoked when import HTML is failure.
        var onErrorCallback = function(event) {
            // do something for error
        };
    //-->
    </script>
    <link rel="import" href="x-piano/x-piano.html" type="text/html" onload="onLoadCallback(event)" onerror="onErrorCallback(event)" />
  
or,
  
    <script type="text/javascript">
    <!--
        (function() {
            // Create <link> tag for import HTML dynamically
            var link = document.createElement('link');

            link.setAttribute('rel', 'import');
            link.setAttribute('href', 'x-piano/x-piano.html');
            link.setAttribute('type', 'text/html');

            // This is invoked when import HTML is success.
            link.onload = function(event) {
                // do something for main document
            };

            // This is invoked when import HTML is failure.
            link.onerror = function(error) {
                // do something for error
            };

            document.querySelector('head').appendChild(link);
        })();
    //-->
    </script>
  
In the case of using Polymer,
  
    <script type="text/javascript" src="bower_components/webcomponentsjs/webcomponents.min.js"></script>
    <link rel="import" href="x-piano-polymer/x-piano.html" type="text/html" />
  
To import 'x-piano.html', then describe &lt;x-piano&gt; tag.
  
    <x-piano></x-piano>
  
Moreover, &lt;x-piano&gt; tag can have some attributes.  
For example,
  
    <x-piano type="sawtooth" volume="0.4" attack="1" glide="1.5"></x-piano>
  
Refer to the following table for attribute details.
  
|  Attribute | Description                  | Value                                                                      |
|:-----------|:-----------------------------|:---------------------------------------------------------------------------|
| ui-only    | Not use sound                | boolean attribute                                                          |
| responsive | Responsive Layout            | boolean attribute                                                          |
| theme      | Piano Design                 | 'normal' (default), 'fiber', 'wood', 'crystal', 'flat', 'keyboard', 'none' |
| type       | Sound Source                 | 'piano' (default), 'sin', 'square', 'sawtooth', 'triangle'                 |
| volume     | Master Volume                | 0.0 - 1.0 (1.0  by default)                                                |
| attack     | Envelope Generator (Attack)  | 0.0 - 1.0 (0.01 by default)                                                |
| decay      | Envelope Generator (Decay)   | 0.0 - 1.0 (0.3  by default)                                                |
| sustain    | Envelope Generator (Sustain) | 0.0 - 1.0 (1.0  by default)                                                |
| release    | Envelope Generator (Release) | 0.0 - 1.0 (1.0  by default)                                                |
| transpose  | Transpose                    | Integer   (0    by default)                                                |
| glide      | Glide (Oscillator only)      | 0.0 -     (0.0  by default)                                                |
| value      | Keyboard Index               | JSON (readonly)                                                            |
  
### Callbacks
  
The following callbacks is invoked when keyboard was either down or up.
  
    var xpiano = document.querySelector('x-piano');

    /**
     * This callback is invoked when keyboard was down.
     * @param {HTMLElement} element This argument is the instance of HTMLElement that is added event listener.
     * @param {number} index This argument is the index of keyboard where event occurred.
     *     This value is between 0 and 87.
     */
    xpiano.onkeyboarddown = function(element, index) {
        console.log(index + ' :');
        console.dir(element);
    };

    /**
     * This callback is invoked when keyboard was up.
     * @param {HTMLElement} element This argument is the instance of HTMLElement that is added event listener.
     * @param {number} index This argument is the index of keyboard where event occurred.
     *     This value is between 0 and 87.
     */
    xpiano.onkeyboardup = function(element, index) {
        console.log(index + ' :');
        console.dir(element);
    };
  
### Trigger
  
The sound is created by triggering event.
  
    var xpiano = document.querySelector('x-piano');

    /**
     * This method triggers event.
     * @param {number} index This argument is between 0 and 87.
     * @param {boolean} isDown If this argument is true, the designated keyboard is down.
     *     Otherwise, the designated keyboard is up.
     */
    xpiano.trigger(index, isDown);
  
For example,
  
    var xpiano = document.querySelector('x-piano');

    window.setTimeout(function() {
        // A (440 Hz) start
        xpiano.trigger(48, true);

        window.setTimeout(function() {
            // A (440 Hz) stop
            xpiano.trigger(48, false);
        }, 1000);
    }, 1000);
  
