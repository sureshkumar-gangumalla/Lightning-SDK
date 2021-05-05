# Single Audio

The `Web Audio` provides a provision to apply effects and controls on each individual audio

The `getAudio` method returns the WebAudio instance of specified audio

```js
const speechAudio = WebAudio.getAudio('speech')
```
## Controls Methods

### play

Plays the audio

```js
WebAudio.getAudio('speech').play()
```

### pause

Pauses the playing audio

```js
WebAudio.getAudio('speech').pause()
```

### resume

Resumes the paused audio

```js
WebAudio.getAudio('speech').resume()
```

### stop

Stops the current playing audio

```js
WebAudio.getAudio('speech').stop()
```

##  Effects Methods

### volume

Set the volume of audio

The `volume` method accept 1 argument (`volume`) and the value should be in range [0 1].


```js
WebAudio.getAudio('speech').volume(0.5)
```

### skip

Skips a specified number of seconds from start of audio

The `skip` method accepts the number of seconds to jump as single argument
```js
WebAudio.getAudio('speech').skip(5)
```

### delay

Set the delay on audio. audio starts playing after delay time

The `delay` method accepts the number of seconds of delay as single argument

```js
WebAudio.getAudio('speech').delay(5)
```

###loop

Set the audio in loop mode.

The `loop` method accepts the boolean value `true` or `false`

```js
WebAudio.getAudio('speech').loop()
```

### reset

Reset to initial state by dropping all the
settings and effects

```js
WebAudio.getAudio('speech').reset()
```

### effect

Apply the effect on audio

The `effect` method accepts the identifier of effect as single argument and that should be the valid and already loaded before

```js
WebAudio.getAudio('speech').effet('muffler')
```

### compress

Compression effect lowers the volume of loudest parts of singal.

The `compress` method accepts the `CompressorParams` object as single argument.

The `CompressorParams` instance can be created by `new WebAudio.CompressorParams()`
You can find more about properties of compressor at [ Compressor](https://developer.mozilla.org/en-US/docs/Web/API/DynamicsCompressorNode#properties)

```js
const compParams = new WebAudio.CompressorParams()

compParams.threshold = -50
compParams.knee = 20
compParams.ratio = 6
compParams.attack = 1
compParams.release = 1

WebAudio.getAudio('speech').compress(compParams)
```

### filter

A low-order filter on audio which uses
filter algorithms based on type of filter

The `filter` method accepts the `FilterParams` object as single argument.

The `FilterParams` instance can be created by `new WebAudio.FilterParams()`

You can find more about properties of compressor at [Filter](https://developer.mozilla.org/en-US/docs/Web/API/BiquadFilterNode#properties)

```js
// create instance of FilterParams
const filterParams  = new WebAudio.FilterParams()

// FilterParams properties
filterParams1.frequency = 100
filterParams1.detune = 10
filterParams1.Q = 10
filterParams1.gain = 10
filterParams.type = WebAudio.FilterParams.TYPE.HIGHPASS

WebAudio.getAudio('speech').filter(filterParams)
```

### IIRFilter

An infinite impulse response filter, the filter response parameters can be specified, so that it can be tuned as needed.

The `IIRFilter` method accepts 2 arguments (`feedForward`, `feedBack`). Both of these parameters are arrays, neither of which can be larger than 20 items.

```js

const feedForward = [0.00020298, 0.0004059599, 0.00020298]

const feedBack = [1.0126964558, -1.9991880801, 0.9873035442];

WebAudio.getAudio('speech').IIRFilter(feedForward, feedBack)
```

### distortion

Represents a non-linear distorter. It uses a curve to apply a wave shaping distortion to the signal

The `distortion` method accepts 2 arguments (`amount`, `oversample`). The `amount` should be in range [0, 1]
and `oversample` could be one of the following
`2x`, `4x` and `none`.
The default `oversample` is set to `none`

the `distortion` curve is formed based on code at [Distortion curve](https://stackoverflow.com/a/22313408)

```js
WebAudio.getAudio('speech').distortion(0.5, '2x')
```

### panner

Represents the position and behavior of an audio source signal in 3D space, allowing you to create complex panning effects.

The `filter` method accepts the `PannerParams` object as single argument.

The `PannerParams` instance can be created by `new WebAudio.PannerParams()`

You can find more about properties of panner at [Panner](https://developer.mozilla.org/en-US/docs/Web/API/PannerNode#properties)

```js

const pannerParams = new WebAudio.PannerParams()

pannerParams.positionX = 0
pannerParams.positionY = 0
pannerParams.positionZ = 1
pannerParams.coneInnerAngle = 480
pannerParams.coneOuterAngle = -10
pannerParams.coneOuterGain = 0
pannerParams.distanceModel = 'linear'
pannerParams.maxDistance = 9
pannerParams.orientationX = 0
pannerParams.orientationY = 0
pannerParams.orientationZ = 1
pannerParams.panningModel = 'HRTF'
pannerParams.refDistance = 1
pannerParams.rolloffFactor = 1.1

WebAudio.getAudio('speech').panner(pannerParams)
```

### getPanner

Return the `PannerNodeWrapper` instance which enable provision to directly update the properties on created panner node.

```js
WebAudio.getAudio('speech').getPanner()
```

### stereoPanner

This can be used to pan an audio stream  left or right.

The `stereoPanner` method accepts the `pan` value between
`-1` (full left pan) and `1` (full right pan).

```js
WebAudio.getAudio('speech').stereoPanner(1)
```


## Method Chaining

All the effects methods on `WebAudio` (`WebAudio.getAudio('speech')`) are chainable methods

```js

// Chainable methods
WebAudio.getAudio('speech').volume(1).skip(5).delay(5).loop().effect('muffler')

```



