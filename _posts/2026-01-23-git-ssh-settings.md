# 重新設定 git 與 ssh

過往對他們一知半解，現在重新設定。

```bash
ssh-keygen -t ed25519 -C david0601d@gmail.com # `-t` 指定加密演算法， `-C` 為標籤，當想要區分金鑰用途時，例如工作用、學校用，就可加上 email 標籤進行區分。
```
設定過程中都輸入 Enter 即可。得到公鑰在 `~/.ssh/id_ed25519.pub` 私鑰在 `~/.ssh/id_ed25519`。注意， 之後會需要分享此公鑰給遠端機器或是遠端服務來做到以金鑰進行 SSH 連線。

```bash
git restore --staged <file> # 把檔案加入到暫存區後反悔時，可用它暫時把檔案從暫存區 (stage area) 移出去。
git restore file            # 若從暫存區移出後，還想恢復成變更前的狀態，可再次使用 `git restore` (注意沒有 `--staged`)

# 情境：假設已經 git add .gitignore，反悔想退回，可以 git restore --staged .gitignore。若已經 git commit -m "add .gitignore" 後，想要反悔就必須 git reset。

# 狀況 1
git add .gitignore # 填寫完後 add 到 Staged Changes。(從 Untracked -> Added)
git restore --staged .gitignore # 退回至工作目錄 (Changes) (從 Added -> Untracked)

# 狀況 2
git add .gitignore
git commit -m "add .gitignore" # Staged Changes 變到 Outgoing Changes 狀態。
git reset --soft HEAD~1  # 反悔了，想退回至前一個 commit。這樣 commit 會被撤回，.gitignore 會留在暫存區 (Staged)。
git reset --mixed HEAD~1 # 又或者，退回至工作目錄 (Changes)
```

Outgoing Changes 即將推送的變更
Staged Changes 暫存區變更
Changes 工作目錄上的變更

修 bug、增加 feature、.gitignore 加入新規則，應該分別寫一個 commit，而不是全部寫在一起。原因是比較好 roll back 到上一個版本

