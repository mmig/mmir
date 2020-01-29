[mmir][11]
====

[![MIT license](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![API](https://img.shields.io/badge/docs-API%20reference-orange.svg?style=flat)](https://mmig.github.io/mmir/api)
[![Guides](https://img.shields.io/badge/docs-guides-orange.svg?style=flat)](https://github.com/mmig/mmir/wiki)

<p align="center">
<img width="10%" src="https://raw.githubusercontent.com/wiki/mmig/mmir/images/logo.png">
</p>

Overview for the _open source_ `mmir` (Mobile Multimodal Interaction and Relay) Framework*.


##### Related repositories

- core:
  * [mmir-lib][4] [![npm](https://img.shields.io/npm/v/mmir-lib)](https://www.npmjs.com/package/mmir-lib): the core library _(this is usually included in the directory `mmirf/` of MMIR-based applications)_
  * [mmir-tooling][5] [![npm](https://img.shields.io/npm/v/mmir-tooling)](https://www.npmjs.com/package/mmir-tooling): scripts and resources for building and generating resources _(e.g. compiling JSON grammars)_
  * [mmir-webpack][25] [![npm](https://img.shields.io/npm/v/mmir-webpack)](https://www.npmjs.com/package/mmir-webpack): extended tooling for integrating `mmir-lib` in [webpack][26]-based apps
- plugins (e.g. for different speech recognition/synthesis engines):
  * [mmir-plugins-*][20]: multiple speech input (ASR) and speech oupt (TTS) plugins that use various web services
  * [mmir-plugin-speech-android][14]: a Cordova 5.x plugin that integrates Android's default speech recognizer and text-to-speech engines
  * [mmir-plugin-speech-nuance][15]: a Cordova 5.x plugin that integrates the Nuance SpeechKit (Dragon Mobile SDK) for speech recognition and text-to-speech
  * see also [module overview][16] in the wiki
- tools:
  * [scion-queue-plugin][6]: a Cordova 5.x plugin for `android` platform that provides an event-queue for SCION (used by the dialog manager)
- examples:
  * [mmir-cordova][9]: resources / example for creating a minimal MMIR-based application _(for Cordova 5.x)_
  * [mmir-starter-kit][10]: a small MMIR-based example application _(for Cordova 5.x)_

## Documentation

See the **[wiki][8]** for the main documentation.


See [API][12] documentation for information about the `mmir-lib` interface (or the even more detailed API doc with [private-visibility][13]).


See the README in [mmir-cordova][9] for step-by-step instruction on how to (1) create a new Cordova project and (2) add the MMIR framework.


Older Documenation:
 * [API mmir-lib v5.x][27] (and [private-visibility][28])
 * [API mmir-lib v4.x][23] (and [private-visibility][24])
 * [API mmir-lib v3.x][17] (and [private-visibility][18])


## Introduction

The MMIR (Mobile Multimodal Interaction and Relay) framework* aims to provide a
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
(see [Cordova][21] documentation on CLI based development for more details).

In addition, the development tools for the targeted `platforms` need to be installed (see also the [Cordova][21] documentation).

##### Custom Cordova Plugins

If you plan to use the MMIR framework in combination with SCION (that is: make use of
the framework's `DialogManager` and/or `InputManager`) within an environment that __does not__
support HTML5 `WebWorkers`, you need the [Queue Plugin][6] for extending the framework's SCION  
integration with an event queue.

----
_*:_ _previously " Mobile Multimodal Interaction and **Rendering** "_, this has been changed
      since version 6 of the framework, to account for the changed focus in that regard,
      namely that (graphical) _rendering_ is not a major focus of the framework anymore,
      but only considered an optional/add-on feature.


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
[20]: https://github.com/mmig?q=mmir-plugin-
[21]: https://cordova.apache.org/docs/
[22]: https://github.com/mmig/mmir-starter-kit/tree/ionic-gui
[23]: https://mmig.github.io/mmir/api-v4
[24]: https://mmig.github.io/mmir/api-all-v4
[25]: https://github.com/mmig/mmir-webpack
[26]: https://webpack.js.org/
[27]: https://mmig.github.io/mmir/api-v5
[28]: https://mmig.github.io/mmir/api-all-v5
