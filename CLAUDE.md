# CLAUDE.md — yourclass-app プロジェクトガイド

## プロジェクト概要
「YourClass」は教育/授業管理をテーマにしたモバイルアプリのモックアップです。
バックエンドは構築せず、フロントエンド（画面）開発に集中します。
初めてのアプリ開発者が理解しやすいコードベースを目指します。

## 技術スタック
- **フレームワーク**: React Native + Expo (Managed Workflow)
- **言語**: TypeScript
- **ナビゲーション**: Expo Router (ファイルベースルーティング)
- **UI**: React Native の標準コンポーネント + カスタムコンポーネント
- **状態管理**: React Context (小規模なのでRedux不要)
- **データ**: モックデータ (JSON / TypeScript オブジェクト) — API呼び出しなし

## コーディング規約

### 日本語コメント
- すべてのファイルの先頭に、そのファイルの役割を説明するブロックコメントを記載する
- 関数・コンポーネントには「何をするか」「なぜそうするか」を日本語コメントで記載する
- 型定義には各プロパティの用途をインラインコメントで記載する
- 複雑なロジックにはステップごとにコメントを付与する

### Mermaid 図による解説
- 複数コンポーネントの連携やデータフローなど、理解が難しい構成には
  コロケートした `_docs/flow.html` を配置する
- HTML内に Mermaid CDN を読み込み、ブラウザで直接開いて図を確認できるようにする
- 配置例: `app/(tabs)/_docs/navigation-flow.html`

### ファイル・ディレクトリ構成
```
yourclass-app/
├── app/                    # Expo Router のルーティング (画面定義)
│   ├── (tabs)/             # タブナビゲーション
│   ├── _layout.tsx         # ルートレイアウト
│   └── ...
├── components/             # 再利用可能なUIコンポーネント
├── constants/              # 色・フォントサイズ等の定数
├── contexts/               # React Context (状態管理)
├── hooks/                  # カスタムフック
├── mocks/                  # モックデータ
├── types/                  # TypeScript 型定義
├── utils/                  # ユーティリティ関数
└── assets/                 # 画像・フォント等の静的ファイル
```

### 命名規則
- コンポーネント: PascalCase (`StudentCard.tsx`)
- フック: camelCase, `use` プレフィックス (`useStudents.ts`)
- 型定義: PascalCase, `I` プレフィックスなし (`Student`, `Course`)
- モックデータ: camelCase (`students.ts`, `courses.ts`)
- 定数: SCREAMING_SNAKE_CASE (`PRIMARY_COLOR`)

### コンポーネント設計
- 1コンポーネント1ファイル
- Props の型は同ファイル内で定義 (共有する場合は `types/` へ)
- スタイルは `StyleSheet.create()` を使い、同ファイル末尾に記載
- デフォルトエクスポートを使用

## 開発コマンド
```bash
npx expo start          # 開発サーバー起動
npx expo start --ios    # iOSシミュレーター起動
npx expo start --android # Androidエミュレーター起動
```

## 重要な注意事項
- このアプリはモックアップです。実際のAPI通信は行いません
- モックデータの変更は `mocks/` ディレクトリ内で行います
- 画面遷移のフローを変更する場合は、対応する `_docs/` 内の Mermaid 図も更新してください
