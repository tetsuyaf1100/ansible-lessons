# ansible-lessons

## Ansibleとは

## コントロールノードとターゲットノード

## non pass ssh 設定
 
コントロールノードで秘密鍵・公開鍵の作成
```

# mkdir .ssh
# chmod 700 .ssh
# ssh-keygen -t rsa

# ssh-copy-id -i ~/.ssh/id_rsa.pub <ターゲットノードのip address>
```

 ssh-copy-id コマンドを実行すると、ターゲットノードの　~/.ssh/authorized_keys に公開鍵が追加される
 
 
