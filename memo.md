# memo

## 設定

### GitHub の SSH アクセスができるようにホストと秘密鍵の共有

keychain インストール（WSL）

```bash
sudo apt install keychain
```

ssh-agent を動かして、keychainも動かすため、 ~/.bashrc を編集

```text
if [ -z "${SSH_AGENT_PID}" ]; then
  eval `ssh-agent` 1>/dev/null
fi

# keychain
/usr/bin/keychain -q --nogui $HOME/.ssh/id_ed25519_github # SSHの秘密鍵を読み込み
source $HOME/.keychain/$(hostname)-sh
```

Dev Container 側で git config の設定

```bash
git config user.name hoge
git config user.email aaa@example.com
```
