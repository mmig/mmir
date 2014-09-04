[mmir][11]
====

<p align="center">
<img width="20%" src="https://raw.githubusercontent.com/wiki/mmig/mmir/images/logo.png">
</p>

Overview for the MMIR (Mobile Multimodal Interaction and Rendering) Framework. 


##### Related repositories

- core
 * [mmir-lib][4]: the core library (this is usually included in the directory `mmirf/` of MMIR-based applications)
 * [mmir-tooling][5]: scripts and resources for building and generating resources (e.g. compiling JSON grammars)
- tools
 * [scion-queue-plugin][6]: a Cordova 3.x plugin that provides an even-queue for SCION
- examples
 * [mmir-cordova][9]: resources / example for creating a minimal MMIR-based application (for Cordova 3.x)
 * [mmir-starter-kit][10]: a small MMIR-based example application (for Cordova 3.x)

## Introduction

The MMIR (Mobile Multimodal Interaction and Rendering) framework aims to provide a lightweight multimodal dialog manager that -- for instance -- can run
on mobile devices. The base technology is HTML5 (JavaScript).

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

Installed Cordova 3.x environment (see [Cordova][0] documentation on CLI based development for more details).

In addition, the development tools for the targeted `platforms` need to be installed (see also the [Cordova][0] documentation).

##### Custom Cordova Plugins

If you plan to use the MMIR framework in combination with SCION (that is: make use of
the framework's ```DialogManager``` and/or ```InputManager```) within an environment that __does not__
support HTML5 ```WebWorkers```, you need the [Queue Plugin][6] for extending the framework's SCION  
integration with an event queue.

## Documentation

See the [wiki][8] for documentation.


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
