[mmir][11]
====

<p align="center">
<img width="10%" src="https://raw.githubusercontent.com/wiki/mmig/mmir/images/logo.png">
</p>

Overview for the MMIR (Mobile Multimodal Interaction and Rendering) Framework. 


##### Related repositories

- core
 * [mmir-lib][4]: the core library _(this is usually included in the directory `mmirf/` of MMIR-based applications)_
 * [mmir-tooling][5]: scripts and resources for building and generating resources _(e.g. compiling JSON grammars)_
- tools
 * [scion-queue-plugin][6]: a Cordova 5.x plugin that provides an event-queue for SCION (used by the dialog manager)
- speech modules
 * [mmir-plugin-speech-android][14]: a Cordova 5.x plugin that integrates Android's default speech recognizer and text-to-speech engines into the MMIR framework (platforms: android)
 * [mmir-plugin-speech-android][15]: a Cordova 5.x plugin that integrates the Nuance SpeechKit (Dragon Mobile SDK) for speech recognition and text-to-speech (platforms: android, ios)
 * WebKit SpeechRecognizer (included in core framework): a module for integrating Google Chrome's SpeechRecognition into the MMIR framework (platforms: browser _(Chrome only)_)
 * MARYTTS (included in core framework): a module for integrating MARY TTS service (an Open Source speech synthesis) into the MMIR framework (platforms: all)
- examples
 * [mmir-cordova][9]: resources / example for creating a minimal MMIR-based application _(for Cordova 5.x)_
 * [mmir-starter-kit][10]: a small MMIR-based example application _(for Cordova 5.x)_

## Documentation

See the **[wiki][8]** for the main documentation.


See [API][12] documentation for information about the `mmir-lib` interface (or the even more detailed API doc with [private-visibility][13]).


See the README in [mmir-cordova][9] for step-by-step instruction on how to (1) create a new Cordova project and (2) add the MMIR framework


## Introduction

The MMIR (Mobile Multimodal Interaction and Rendering) framework aims to provide a 
lightweight multimodal dialog manager that -- for instance -- can run on mobile devices. 
The base technology is HTML5 (JavaScript).

A core concept for the framework is the MVC (Model View Controller) pattern. The framework provides a template
mechanism similar to JSP (Java Server Pages), ASP (Active Server Pages), and alike.

The state of the dialog system can be tracked and manipulated based on a finite-state machine (FSM).
The framework uses SCXML (State Chart XML) via [SCION][1]: SCION is a JavaScript-based interpreter for SCXML files.

The framework core and its extensions are implemented as AMD (Asynchronous Module Definition) using [RequireJS][3].


The MMIR library provides basic capabilities for recognizing speech input (ASR, using the Google Speech Recognition service), and speech output (TTS, using [MARY][2]).

NOTE 1: There are some restrictions for ASR when running the StarterKit in a browser environment:
 * microphone access: currently only Google Chrome (version 21.x.x), and Firefox (version 20.x) allow access to the microphone resource for speech input
 * silence detection: currently only Google Chrome (version 25.x.x) and Firefox (version 26.x) provide an implementation for the AudioContext object, which is needed by our implementation for the end-of-speech detection (aka silence detection) 

NOTE 2: Since the Google Speech Recognition service now requires registration and an API key (and has a volume limit),
        the use of the general (i.e. _HTML5 based_) ASR solution of the framework is rather limited.
        However, for the browser environment Google Chrome, we recommend the _webkitAudioInput_ plugin
        that makes use of the
        [Web Speech API][7] (which, unfortunately, currently is only supported by Chrome).

## Prerequisites

Installed Cordova 5.x environment (see [Cordova][0] documentation on CLI based development for more details).

In addition, the development tools for the targeted `platforms` need to be installed (see also the [Cordova][0] documentation).

##### Custom Cordova Plugins

If you plan to use the MMIR framework in combination with SCION (that is: make use of
the framework's ```DialogManager``` and/or ```InputManager```) within an environment that __does not__
support HTML5 ```WebWorkers```, you need the [Queue Plugin][6] for extending the framework's SCION  
integration with an event queue.



[0]: http://cordova.apache.org/
[1]: https://github.com/jbeard4/SCION
[2]: http://mary.dfki.de/
[3]: http://requirejs.org/
[4]: https://github.com/mmig/mmir-lib
[5]: https://github.com/mmig/mmir-tooling
[6]: https://github.com/mmig/mmir-plugin-scionqueue
[7]: https://dvcs.w3.org/hg/speech-api/raw-file/tip/speechapi.html
[8]: https://github.com/mmig/mmir/wiki
[9]: https://github.com/mmig/mmir-cordova
[10]: https://github.com/mmig/mmir-starter-kit
[11]: https://github.com/mmig/mmir
[12]: https://mmig.github.io/mmir/api
[13]: https://mmig.github.io/mmir/api-all
[14]: https://github.com/mmig/mmir-plugin-speech-android
[15]: https://github.com/mmig/mmir-plugin-speech-nunace
