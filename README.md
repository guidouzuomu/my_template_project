

# NestJS + Prisma + PostgreSQL Template

NestJS (v11) をベースにした、堅牢なバックエンド開発用のテンプレートプロジェクトです。
ORMとしてPrismaを採用し、ローカル開発用のデータベース（PostgreSQL）をDockerで簡単に構築できる環境が整っています。

## 🛠 技術スタック

- **Framework**: NestJS (v11)
- **Language**: TypeScript
- **ORM**: Prisma
- **Database**: PostgreSQL (Docker)
- **Package Manager**: npm

---

## 📦 環境構築（Getting Started）

開発を始めるためのセットアップ手順です。

### 1. 依存パッケージのインストール

```
npm install
```

### 2. 環境変数の設定

プロジェクトのルートディレクトリに `.env` ファイルを作成し、データベースの接続情報を記載します。

**コード スニペット**

```
DATABASE_URL="postgresql://postgres:postgres@localhost:6543/postgres"
```

### 3. データベースの起動 (Docker)

Docker Composeを使用して、ローカルにPostgreSQLのデータベースコンテナを立ち上げます。

※事前にDocker Desktop等が起動していることを確認してください。

**Bash**

```
docker compose -f docker/compose.yaml up -d
```

*(※データベースを停止・削除する場合は `docker compose down` を実行します)*

### 4. データベースのマイグレーションと型の生成

Prismaのスキーマ（`schema.prisma`）を実際のデータベースに反映し、同時にTypeScriptの型を生成します。

**Bash**

```
npx prisma migrate dev --name init
```

---

## 🚀 開発サーバーの起動

すべての準備が完了したら、ローカルサーバーを起動します。

**Bash**

```
# 開発モード（ファイルを保存するたびに自動で再起動します）
npm run start:dev
```

サーバーが起動したら、`http://localhost:3000` にアクセスして動作を確認してください。

---

## 💡 便利なコマンド一覧

開発中によく使うコマンドのまとめです。

| **コマンド**         | **説明**                                                   |
| -------------------------- | ---------------------------------------------------------------- |
| `npm run start:dev`      | 開発サーバーを起動（ウォッチモード）                             |
| `npm run build`          | 本番環境用にビルド（`dist`フォルダに出力）                     |
| `npx prisma studio`      | ブラウザ上でDBのデータを直接確認・編集できるGUIツールを起動      |
| `npx prisma generate`    | （スキーマ変更時など）Prismaの型定義を手動で再生成               |
| `nest g resource <名前>` | 新しいAPIのエンドポイント（Controller, Service等）を一式自動生成 |
