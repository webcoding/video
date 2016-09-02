# js_video
学习 video 相关知识

参考：

- [移动端HTML5<video>视频播放优化实践](http://www.xuanfengge.com/html5-video-play.html)
- [HTML5 Video Events and API检测工具](http://www.w3.org/2010/05/video/mediaevents.html)
- [W3C video 标准](http://www.w3.org/TR/html5/embedded-content-0.html#the-video-element)
- [如何在iOS7+的webview中内联播放视频](http://darktalker.com/2014/play-video-inline-iphone-ios7)
- [视频事件流水查看工具](http://z.weishi.qq.com/app/video.html)
- [Audio_and_video_delivery/buffering_seeking_time_ranges](https://developer.mozilla.org/en-US/Apps/Fundamentals/Audio_and_video_delivery/buffering_seeking_time_ranges)
- [HTML5 Video Events and API](https://www.w3.org/2010/05/video/mediaevents.html)
- [HTML 五 Video概述](http://www.educity.cn/wenda/8156.html)
- [ html5的video各种属性及api](http://blog.csdn.net/cdnight/article/details/39323697)


```
Media方法和属性：
HTMLVideoElement 和HTMLAudioElement 均继承自HTMLMediaElement

//错误状态
Media.error; //null:正常
Media.error.code; //1.用户终止 2.网络错误 3.解码错误 4.URL无效

//网络状态
Media.currentSrc; //返回当前资源的URL
Media.src = value; //返回或设置当前资源的URL
Media.canPlayType(type); //是否能播放某种格式的资源
Media.networkState; //0.此元素未初始化  1.正常但没有使用网络  2.正在下载数据  3.没有找到资源
Media.load(); //重新加载src指定的资源
Media.buffered; //返回已缓冲区域，TimeRanges
Media.preload; //none:不预载 metadata:预载资源信息 auto:

//准备状态
Media.readyState;    //1:HAVE_NOTHING 2:HAVE_METADATA 3.HAVE_CURRENT_DATA 4.HAVE_FUTURE_DATA 5.HAVE_ENOUGH_DATA
Media.seeking; //是否正在seeking

//回放状态
Media.currentTime = value; //当前播放的位置，赋值可改变位置
Media.startTime; //一般为0，如果为流媒体或者不从0开始的资源，则不为0
Media.duration; //当前资源长度 流返回无限
Media.paused; //是否暂停
Media.defaultPlaybackRate = value;//默认的回放速度，可以设置
Media.playbackRate = value;//当前播放速度，设置后马上改变
Media.played; //返回已经播放的区域，TimeRanges，关于此对象见下文
Media.seekable; //返回可以seek的区域 TimeRanges
Media.ended; //是否结束
Media.autoPlay;  //是否自动播放
Media.loop;  //是否循环播放
Media.play();    //播放
Media.pause();   //暂停

Media.controls;//是否有默认控制条
Media.volume = value; //音量
Media.muted = value; //静音

//TimeRanges(区域)对象
TimeRanges.length; //区域段数
TimeRanges.start(index) //第index段区域的开始位置
TimeRanges.end(index) //第index段区域的结束位置


事件：Js代码
var eventTester = function(e){
 Media.addEventListener(e,function(){
     console.log((new Date()).getTime(),e);
 });
}
eventTester("loadstart");   //客户端开始请求数据
eventTester("progress");    //客户端正在请求数据
eventTester("suspend");     //延迟下载
eventTester("abort");       //客户端主动终止下载（不是因为错误引起），
eventTester("error");       //请求数据时遇到错误
eventTester("stalled");     //网速失速
eventTester("play");        //play()和autoplay开始播放时触发
eventTester("pause");       //pause()触发
eventTester("loadedmetadata");  //成功获取资源长度
eventTester("loadeddata");  //
eventTester("waiting");     //等待数据，并非错误
eventTester("playing");     //开始回放
eventTester("canplay");     //可以播放，但中途可能因为加载而暂停
eventTester("canplaythrough"); //可以播放，歌曲全部加载完毕
eventTester("seeking");     //寻找中
eventTester("seeked");      //寻找完毕
eventTester("timeupdate");  //播放时间改变
eventTester("ended");       //播放结束
eventTester("ratechange");  //播放速率改变
eventTester("durationchange");  //资源长度改变
eventTester("volumechange");    //音量改变
```
