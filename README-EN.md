## English | [中文](https://github.com/lin-sh/Query-by-humming/blob/main/README.md)
# Introduction
#### This repository provides two dependency files .dll (under winodwss) and .so (under linux). They are generated based on https://github.com/YuzhongHuangCS/SDHumming and can be called directly (.dat and .info are model data).
# Code example
#### python
```python
def qbh():
    dll = CDLL(r"./libguess_song.so")
    dll.guess.restype = POINTER(StructPointer)
    dat = ctypes.c_char_p(b'QBHModel.dat')//File Location
    info = ctypes.c_char_p(b'QBHModel.info')//File Location
    wav = ctypes.c_char_p(b'1.wav')//Pending audio file location
    a = dll.guess(dat, info, wav)
	i = 0
	while i < 15:
		print(a[i].name.decode(encoding='GBK'), a[i].score)//Recognized song titles and their accuracy rate
		i += 1
```
