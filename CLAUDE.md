# Fieldtune Records 公式サイト

Ch（オーナー）が運営する自然音・フィールドレコーディング素材レーベル「Fieldtune Records」の公式サイト。
Googleサイトで作っていた https://www.fieldtunerecords.com/ を、Claude Codeで更新できる静的HTMLサイトに移行中。

## 現状（2026-11-22 時点）

- 2026-11-23 オーナーの指示で「とりあえず外部リンクだけのペライチ」に縮小した
  - 今の `index.html`: ヘッダー（名前＋About文＋カテゴリ1行＋波形バー）→ Shop / Merch / Listen のリンク → Technical Setup → Licensing → Privacy Policy → フッター（問い合わせメール）
  - About はヘッダーに組み込んだ（見出しなし、Googleサイトの原文のまま）。「Welcome to the official website…」の一文は残すか削るかオーナー未決
  - Technical Setup / Licensing / Privacy Policy はオーナーの希望で戻した（2026-11-23）。文言はGoogleサイトの原文そのまま。言い換えない
  - 例外: Licensing の1文目のあとに、オーナーの希望で「If those terms differ from the summary below, the platform's terms apply.」を追加した（販売先の規約が優先）
- 教訓: 「〜だけでいい」と言われても、License・Privacy のような説明系の項目を消すときは先に確認する
- まだ公開していない。本番は引き続きGoogleサイトが表示されている

## 構成

```
index.html   # サイト本体。CSS/JSもすべてこの1ファイルに入っている
CNAME        # GitHub Pages用の独自ドメイン設定（www.fieldtunerecords.com）
README.md    # 空でよい（管理者はオーナー本人なので不要。公開手順はこのファイルに書く）
CLAUDE.md    # このファイル
```

- ビルドツールなし。素のHTML/CSS/少量のJSのみ。フレームワークを足すのはオーナーが望んだときだけ
- ページが増えたら `css/style.css` に切り出してよい
- フォントは Google Fonts の Inter（サンセリフ）1種類。見出しも本文も同じ。オーナーの希望でサンセリフにした（セリフ体は試して却下）。線が細いとも言われたので、本文は400、見出しは700、罫線は1.5px、アイコン・波形の線は太めにしてある。細いウェイト（300以下）に戻さない

## サイトの中身（Googleサイトから移植したもの）

サイトの文言は**英語**（海外の購入者向け）。オーナーとのやりとりは日本語。

- キャッチ: Nature ambience, environmental recordings, and original music loops for games, films, VR, and digital media
- 商品カテゴリ: Ambience / Sound Effects / Royalty-free Music Loops
- 録音: 静かな自然の中で現地録音、処理は最小限
  - Recorder: ZOOM F3
  - Mic: BEHRINGER C-2（ステレオペア）
  - Format: WAV 48 kHz / 32-bit float
- ライセンス: 各販売プラットフォームの規約に従う。商品ページに別の記載がない限り
  - OK: 商用・非商用利用、編集・加工、ゲームのビルドや映像・レンダーへの組み込み
  - NG: 再販・再配布、素材ファイルそのままの共有、競合アセットパックへの収録
- プライバシーポリシー: メールで自主的に送られたもの以外の個人情報は集めない。開示・削除の依頼は下記アドレスへ
- 問い合わせ: info@fieldtunerecords.com

## リンク一覧

並び順はオーナーの売上が多い順（BOOTHが1位、Unityが2位）。

| 名前 | URL | 区分 |
|---|---|---|
| BOOTH | https://fieldtune.booth.pm/ | 販売 |
| Unity Asset Store | https://assetstore.unity.com/ja-JP/publishers/119348 | 販売 |
| Audiostock | https://audiostock.jp/artists/65299 | 販売 |
| Bandcamp | https://fieldtunerecords.bandcamp.com/ | 販売 |
| Gumroad | https://fieldtunerecords.gumroad.com/ | 販売 |
| SUZURI | https://suzuri.jp/fieldtunerecords | グッズ |
| SoundCloud | https://soundcloud.com/fieldtunerecords | 試聴 |
| YouTube | https://www.youtube.com/@FieldtuneRecords | 試聴 |

## デザイン

- コンセプト: 森・苔・紙。落ち着いた自然のトーン
- 色（`:root` のCSS変数）: 背景 `#f4f1ea` / 背景(交互) `#ebe6db` / 文字 `#22281f` / 補助文字 `#5b6355` / アクセント(苔) `#4f6b47`・`#34492f` / 線 `#d4cdbd` / カード `#fbfaf6`
- 構成: 1カラム（幅560px）、すべて左揃え。Header → Shop（販売）→ Merch（グッズ）→ Listen（試聴）→ Technical Setup → Licensing → Privacy Policy → Footer。ナビなし
- 2026-11-23 のデザイン方針（オーナー承認済み）
  - 主役は波形バーだけ。ヘッダー下端の苔色の線（地面）に立たせる。ほかは静かに
  - リンクはボタン（高さ56px、苔色の2px枠、角丸10px、名前だけ中央揃え、ホバーで苔色に塗る）。「→」や説明文は付けない
    - 罫線で区切った行も試したが、オーナーに「見出しと区別しにくい、ボタンの方がいい」と言われて変えた。行の形式に戻さない
  - 見出しは普通の書き方（Shop）。全部大文字のラベル、グラデーションの背景、ホバーで浮く動きは使わない
- スマホ対応済み（320px幅で横はみ出しなしを確認）
- 確認用ローカルサーバー: `.claude/launch.json` の `site`（http://localhost:8123）。ファイル直開きのプレビューはJSが動かず波形バーが出ないので、こちらで見る

## 公開の予定

1. GitHubにリポジトリを作ってpush
   - 公開（public）リポジトリでよい。オーナーの希望は「他人に書き換えられなければいい」で、コードを見られるのは構わない
   - コラボレーターは追加しない。他人からのPull Requestは取り込まない（オーナー以外の変更は入れない）
2. GitHub Pagesで公開（mainブランチのルート）。`CNAME` はもう置いてある
3. ドメイン管理会社でDNSをGoogleサイトからGitHub Pagesに向け直す（オーナーが作業）
   - `www` → CNAME `<GitHubユーザー名>.github.io`
   - apex（fieldtunerecords.com）→ A レコード 185.199.108.153 / 185.199.109.153 / 185.199.110.153 / 185.199.111.153
   - 切り替え後、GitHub Pagesの設定で「Enforce HTTPS」をオンにする

## 今後の候補（オーナーが決めたらやる）

- 日本語版（言語切り替え）
- 試聴プレイヤーの埋め込み（SoundCloud / YouTube）
- 商品ごとの紹介ページ
- OGP画像・favicon

## 作業ルール

- 変更したら、ブラウザで見た目を確認してから報告する（スマホ幅も）
- リンクを足すときはURLをオーナーに確認する。推測で作らない
- 宣伝文句・数値・レビューなどを勝手に作らない。中身はオーナーが言ったこと／既存サイトにあることだけ
- オーナーは平日の作業時間が限られているので、確認事項はまとめて短く聞く
