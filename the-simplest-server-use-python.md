# Pi上最简单HTTP服务器

一句话就可以搭建一个HTTP服务器，并且能在浏览器中访问？
听起来怎么不太可能？不过，Python确实给我们这种能力。


```bash
$ python -m SimpleHTTPServer
Serving HTTP on 0.0.0.0 port 8000 ...
```

之后便可以打开本地的浏览，其中输入`http://localhost:8000`或者`http://0.0.0.0:8000`就可以打开改服务器，界面显示的是执行该命令时，所在文件夹的文件目录。

是不是很惊讶？不过这有什么用呢？如果打开想打开文件没有目录，直接用`ls`命令查看，或者直接打开文件管理器不就可以了吗？

当当当～当～！ 还真有点用处。

比如，你用SSH远程连接Raspbery Pi，想在主机上下载Pi上的文件，就可以在SSH中使用上述命令，之后，在主机上打开浏览器，输入`http://pi-IP-address:8000`，如果在一个局域网中，还可以输入`http://pi-hostname:8000`打开该命令所在的文件目录，之后就可以浏览，并且下载你需要的文件。

相比`scp`或者`nc`这种方式简单直接，方便查看文件。也算是一种用处吧。另外，如果你的Raspberry Pi有公网IP，其他人就可以通过该IP，访问你提供的内容。这样就可以做一个简单的文件服务器。