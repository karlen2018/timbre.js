SoundBuffer
=========
SoundBuffer

`T("buffer")` や `T("tape")` では `SoundBuffer` 形式のデータを扱います。

以下はサンプルレート 44.1KHz の 1秒間のデータを表わします。

```js
var soundbuffer = {
    buffer    : new Float32Array(44100),
    samplerate: 44100
};
```

(canvas buffer w:240 h:80)

以下の例は独自に生成したサウンドバッファーを `T("buffer")` にセットして再生しています。

```timbre
var canvas = window.getCanvasById("buffer");

var len    = 44100;
var buffer = new Float32Array(len);

for (var i = 0; i < buffer.length; i++) {
    buffer[i] = Math.sin(Math.PI * 0.001 * i) * (i/len) * (1-(i/len)) * 2;
}

buffer = { buffer:buffer, samplerate:22050 };

T("buffer", {buffer:buffer, pitch:50, isLooped:true}).plot({target:canvas}).play();
```