ディレクトリ構成
```
.
│  
├── docker-compose.yml
├── backend
│    ├── Dockerfile
│    ├── app
│    ├── main.py
│    └── requirements.txt
│  
└── frontend
     ├── Dockerfile
     └── app
```

# 初めに
## front
```
cd frontend
npx create-next-app app --ts
docker compose up
```
を実行

使いたいライブラリは予めDockerfileに記述しておくか、docker execでコンテナ内に入りインストールする

yarn add @next/swc-linux-arm64-gnu @next/swc-linux-arm64-musl が要求されるが必須かよくわからん Arm Macのみ？

```コンテナに入ってサーバー起動
docker exec -it frontend sh
yarn dev
```

tsconfig.json compilerOptionsに以下を追加
```
    "types": ["@emotion/react/types/css-prop"],
```

frontend/app/.babelrc　を追加
```
{
    "presets": [
        [
            "next/babel",
                {
                    "preset-react": {
                        "runtime": "automatic",
                        "importSource": "@emotion/react"
                    }
                }
        ]
    ],
    "plugins": ["@emotion/babel-plugin"]
}
```

## back
初期設定
```
docker exec -it backend /bin/sh
python3 -m venv .venv
source .venv/bin/activate       ←環境によって異なる
python -m pip install --upgrade pip setuptools
pip install -r requirements.txt
```
サーバ起動
```
uvicorn main:app --reload
```

Dockerコマンドメモ
```
docker-compose down --rmi all --volumes --remove-orphans キャッシュとか色々消しつつdownできる
docker system prune -f
```
