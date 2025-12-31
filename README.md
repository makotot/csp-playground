# CSP Playground

Content Security Policy (CSP) の動作を検証するためのテストページ集です。

## 概要

このリポジトリは、様々なCSP設定をテストし、その動作を理解するための学習用プロジェクトです。GitHub Pagesを使用してホスティングされています。

## デモページ

GitHub Pagesで公開されています：
`https://[ユーザー名].github.io/csp-playground/`

## テストページ一覧

- **index.html** - メインページ（全テストページへのリンク）
- **csp-inline-script.html** - インラインスクリプトのブロックテスト
- **csp-external-script.html** - 外部スクリプトのブロックテスト
- **csp-nonce.html** - Nonce を使用したスクリプト許可のテスト
- **csp-style.html** - インラインスタイルのブロックテスト
- **csp-report-only.html** - Report-Only モードのテスト

## GitHub Pages の設定方法

1. GitHubリポジトリの **Settings** を開く
2. 左メニューから **Pages** を選択
3. **Source** セクションで以下を設定：
   - Branch: `main` (または `claude/setup-github-pages-ayzk0`)
   - Folder: `/docs`
4. **Save** をクリック
5. 数分後、URLが生成されてサイトが公開されます

## ローカルでの確認方法

### 方法1: Node.js の HTTP サーバー（推奨）

```bash
npx http-server docs -p 8000
```

または

```bash
npx serve docs -p 8000
```

ブラウザで `http://localhost:8000` を開く

### 方法2: ブラウザで直接開く

`docs/index.html` をブラウザで直接開くこともできますが、一部のCSP機能が正しく動作しない可能性があります。ローカルサーバーの使用を推奨します。

## CSPについて

Content Security Policy (CSP) は、クロスサイトスクリプティング (XSS) やデータインジェクション攻撃などを防ぐためのセキュリティレイヤーです。

### 主要なディレクティブ

- `default-src`: すべてのリソースタイプのデフォルトポリシー
- `script-src`: JavaScript のソース制限
- `style-src`: CSS のソース制限
- `img-src`: 画像のソース制限
- `connect-src`: XHR、WebSocket などの接続先制限

### よく使われる値

- `'self'`: 同じオリジンのみ許可
- `'none'`: すべてブロック
- `'unsafe-inline'`: インラインスクリプト/スタイルを許可（非推奨）
- `'unsafe-eval'`: eval() などを許可（非推奨）
- `'nonce-<値>'`: 特定のnonce値を持つインラインコードのみ許可
- `https:`: HTTPS経由のリソースのみ許可

## テスト時の確認ポイント

各テストページで以下を確認してください：

1. **ブラウザの開発者ツール（F12）を開く**
2. **Console タブで CSP 違反のメッセージを確認**
3. **Network タブでブロックされたリソースを確認**
4. **ページ上の表示結果を確認**

## CSPの段階的導入

実際のプロジェクトにCSPを導入する場合の推奨手順：

1. **Report-Only モードで運用開始**
   ```
   Content-Security-Policy-Report-Only: default-src 'self'
   ```

2. **違反レポートを収集・分析**

3. **ポリシーを調整**

4. **本番環境で有効化**
   ```
   Content-Security-Policy: default-src 'self'
   ```

## 参考リンク

- [MDN - Content Security Policy (CSP)](https://developer.mozilla.org/ja/docs/Web/HTTP/CSP)
- [CSP Evaluator](https://csp-evaluator.withgoogle.com/)
- [Content Security Policy Reference](https://content-security-policy.com/)

## ライセンス

MIT

## 貢献

プルリクエストを歓迎します！バグ報告や機能提案は Issue でお願いします。
