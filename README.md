# ansible-lessons

## Ansibleとは
構成管理ツールのひとつ。  
Python製でエージェントレス。  
non pass ssh 設定とpythonがあれば動作する。  

## コントロールノードとターゲットノード
* コントロールノード  
Ansibleを実行するノード  
* ターゲットノード  
Ansibleが実行されるノード  

## non pass ssh 設定
コントロールノードで秘密鍵・公開鍵の作成
```

# mkdir .ssh
# chmod 700 .ssh
# ssh-keygen -t rsa

# ssh-copy-id -i ~/.ssh/id_rsa.pub <ターゲットノードのip address>
```

 ssh-copy-id コマンドを実行すると、ターゲットノードの　~/.ssh/authorized_keys に公開鍵が追加される

## サンプル ansible コマンド
コントロールノードにinventoryファイルを配置
inventoryファイルにターゲットノードを記載する
ここでは、inventoryファイルをhostsとする

hosts
```
[local]
127.0.0.1 ansible_connection=local

[target]
192.168.10.10
```

ping コマンドを打つ場合
```
ansible -i hosts -m ping
```

## サンプル ansible-playbook コマンド

ansible-playbookを使用する場合は、yamlファイルを配置する
yamlファイルに実行したいことを記載する

a.yml
```
---

- hosts: target
  become: yes
  tasks:
    - name: debug
      debug:
        msg: message
```

ansible-playbook -i hosts a.yml




 
 
