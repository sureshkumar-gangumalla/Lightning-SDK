# Web Audio

The Web Audio plugin provides a powerful and versatile system for controlling audio on the Web, allowing developers to choose audio sources, add effects to audio, apply spatial effects (such as panning) and much more.

## Example app

We've provided an example App that showcases all the features of the Web Audio: https://github.com/mlapps/com.metrological.app.WebAudioTester.

## Usage

In order to power your App with Web Audio capabilities you first need to import this plugin from the Lightning-SDK

```js
import { WebAudio } from '@lightningjs/sdk'

```

## Methods

The Web Audio exposes methods that you can use in your app:

### initWebAudio

Override the AudioContext constructor with platform provided AudioContext

The `initWebAudio` accept config object

```js
const config = {
    AudioContext: platformAudioContext
}

WebAudio.initWebAudio(config)
```

### Load

load the configured audio buffers into the application and override default window AudioContext with given context

The `load` method accept an config object.
Object should have `sounds` property with array of objects as value.
Each object key act as `identifier` of `audio` and value is audio source URL


```js
const audios = [
    {speech: 'https://webaudioapi.com/samples/room-effects/sounds/speech.mp3'},
    {chrono_sound: 'https://webaudioapi.com/samples/script-processor/chrono.mp3'}
]

WebAudio.load(config)
```
### getBuffers

Return beffers of loaded audios

```js
WebAudio.getBuffers()
```

### isReady

Return status of completion of audio context instance creation

### loadEffects

load the effects into application.

The `loadEffects` method accept an array of objects. Each object key act as identifier of the effect and value represents the audio source url

```js
const effects = [
    {telephone: 'https://webaudioapi.com/samples/room-effects//sounds/impulse-response/telephone.wav' },
    {muffler: 'https://webaudioapi.com/samples/room-effects//sounds/impulse-response/muffler.wav' },
]

WebAudio.load(effects)
```

### getAudio

Return the `WebAudio` instance of given identifier

The `getAudio` method accept an identifier
to find out the audio

```js
WebAudio.getAudio('speech')
```

### play

Play all the loaded audios with given settings

The `play` method accept the two arguments
(`settings` and `identifiers`). Both the parameters are optional.

`settings` is an object where key represents the setting name and value represents its value and these settings are applied of each audios

`identifiers` is an array of `identifier`.
`play` method plays only audios of given identifiers if this argument if fulfilled or else play all the audios

```js
const settings = {
    volume: 1,
    skip: 0.5,
    delay: 1
}

WebAudio.play(settings)

/*
  const identifiers = ['speech']

  WebAudio.play(settings, identifiers)
 */
```

### stop

Stop the all audios

```js
WebAudio.stop()
```

### pause

Pause the all running audios

```js
WebAudio.pause()
```

### resume

Resume the all paused audios

```js
WebAudio.resume()
```

### remove

Remove the loaded audios

The `remove` method accept `identifiers` as argument. This is options argument if provided remove only given audios or else all the audios

```js
WebAudio.remove() // remove all the audios

/*
 WebAudio.remove(['speech']) remove only speech audio
*/
```

### removeEffects

Remove the audio effects

The `removeEffects` method accept `identifiers` as argument. This is options argument if provided remove only given effects or else all the effects

```js
WebAudio.removeEffects() // remove all the effects

/*
 WebAudio.removeEffects(['telephone']) remove only telephone effect
*/



### getListener










