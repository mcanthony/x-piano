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
  
[http://korilakkuma.github.io/x-piano/demo/import.html](http://korilakkuma.github.io/x-piano/demo/import.html)
  
## Usage
  
<x-piano> tag can be used by the following HTML.
  
    <link rel="import" href="x-piano/x-piano.html" />
  
To import 'x-piano.html', then describe &lt;x-piano&gt; tag.
  
    <x-piano></x-piano>
  
Moreover, &lt;x-piano&gt; tag can have some attributes.  
For example,
  
    <x-piano type="sawtooth" volume="0.4" attack="1" glide="1.5"></x-piano>
  
Refer to the following table for attribute details.
  
|  Attribute | Description                  | Value                                                      |
|:-----------|:-----------------------------|:-----------------------------------------------------------|
| type       | Sound Source                 | 'piano' (default), 'sin', 'square', 'sawtooth', 'triangle' |
| volume     | Master Volume                | 0.0 - 1.0 (1.0  by default)                                |
| attack     | Envelope Generator (Attack)  | 0.0 - 1.0 (0.01 by default)                                |
| decay      | Envelope Generator (Decay)   | 0.0 - 1.0 (0.3  by default)                                |
| sustain    | Envelope Generator (Sustain) | 0.0 - 1.0 (1.0  by default)                                |
| release    | Envelope Generator (Release) | 0.0 - 1.0 (1.0  by default)                                |
| transpose  | Transpose                    | Integer   (0    by default)                                |
| glide      | Glide (Oscillator only)      | 0.0 -     (0.0  by default)                                |
| value      | Keyboard Index               | JSON (readonly)                                            |
  
## Callbacks
  
The following callbacks is invoked when keyboard was either down or up.
  
    var xpiano = document.querySelector('x-piano');

    /**
     * This callback is invoked when keyboard was down.
     * @param {HTMLElement} element This argument is the instance of HTMLElement that is added event listener.
     * @param {number} index This argument is the index of keyboard where event occurred.
     *     This value is between 0 and 87.
     */
    xpiano.onDownCallback = function(element, index) {
        console.log(index + ' :');
        console.dir(element);
    };

    /**
     * This callback is invoked when keyboard was up.
     * @param {HTMLElement} element This argument is the instance of HTMLElement that is added event listener.
     * @param {number} index This argument is the index of keyboard where event occurred.
     *     This value is between 0 and 87.
     */
    xpiano.onUpCallback = function(element, index) {
        console.log(index + ' :');
        console.dir(element);
    };
  