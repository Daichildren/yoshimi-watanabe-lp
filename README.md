# 渡辺喜美 公式LP

元金融担当大臣・元行政改革担当大臣 渡辺喜美の公式ランディングページ。
企業顧問・アドバイザリー・講演・寄稿の獲得を目的とした営業用LP。

---

## 📁 ファイル構成

```
yoshimi_lp/
├── index.html          ← LP本体（CSS埋め込み・1ファイル完結）
├── privacy.html        ← プライバシーポリシー・利用規約
├── README.md           ← このファイル
├── .gitignore          ← Git除外設定
└── images/             ← 写真ファイル（4枚）
    ├── yoshimi_hero.jpg
    ├── yoshimi_speaking.jpg
    ├── yoshimi_profile.jpg
    └── yoshimi_contact.jpg
```

---

## 🔒 現状：noindex 設定中（検索エンジン非表示）

公開後も Google 等の検索エンジンには表示されない設定。本公開時は `index.html` の以下を削除：

```html
<meta name="robots" content="noindex, nofollow">
```

privacy.html は永続的に noindex で問題なし。

---

## 👀 ローカルプレビュー

```bash
cd /Users/daichi/Desktop/CC/01_sns/01-2-443/sub-projects/yoshimi_lp
python3 -m http.server 8000
# → http://localhost:8000 でブラウザ確認
```

---

## 🚀 Cloudflare Pages にデプロイする手順

### Step 1: GitHubリポジトリ作成

1. https://github.com/new でリポジトリ作成
2. リポジトリ名（例）: `yoshimi-watanabe-lp`
3. **Public** または **Private** どちらでも可（Cloudflareは両方対応）
4. README・.gitignore・License は **追加しない**（ローカルに既にある）

### Step 2: ローカルから git push

ターミナルで以下を実行：

```bash
cd /Users/daichi/Desktop/CC/01_sns/01-2-443/sub-projects/yoshimi_lp

git init
git add .
git commit -m "Initial commit: Yoshimi Watanabe LP"
git branch -M main
git remote add origin https://github.com/[YOUR_USERNAME]/yoshimi-watanabe-lp.git
git push -u origin main
```

`[YOUR_USERNAME]` は自分のGitHubユーザー名に置換。

### Step 3: Cloudflare Pages でデプロイ

1. https://dash.cloudflare.com/ にサインアップ（無料）
2. 左メニュー **Workers & Pages** → **Create application**
3. **Pages** タブ → **Connect to Git**
4. GitHubアカウント連携 → 作成したリポジトリ選択
5. **Build settings** はそのまま（静的HTMLなのでビルド不要）
   - Framework preset: `None`
   - Build command: 空欄
   - Build output directory: 空欄（または `/`）
6. **Save and Deploy** ボタン
7. 数十秒で `https://yoshimi-watanabe-lp.pages.dev` 等のURLで公開

---

## 🌐 独自ドメイン取得＆接続

### おすすめドメイン候補

| ドメイン | 想定価格/年 | 用途 |
|---|---|---|
| `watanabe-yoshimi.com` | ¥1,500〜2,000 | グローバル・標準（最推奨） |
| `watanabe-yoshimi.jp` | ¥3,000〜4,000 | 国内向け権威性 |
| `yoshimi-watanabe.com` | ¥1,500〜2,000 | 英語表記順 |

### Step 4: Cloudflare Registrar でドメイン取得（推奨）

1. Cloudflare ダッシュボード → **Domains** → **Register Domains**
2. 希望ドメイン検索 → 価格確認
3. 購入手続き（年¥1,500程度）

**メリット**: 更新料も卸値・WHOIS保護無料・自動DNS設定

### Step 5: Cloudflare Pages にカスタムドメイン追加

1. Pages プロジェクト → **Custom domains** タブ
2. **Set up a custom domain** → ドメイン入力
3. **Activate domain** → DNS自動設定（Cloudflareで取ったドメインなら数秒）
4. 数分〜半日でSSL証明書発行・独自ドメインで公開

---

## ✅ 公開前の最終チェック

- [ ] `index.html` を Cmd+Shift+R リロードで全セクション確認
- [ ] スマホでも崩れないか確認（Chrome DevTools のレスポンシブモード）
- [ ] お問い合わせフォームのリンクが正しく開くか
- [ ] X / note / Substack の各リンクが正しく開くか
- [ ] privacy.html のリンクが正しく開くか
- [ ] 画像が全て表示されているか
- [ ] note / Xの埋め込みが表示されるか

## 🔓 本公開（noindex 解除）の手順

公開準備完了 → 検索エンジンに載せたい時：

1. `index.html` から `<meta name="robots" content="noindex, nofollow">` 削除
2. git commit → push
3. Cloudflare Pages が自動再デプロイ（数十秒）
4. Google Search Console で sitemap 登録（任意・SEO強化）

---

## 📊 営業観点の補足（メモリー連携）

- **真の北極星**: 追加収入確保（月+20-50万円・3-6ヶ月）
- **LP導入価格目安**: 梅10-15万・竹25-40万・松50-80万（月額）
- **稼働目安**: 顧問契約3-5社で月15-25時間

---

## 🔄 今後の更新候補（公開後）

1. **画像差し替え**（大知のAI加工画像 or 本人事務所提供の正規写真）
2. **クライアントの声・実績ロゴ集**（案件発生後）
3. **動画埋め込み**（90秒メッセージ動画等）
4. **Substack 実運用後にリンク有効化**
5. **アクセス解析**（Google Analytics 4 or Plausible）

---

## 📝 制作メモ

- **設計コンセプト**: 紺×ゴールドの権威系カラー × 経営者の実利目線コピー
- **フォント**: 見出し Noto Serif JP / 本文 Noto Sans JP
- **レスポンシブ**: モバイル・タブレット・PC対応
- **JS**: Intersection Observer（スクロールアニメ）、カルーセル制御、Xウィジェット
- **外部依存**: Google Fonts CDN、YouTube サムネCDN、X widgets.js、note iframe、Google Forms

---

制作: Claude Code (Kai)
最終更新: 2026-06-08
