
# 前提
* Nvidia Driver　がインストール済み
* WSL に Nvidia Container Toolkit がインストール済み


# イメージの作成とDockerComposeの用意
1. Build Image  
    ```
    # xxxx -> Dockerアカウントのユーザ名
    docker build -f OrigianalDockerfile -t xxxx/pytorch-python310-cudnn8-devel-ubuntu22.04:v1.0.0 ./Dockerfiles
    ```

2. Create docker-compose.yaml  
    ```
    .devcontainer の docker-compose_sample.yaml を docker-compose.yaml という名前で複製する  
    docker-compose.yaml 内の xxxx も 1.Build Image 同様にDockerアカウントのユーザ名に変更する  
    ```

# DevContainer の利用開始
1. コンテナを起動しターミナルに入る
    ```
    # VS Code の左下の><をクリックし、コンテナで再度開くを選択
    ```

2. 利用開始
    ```
    # VS Code の場合はそのまま開発開始
    
    # jupyter の場合は以下コマンド実行
    jupyter lab --ip 0.0.0.0 --no-browser --allow-root
    ```

# イメージの更新
1. Edit Dockerfile
    ```
    Dockerfiles の UpdateDockerfile_sample を UpdateDockerfile という名前で複製する 
    UpdateDockerFile の中身を更新する
    xxxx: Dockerアカウントのユーザ名
    yyyy: 現在のImageのバージョン ex v1.0.2
    zzzz: 追加でインストールするライブラリ ex pandas
    ```

2. Build Image  
    ```
    # xxxx -> Dockerアカウントのユーザ名
    # yyyy -> 更新後のImageのバージョン ex v1.0.3
    docker build -f UpdateDockerfile -t xxxx/pytorch-python310-cudnn8-devel-ubuntu22.04:yyyy ./Dockerfiles
    ```

3. Modify docker-compose.yaml  
    ```
    docker-compose.yaml 内の image のタグをビルドしたバージョンに変更する
    ```

# コマンドメモ
```
docker-compose up -d
docker exec -it container_name /bin/bash
docker images
docker pull yyy(user/name:version)
docker push yyy(user/name:version)
docker login/logout
docker tag xxx(name or id) yyy(user/name:version)
docker rmi yyy(user/name:version)
docker commit xxx(name or id) yyy(user/name:version)
```