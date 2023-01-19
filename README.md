## 中文 | [English](https://github.com/lin-sh/Query-by-humming/blob/main/README-EN.md) 
# 简介
#### 本仓库提供了.dll(winodwss下)和.so(linux下)两个依赖文件，他们是基于https://github.com/YuzhongHuangCS/SDHumming 生成的，可直接调用(.dat和.info是模型数据)。
# 代码示例
#### python
```python
def qbh():
    dll = CDLL(r"./libguess_song.so")
    dll.guess.restype = POINTER(StructPointer)
    dat = ctypes.c_char_p(b'QBHModel.dat')//文件位置
    info = ctypes.c_char_p(b'QBHModel.info')//文件位置
    wav = ctypes.c_char_p(b'1.wav')//音频文件位置
    a = dll.guess(dat, info, wav)
	i = 0
	while i < 15:
		print(a[i].name.decode(encoding='GBK'), a[i].score)//识别出的歌名和其准确率
		i += 1
```
