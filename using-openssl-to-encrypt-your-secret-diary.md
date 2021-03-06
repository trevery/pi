# 使用openssl加密你的私密日记

每个人都有自己的秘密。甜蜜的，不幸的。那些不想让人知道秘密，最好保存在心里。不告诉任何人。如果非要记录下来，那就想办法给它上把锁，只有自己有钥匙打开。

## 加密解密你的日记

假如你的一篇日记为 my-secret-diary.md。为了防止别人阅读，你可以使用openssl工具来进行加密。

```bash
$ openssl enc -e -aes-256-cbc -a -in my-secret-diary.md -out my-secret-diary.cry
```
解释：

- enc: 告诉openssl 这里使用 encrypt（加密）命令。
- -e: 表示 encrypt 加密，与 -d 命令表示的 decrypt相反。
- -aes-256-cbc: 使用aes-256-cbc算法，准确的说使用AES算法，256位加密类型。CBC为
- -a: 使用 base64 编码，可以要。如果这里添加，解密的时候也要添加。
- -in: 后面跟输入的文件
- -out: 后面跟输出的文件。文件名可以自行修改，建议里面不要包含敏感信息，如该例中国年的'secret-diary'。当然，目前想要破解AES-256位加密几乎不可能。但是说不准你的日记要保存100年，那个时候的计算能力可能解密AES-256算法已经非常轻松啦

输入命令后，会提示你输入密码，你可以输入一个只有你知道的‘钥匙’。linux下输入passwd都是不显示的，所以不要以为没有输入进去。

如果没有提示输入密码，可能命令的参数输入错了。由于非常长，所以输入错误很容易出现。建议你自己对比一下。

这个时候可以使用 ls 命令查看以下加密之后的文件。不出意外，应该包含 my-secret-diary.md 和 my-secret-diary.cry 两个文件。 你可以立刻使用 rm 命令删除 my-secret-diary.md 以防止别人查看你的私密文件。当然你一可以先解密以下 my-secret-diary.cry 文件，防止加密时记错了密码，以防你的加密文件连自己也查看不了。如何解密呢？

```bash
$ openssl enc -d -aes-256-cbc -a -in my-secret-diary.cry
```
之后会提示你输入密码，如果不出意外，当你输入正确的密码后就可以查看到自己的秘密日记了。

哦，对了，忘了告诉你，如果你使用cat命令查看自己的加密文档，会发现是一堆乱七八糟的东西。另外，如果你输入的密码错误，同样会返回乱码。可见，只有正确的密码作为key，才能正确解开加密文档。

如果一切都正确，可以通过 my-secret-diary.cry 获得正确的 my-secret-diary.md文件内容，那么你就可以放心的使用 rm 命令删除明文文件啦。

```bash
rm my-secret-diary.md
```

## 备份到Github

如果你以下条件：

- 希望利用Github托管自己的日记，以便备份，防止本地不小心删除。
- 只有使用Gihub public repository 的权限（一般免费用户可以使用的功能）
- 希望别人无法阅读自己的秘密

那你不妨将上述使用openssl加密日记的方法结合Github的使用，就可以既享受免费托管自己的私密日记，又不会被别人查看到自己的秘密啦。
