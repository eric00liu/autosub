# Autosub <a href="https://pypi.python.org/pypi/autosub"><img src="https://img.shields.io/pypi/v/autosub.svg"></img></a>
autosub 是一个可以为视频生成字幕的命令行工具，支持windows, Mac, Linux系统。

本repo fork自: https://github.com/agermanidis/autosub   
主要修改了语音识别部分，将其中的Google API替换为Baidu API，方便国内用户使用     
使用时，请将源语言和目标语言都设置为中文，例如：
```
autosub 1.mp4  -S zh-CN -D zh-CN -C 10 -o 1.srt
```

### 安装
1. 开通自己的百度开发者账号，打开语音识别API服务，创建自己的apikey和skey https://cloud.baidu.com/doc/SPEECH/index.html  
2. 如果不方便注册百度开发者账号，可以联系我获取一个临时的token，有效期为24小时。
![](profile.jpg)
3. 打开编辑 autosub/constants.py    

```           
- 填入百度开发者的 BAIDU_APIKEY和BAIDU_SKEY。              
- 将临时token填入到BAIDU_TOKEN          
以上二者有其一即可。
```          

4. Install ffmpeg
5. python setup.py install
6. 执行语音转文字
```
autosub 1.mp4  -S zh-CN -D zh-CN -C 10 -o 1.srt
```
  
  
### Auto-generated subtitles for any video

Autosub is a utility for automatic speech recognition and subtitle generation. It takes a video or an audio file as input, performs voice activity detection to find speech regions, makes parallel requests to Google Web Speech API to generate transcriptions for those regions, (optionally) translates them to a different language, and finally saves the resulting subtitles to disk. It supports a variety of input and output languages (to see which, run the utility with the argument `--list-languages`) and can currently produce subtitles in either the [SRT format](https://en.wikipedia.org/wiki/SubRip) or simple [JSON](https://en.wikipedia.org/wiki/JSON).

### Installation

1. Install [ffmpeg](https://www.ffmpeg.org/).
2. Run `pip install autosub`.

### Usage

```
$ autosub -h
usage: autosub [-h] [-C CONCURRENCY] [-o OUTPUT] [-F FORMAT] [-S SRC_LANGUAGE]
               [-D DST_LANGUAGE] [-K API_KEY] [--list-formats]
               [--list-languages]
               [source_path]

positional arguments:
  source_path           Path to the video or audio file to subtitle

optional arguments:
  -h, --help            show this help message and exit
  -C CONCURRENCY, --concurrency CONCURRENCY
                        Number of concurrent API requests to make
  -o OUTPUT, --output OUTPUT
                        Output path for subtitles (by default, subtitles are
                        saved in the same directory and name as the source
                        path)
  -F FORMAT, --format FORMAT
                        Destination subtitle format
  -S SRC_LANGUAGE, --src-language SRC_LANGUAGE
                        Language spoken in source file
  -D DST_LANGUAGE, --dst-language DST_LANGUAGE
                        Desired language for the subtitles
  -K API_KEY, --api-key API_KEY
                        The Google Translate API key to be used. (Required for
                        subtitle translation)
  --list-formats        List all available subtitle formats
  --list-languages      List all available source/destination languages
```

### License

MIT
