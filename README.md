## 基于AudioContext与Canvas制作的音乐播放器 ##

### [index.html](https://jhinsama.github.io/H5-Web-Audio-Player/)是1.0版本 ###
> 1.0版本使用了 FileReader 解析路径文件信息 使用 audioBufferSourceNode 播放音频

### [audio.html](https://jhinsama.github.io/H5-Web-Audio-Player/audio.html)是2.0版本 ###
> 2.0版本 主要体现了对 audio 标签的控制 及其 audio 对象的方法的调用

---

### audio tag ###
```javascript
// <audio id="my-audio"></audio>
var audio = document.getElementById("my-audio");

audio.onloadstart = function(){console.log("开始加载");};
audio.ondurationchange = function(){console.log("媒体时长改变");};
audio.onloadedmetadata = function(){console.log("元数据加载完成");};
audio.onloadeddata = function(){console.log("当前帧加载完成");};
audio.onprogress = function(){console.log("下载指定的数据");};
audio.oncanplay = function(){console.log("可以开始播放");};
audio.oncanplaythrough = function(){console.log("可以正常播放且无需停顿");};
audio.onended = function(){console.log("播放结束");};
audio.onerror = function(){console.log("数据加载出错");};
audio.onpause = function(){console.log("暂停中");};
audio.onplay = function(){console.log("准备开始播放");};
audio.onplaying = function(){console.log("播放中");};
audio.onratechange = function(){console.log("播放速度发生改变");};
audio.onseeked = function(){console.log("完成定位播放位置");};
audio.onseeking = function(){console.log("开始定位播放位置");};
audio.onvolumechange = function(){console.log("音量发生改变");};
audio.onwaiting = function(){console.log("播放下一帧需要缓冲");};
audio.onstalled = function(){console.log("获取到数据但数据不可用");};
audio.onsuspend = function(){console.log("读取数据中止");};
audio.onemptied = function(){console.log("复位到初始状态");};
audio.onencrypted = function(){console.log("遇到加密的数据");};

audio.audioTracks	// 返回表示可用音频轨道的 AudioTrackList 对象。
audio.autoplay		// 设置或返回是否在就绪（加载完成）后随即播放音频。
audio.buffered		// 返回表示音频已缓冲部分的 TimeRanges 对象。
audio.controller	// 返回表示音频当前媒体控制器的 MediaController 对象。
audio.controls		// 设置或返回音频是否应该显示控件（比如播放/暂停等）。
audio.crossOrigin	// 设置或返回音频的 CORS 设置。
audio.currentSrc	// 返回当前音频的 URL。
audio.currentTime	// 设置或返回音频中的当前播放位置（以秒计）。
audio.defaultMuted	// 设置或返回音频默认是否静音。
audio.defaultPlaybackRate	// 设置或返回音频的默认播放速度。
audio.duration		// 返回音频的长度（以秒计）。
audio.ended 		// 返回音频的播放是否已结束。
audio.error 		// 返回表示音频错误状态的 MediaError 对象。
audio.loop  		// 设置或返回音频是否应在结束时再次播放。
audio.mediaGroup	// 设置或返回音频所属媒介组合的名称。
audio.muted 		// 设置或返回是否关闭声音。
audio.networkState	// 返回音频的当前网络状态。
audio.paused		// 设置或返回音频是否暂停。
audio.playbackRate	// 设置或返回音频播放的速度。
audio.played		// 返回表示音频已播放部分的 TimeRanges 对象。
audio.preload		// 设置或返回音频的 preload 属性的值。
audio.readyState	// 返回音频当前的就绪状态。
audio.seekable		// 返回表示音频可寻址部分的 TimeRanges 对象。
audio.seeking		// 返回用户当前是否正在音频中进行查找。
audio.src   		// 设置或返回音频的 src 属性的值。
audio.textTracks	// 返回表示可用文本轨道的 TextTrackList 对象。
audio.volume		// 设置或返回音频的音量。

audio.addTextTrack()// 向音频添加新的文本轨道。
audio.canPlayType()	// 检查浏览器是否能够播放指定的音频类型。
audio.fastSeek()	// 在音频播放器中指定播放时间。
audio.getStartDate()// 返回新的 Date 对象，表示当前时间线偏移量。
audio.load()		// 重新加载音频元素。
audio.play()		// 开始播放音频。
audio.pause()		// 暂停当前播放的音频。
```

---

### AudioContext API ###
```javascript
var audioContext = new AudioContext();
var analyser = audioContext.createAnalyser();
var gain = audioContext.createGain();
var sources = audioContext.createMediaElementSource(/*audio tag*/);
var audioBufferSourceNode = audioContext.createBufferSource();
```