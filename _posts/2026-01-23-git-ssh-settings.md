# 重新設定 git 與 ssh

過往對他們一知半解，現在重新設定。

```bash
ssh-keygen -t ed25519 -C david0601d@gmail.com # `-t` 指定加密演算法， `-C` 為標籤，當想要區分金鑰用途時，例如工作用、學校用，就可加上 email 標籤進行區分。
```
設定過程中都輸入 Enter 即可。得到公鑰在 `~/.ssh/id_ed25519.pub` 私鑰在 `~/.ssh/id_ed25519`。注意， 之後會需要分享此公鑰給遠端機器或是遠端服務來做到以金鑰進行 SSH 連線。

```bash
git restore --staged <file> # 把檔案加入到暫存區後反悔時，可用它暫時把檔案從暫存區 (stage area) 移出去。
git restore file            # 若從暫存區移出後，還想恢復成變更前的狀態，可再次使用 `git restore` (注意沒有 `--staged`)
```
