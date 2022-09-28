---
title:  "mbedtls与bouncyCastle对接ECDH秘钥协商"
date:   2022-9-28 21:57:00 +0800
---
本文旨在记录两个开源库之间对接时出现的一些问题
# 1.字节序

bouncyCastle的字节序输出都是小端序，需要转换成大端序放入负载报文中，同样的，对于收到的对端公钥也需要转换一次才能正确加载。

# 2.压缩点问题

[github上的issue](https://github.com/bcgit/bc-java/issues/251)

参照上面这个issue可知，bouncyCastle使用的点压缩方式与mbedtls不同，需要进行转换