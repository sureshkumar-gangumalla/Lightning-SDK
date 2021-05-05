# Single Audio

The `Web Audio` provides a provision to apply effects and controls on each individual audio

The `getAudio` method returns the WebAudio instance of specified audio

```js
const speechAudio = WebAudio.getAudio('speech')
```

##Methods
The Web Audio exposes methods that you can use on single audio:

### volume

```js
WebAudio.getAudio('speech').volume(0.5)
```

### skip

```js
WebAudio.getAudio('speech').skip(5)
```

### delay

```js
WebAudio.getAudio('speech').delay(5)
```

###loop

```js
WebAudio.getAudio('speech').loop()
```

### play

```js
WebAudio.getAudio('speech').play()
```

### pause

```js
WebAudio.getAudio('speech').pause()
```

### resume

```js
WebAudio.getAudio('speech').resume()
```

### stop

```js
WebAudio.getAudio('speech').stop()
```

### reset

```js
WebAudio.getAudio('speech').reset()
```

### effect

```js
WebAudio.getAudio('speech').effet('muffler')
```

### compress
```js
WebAudio.getAudio('speech').compress(compressorParams)
```

### filter

```js
WebAudio.getAudio('speech').filter(filterParams)
```

### IIRFilter

```js
WebAudio.getAudio('speech').IIRFilter(feedForward, feedBack)
```

### distortion

```js
WebAudio.getAudio('speech').distortion(0.5, '2x')
```

### panner

```js
WebAudio.getAudio('speech').panner(pannerParams)
```

### stereoPanner

```js
WebAudio.getAudio('speech').stereoPanner(1)
```



