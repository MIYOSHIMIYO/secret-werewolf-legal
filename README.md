# secret-werewolf-legal

**正本URLで運用する 利用規約 / プライバシーポリシー**  
- 最新：`/terms/`  
- アーカイブ：`/terms/v/<semver>/`  
- プライバシー：`/privacy/`

## 運用ルール
1. 改定時は `terms/v/X.Y.Z/` を新規作成して固定保存
2. `/terms/` を新しい本文に差し替え
3. 版・初版日・最終改定日・連絡先・正本URLをページに明記
4. `CHANGELOG.md` を更新し Git タグ `vX.Y.Z` を付与

## GitHub Pages
- Settings → Pages → Source: "Deploy from a branch" / Branch: `main`
- 公開URL: `https://miyoshiyuudai.github.io/secret-werewolf-legal/`

## クライアント側での設定例

### .env ファイル
```bash
# 利用規約・プライバシーポリシーの正本URL
VITE_TERMS_URL=https://miyoshiyuudai.github.io/secret-werewolf-legal/terms/
VITE_PRIVACY_URL=https://miyoshiyuudai.github.io/secret-werewolf-legal/privacy/
VITE_TERMS_ARCHIVE_URL=https://miyoshiyuudai.github.io/secret-werewolf-legal/terms/v/1.0.0/
```

### 利用規約ページでの使用例
```typescript
// 正本URLをブラウザで開く
const openFullTerms = async () => {
  const fullTermsUrl = import.meta.env.VITE_TERMS_URL || "https://miyoshiyuudai.github.io/secret-werewolf-legal/terms/";
  window.open(fullTermsUrl, "_blank");
};
```

## 設定手順

### 1. リポジトリ作成
```bash
# GitHubで新規リポジトリを作成
# リポジトリ名: secret-werewolf-legal
# 公開設定: Public
# README.md: チェック
# .gitignore: Node
# ライセンス: MIT
```

### 2. ローカルにクローン
```bash
git clone https://github.com/miyoshiyuudai/secret-werewolf-legal.git
cd secret-werewolf-legal
```

### 3. ファイルを追加・コミット
```bash
git add .
git commit -m "初版公開（利用規約・プライバシーポリシー）"
git push origin main
```

### 4. GitHub Pages有効化
1. リポジトリの Settings タブを開く
2. 左サイドバーの "Pages" をクリック
3. Source で "Deploy from a branch" を選択
4. Branch で "main" を選択
5. Save をクリック

### 5. 初回デプロイ完了確認
- 数分後に `https://miyoshiyuudai.github.io/secret-werewolf-legal/` でアクセス可能
- 利用規約: `https://miyoshiyuudai.github.io/secret-werewolf-legal/terms/`
- プライバシーポリシー: `https://miyoshiyuudai.github.io/secret-werewolf-legal/privacy/`

## 今後の更新手順

### 利用規約改定時
1. 新しいバージョン用のアーカイブディレクトリを作成
   ```bash
   mkdir -p terms/v/1.1.0
   cp terms/index.html terms/v/1.1.0/index.html
   ```
2. アーカイブファイルのcanonical URLを更新
3. 正本（`/terms/index.html`）を新しい内容に更新
4. 版・日付・連絡先等を更新
5. CHANGELOG.mdを更新
6. Gitタグを付与
   ```bash
   git add .
   git commit -m "利用規約 v1.1.0 に更新"
   git tag v1.1.0
   git push origin main --tags
   ```

### プライバシーポリシー更新時
1. `/privacy/index.html` を更新
2. 版・日付・連絡先等を更新
3. CHANGELOG.mdを更新
4. コミット・プッシュ

## 注意事項
- アーカイブファイルは絶対に変更しない（法的証拠として保持）
- 正本URLは常に最新版を指すようにする
- 改定時は必ずCHANGELOG.mdとGitタグを更新する
- 連絡先メールアドレスは実際に使用可能なものを設定する 