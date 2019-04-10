[mmir][11]
====

<p align="center">
<img width="10%" src="https://raw.githubusercontent.com/wiki/mmig/mmir/images/logo.png">
</p>

Overview for the MMIR (Mobile Multimodal Interaction and Rendering) Framework. 


##### Related repositories

- core:
  * [mmir-lib][4]: the core library _(this is usually included in the directory `mmirf/` of MMIR-based applications)_
  * [mmir-tooling][5]: scripts and resources for building and generating resources _(e.g. compiling JSON grammars)_
- tools:
  * [scion-queue-plugin][6]: a Cordova 5.x plugin that provides an event-queue for SCION (used by the dialog manager)
- speech modules:
  * [mmir-plugin-speech-android][14]: a Cordova 5.x plugin that integrates Android's default speech recognizer and text-to-speech engines
  * [mmir-plugin-speech-nuance][15]: a Cordova 5.x plugin that integrates the Nuance SpeechKit (Dragon Mobile SDK) for speech recognition and text-to-speech
  * [mmir-plugins-media][20]: multiple speech input (ASR) and speech oupt (TTS) plugins that use various web services
  * see also [module overview][16] in the wiki
- examples:
  * [mmir-cordova][9]: resources / example for creating a minimal MMIR-based application _(for Cordova 5.x)_
  * [mmir-starter-kit][10]: a small MMIR-based example application _(for Cordova 5.x)_

## Documentation

See the **[wiki][8]** for the main documentation.


See [API][12] documentation for information about the `mmir-lib` interface (or the even more detailed API doc with [private-visibility][13]).


See the README in [mmir-cordova][9] for step-by-step instruction on how to (1) create a new Cordova project and (2) add the MMIR framework.


Older Documenation:
 * [API mmir-lib v3.x][17] (and [private-visibility][18])


## Introduction

The MMIR (Mobile Multimodal Interaction and Rendering) framework aims to provide a 
lightweight multimodal dialog manager that -- for instance -- can run on mobile devices. 
The base technology is HTML5 (JavaScript).

A core concept for the framework is the MVC (Model View Controller) pattern.
While the framework provides a template mechanism similar to JSP (Java Server Pages),
ASP (Active Server Pages), the MMIR framework can also be combined/used with other GUI
frameworks, e.g. see [Ionic/Angluar starter-kit example][22].

The state of the dialog system can be tracked and manipulated based on a finite-state machine (FSM).
The framework uses SCXML (State Chart XML) via [SCION][1]: SCION is a JavaScript-based interpreter for SCXML files.

The framework core and its extensions are implemented as AMD (Asynchronous Module Definition) using [RequireJS][3].

The MMIR library provides basic capabilities for recognizing speech input
(ASR, e.g. using Google Speech Recognition service), and speech output (TTS, e.g. using [MARY][2]).  
For more details of available MMIR Speech Plugins, see the overview on the [speech processing wiki page][19].

NOTE: Requirements for browser-based speech plugins
 * web-service-based ASR plugins
	* microphone access: plugins require access to the microphone resource for speech input, i.e. [getUserMedia API](https://caniuse.com/#feat=stream)
	* silence detection: plugins require support of the [AudioContext API](https://caniuse.com/#feat=audio-api), for the implementation of the end-of-speech detection (aka silence detection)
 * _Web Speech_-based ASR plugins: plugins that use [Web Speech][7] for speech recognition, require support of the [Web Speech API](https://caniuse.com/#feat=speech-recognition)
 * web-service-base TTS plugins:
    * playback of speech synthesis: plugins require support of the [Audio Object API](https://caniuse.com/#feat=audio)


## Prerequisites

For target platforms `Android` and `iOS`, Cordova 5.x or later is required
(see [Cordova][20] documentation on CLI based development for more details).

In addition, the development tools for the targeted `platforms` need to be installed (see also the [Cordova][20] documentation).

##### Custom Cordova Plugins

If you plan to use the MMIR framework in combination with SCION (that is: make use of
the framework's `DialogManager` and/or `InputManager`) within an environment that __does not__
support HTML5 `WebWorkers`, you need the [Queue Plugin][6] for extending the framework's SCION  
integration with an event queue.



[0]: https://cordova.apache.org/
[1]: https://gitlab.com/scion-scxml/scion
[2]: http://mary.dfki.de/
[3]: https://requirejs.org/
[4]: https://github.com/mmig/mmir-lib
[5]: https://github.com/mmig/mmir-tooling
[6]: https://github.com/mmig/mmir-plugin-scionqueue
[7]: https://w3c.github.io/speech-api/
[8]: https://github.com/mmig/mmir/wiki
[9]: https://github.com/mmig/mmir-cordova
[10]: https://github.com/mmig/mmir-starter-kit
[11]: https://github.com/mmig/mmir
[12]: https://mmig.github.io/mmir/api
[13]: https://mmig.github.io/mmir/api-all
[14]: https://github.com/mmig/mmir-plugin-speech-android
[15]: https://github.com/mmig/mmir-plugin-speech-nunace
[16]: https://github.com/mmig/mmir/wiki/3.9.2-Speech-Processing-in-MMIR#speech-modules
[17]: https://mmig.github.io/mmir/api-v3
[18]: https://mmig.github.io/mmir/api-all-v3
[19]: https://github.com/mmig/mmir/wiki/3.9.2-Speech-Processing-in-MMIR
[20]: https://github.com/mmig/mmir-plugins-media
[21]: https://cordova.apache.org/docs/
[22]: https://github.com/mmig/mmir-starter-kit/tree/ionic-gui
