# 重新設定 git 與 ssh

過往對他們一知半解，現在重新設定。

```bash
ssh-keygen -t ed25519 -C david0601d@gmail.com # `-t` 指定加密演算法， `-C` 為標籤，當想要區分金鑰用途時，例如工作用、學校用，就可加上 email 標籤進行區分。
```
```
Generating public/private ed25519 key pair.
Enter file in which to save the key (/Users/dah/.ssh/id_ed25519):
Enter passphrase for "/Users/dah/.ssh/id_ed25519" (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/dah/.ssh/id_ed25519
Your public key has been saved in /Users/dah/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:ewBOKeQtO2rTUg9vDuTmSGsSWoMhGt5lxCyqoz8EaDo david0601d@gmail.com
The key's randomart image is:
+--[ED25519 256]--+
|    +            |
|   + = .         |
|. . * =          |
|*o   O .         |
|B=. O . S        |
|E.+B =   o       |
|o**.= + . .      |
|+ooB +   .       |
| ++.. .          |
+----[SHA256]-----+
```

得到公鑰在 `~/.ssh/id_ed25519.pub` 私鑰在 `~/.ssh/id_ed25519`。注意， 之後會需要分享此公鑰給遠端機器或是遠端服務來做到以金鑰進行 SSH 連線。

