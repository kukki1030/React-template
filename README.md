# React テンプレート

React + TypeScript + Vite + Tailwind CSS を使用したモダンな Web アプリケーション開発テンプレートです。

## 🚀 技術スタック

### コアライブラリ

- **React**: ^19.2.0 - UI ライブラリ
- **React DOM**: ^19.2.0 - React DOM レンダラー
- **TypeScript**: ~5.9.3 - 型安全な開発環境

### ビルドツール

- **Vite (Rolldown-Vite)**: 7.2.5 - 高速なビルドツールとホットモジュールリプレースメント(HMR)
- **@vitejs/plugin-react**: ^5.1.1 - React Fast Refresh 用の Vite プラグイン

### スタイリング

- **Tailwind CSS**: ^3.4.19 - ユーティリティファースト CSS フレームワーク
- **PostCSS**: ^8.5.6 - CSS トランスフォーマー
- **Autoprefixer**: ^10.4.23 - CSS ベンダープレフィックスの自動追加

### Linting & 型チェック

- **ESLint**: ^9.39.1 - コード品質とスタイルチェック
- **TypeScript ESLint**: ^8.46.4 - TypeScript 用 ESLint 設定
- **eslint-plugin-react-hooks**: ^7.0.1 - React Hooks のルール
- **eslint-plugin-react-refresh**: ^0.4.24 - React Fast Refresh のルール

## 📦 セットアップ

### 必要な環境

- Node.js (推奨: 最新の LTS 版)
- npm または yarn

### インストール

```bash
# 依存関係のインストール
npm install
```

## 🛠️ 使用方法

### 開発サーバーの起動

```bash
npm run dev
```

開発サーバーが起動し、HMR が有効になります。

### プロダクションビルド

```bash
npm run build
```

TypeScript の型チェックと Vite ビルドを実行します。ビルド成果物は `dist` ディレクトリに出力されます。

### プレビュー

```bash
npm run preview
```

ビルドされたアプリケーションをローカルでプレビューします。

### Linting

```bash
npm run lint
```

ESLint を使用してコードをチェックします。

## ⚙️ 設定について

### Vite プラグイン

現在、以下の Vite 公式プラグインを使用しています：

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) - Babel（または rolldown-vite での oxc）を使用した Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) - SWC を使用した Fast Refresh

### React Compiler

React Compiler は、開発およびビルドパフォーマンスへの影響を考慮して、このテンプレートではデフォルトで無効になっています。有効にする場合は、[公式ドキュメント](https://react.dev/learn/react-compiler/installation)を参照してください。

### ESLint 設定の拡張

本番環境向けのアプリケーションを開発する場合、型を考慮した Lint ルールを有効にすることを推奨します：

```js
export default defineConfig([
  globalIgnores(["dist"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [
      // その他の設定...

      // tseslint.configs.recommendedを削除し、以下に置き換える
      tseslint.configs.recommendedTypeChecked,
      // より厳格なルールの場合
      tseslint.configs.strictTypeChecked,
      // スタイル関連のルールを追加する場合（オプション）
      tseslint.configs.stylisticTypeChecked,

      // その他の設定...
    ],
    languageOptions: {
      parserOptions: {
        project: ["./tsconfig.node.json", "./tsconfig.app.json"],
        tsconfigRootDir: import.meta.dirname,
      },
      // その他のオプション...
    },
  },
]);
```

### React 専用の Lint ルール

[eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x)と[eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom)をインストールすることで、React 専用の Lint ルールを追加できます：

```bash
npm install -D eslint-plugin-react-x eslint-plugin-react-dom
```

```js
// eslint.config.js
import reactX from "eslint-plugin-react-x";
import reactDom from "eslint-plugin-react-dom";

export default defineConfig([
  globalIgnores(["dist"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [
      // その他の設定...
      // React用のLintルールを有効化
      reactX.configs["recommended-typescript"],
      // React DOM用のLintルールを有効化
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ["./tsconfig.node.json", "./tsconfig.app.json"],
        tsconfigRootDir: import.meta.dirname,
      },
      // その他のオプション...
    },
  },
]);
```

## 📁 プロジェクト構造

```
react-template/
├── public/           # 静的アセット
├── src/             # ソースコード
│   ├── assets/      # 画像やフォントなどのアセット
│   ├── App.tsx      # メインアプリコンポーネント
│   ├── App.css      # アプリスタイル
│   ├── main.tsx     # エントリーポイント
│   └── index.css    # グローバルスタイル（Tailwind CSS含む）
├── index.html       # HTMLテンプレート
├── vite.config.ts   # Vite設定
├── tsconfig.json    # TypeScript設定
├── eslint.config.js # ESLint設定
└── tailwind.config.js # Tailwind CSS設定
```

## 📝 ライセンス

このプロジェクトはプライベートテンプレートです。

## 🔗 参考リンク

- [React Documentation](https://react.dev/)
- [TypeScript Documentation](https://www.typescriptlang.org/)
- [Vite Documentation](https://vite.dev/)
- [Tailwind CSS Documentation](https://tailwindcss.com/)
- [ESLint Documentation](https://eslint.org/)
