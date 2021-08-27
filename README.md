# multi-media-FaceRecognition

# 根据声音或者视频，给出镜头切换点。并标注出讲话人的声音。并给出画面中嘉宾的人的名字，按时间段给出时间起点和终点，画面中只要嘉宾变了，就作为一个新段。

## 一开始拿到这个题目是有点懵的，因为我们组里都是信安，并没有学习过机器学习类似的课程，但是这道题目是一定要用到机器学习。再加上这道题老师并没有给出参考代码，所以可以说是完全是“从头开始”。不过功夫不负有心人并且老师给了我们最后一个选题充裕的时间，所以我们才可以将其做出来。

## 1.1 切换点

而根据问题的描述：根据声音或者视频，给出镜头的切换点，按照时间段给出时间起点和终点。
我们所理解的切换点为两种：镜头切换点和音频切换点。
### 1.1.1 镜头切换点
对于镜头切换点：对于这个视频来说，可以很明显的看到这个视频的拍摄并不是一个机位拍摄的，而是多机位进行拍摄。每个机位对着一个嘉宾或者主持人。如下图所示：
 
所以我们想到如果说我们可以找到这个视频的镜头切换点或者说剪辑点，对于一个视频而言后期剪辑会将不同机位拍摄的视频剪辑在一起，而这个剪辑点是很好找的，所以只要找到这视频的剪辑点就相当于找到了这个视频的镜头切换点，就可以将一段视频分段，分成一段只有一个主持人的样子，并且将每一段所对应的时间记录下来生成一个列表，这样就可以达到选题给出的要求。
至于如何找这个剪辑点在之后的第三段：分帧中会提到，这里就不赘述了。
### 1.1.2 音频切换点。
对比寻找视频切换点，音频切换点就显得不是友好了。
 
对于这个切换点我们给出了两种方案：
<br> 1：设定相应的步长，分块进行声纹识别，得出说话人队列。</br>
<br> 2：说话人日志（Speaker Diarization）：基于深度学习的说话人日志，通过深度学习的方法，从训练数据中学习语音和说话人的特征，从而实现说话人“谁在什么时候说话”的目标。</br>

## 2.2 嘉宾识别 = 人脸识别 & 声纹识别
### 2.2.1 人脸识别
对于人脸识别这方面，现在技术上已经做的很发达了。比如说图书馆和宿舍用的人脸识别系统：可以说秒识别了。而且识别准确率特别高。
	我们在这里先假设我们的人脸识别准确率可以达到90%以上，实际上我们也达到了90%以上。但是在这里我们假设人脸识别是成功的，是可移植的。如果说分帧做好了的话，对于人脸识别的话我们就可以在一段视频中取多帧图片，对其进行人脸识别，然后取匹配结果中的最匹配的那一项作为结果，成为那个片段的标签用来标记这个片段中是哪个嘉宾。
	这样我们就可以将嘉宾识别出来。
	具体的人脸识别是怎么样实现的之后会有详细的介绍。
	
	
### 2.2.2 声纹识别
	对于声纹识别这方面，通过对市面上的调研，声纹识别的应用场景并没有人脸识别广泛。所以对于声纹识别这方面的实现来说，并不是一件简单的事情。
	所以对于声纹识别这个部分，我们也像人脸识别一样假设，我们实现的声纹识别准确率可以达到90%以上，（实际上可能最高只有80%）。
	通过上面介绍的两种找音频切换点的方案：这样也可以像人脸识别一样得到一项列表，也可以将嘉宾实现出来。
	具体的声纹识别是怎么样实现的在之后会有所涉及。


# 三：实验环境
<br> 操作系统：Windows 10 pro</br>

<br> 编译环境: Python 3.7.4 + Pychram 2019.3 + Jupyter Notebook</br>

<br> 视频播放器：potplayer Mini<br>
