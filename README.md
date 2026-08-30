# now-match-legal

iOSアプリ「スグイコ」（旧 Now Match）の紹介・法務ページ**だったもの**。
いまは <https://cleardrop.jp> への**転送板**です。

## なぜ転送板なのか

**条文の正本は事業サイトの中にあります。** かつてはサイトと GitHub Pages の
両方に条文を持っていて、片方だけが古びるという事故が実際に起きました
（却下される前の「位置情報マッチングアプリ」「Plus / Gold / Platinum」が
公開され続けていた）。同じ条文を2箇所に置かないために、「両方に置く」ではなく
「片方を転送にする」で運用します。

## ⚠️ このリポジトリを消さないこと

アプリが `lib/legal_links.dart` にこのURLを焼き込んでおり、**配信済みの
ビルドはここを開き続けます。** アプリ側を cleardrop.jp のURLに差し替えた
あとも、旧ビルドを使い続ける人がいるため転送板は残してください。

## 転送先

**ハッシュを引き継ぎます。** 1枚のページに節が並ぶ作りで、ハッシュが節の
識別子そのものだったためです（ファイルごとに分かれている `resuru-legal` は
ファイル単位で転送先を固定しており、事情が違います）。

| 受け取るハッシュ | 転送先 |
|---|---|
| `#privacy` | `https://cleardrop.jp/suguiko/legal#privacy` |
| `#terms` | `https://cleardrop.jp/suguiko/legal#terms` |
| `#tokushoho` | `https://cleardrop.jp/suguiko/legal#tokushoho` |
| `#support` | `https://cleardrop.jp/suguiko/support` |
| `#top` | `https://cleardrop.jp/suguiko` |
| なし・その他 | `https://cleardrop.jp/suguiko/legal` |

## 転送の仕組み

GitHub Pages は 301 を返せないので、`<link rel="canonical">` ＋
`<meta http-equiv="refresh">` ＋ `location.replace()` の3つで送ります。

**本文の実リンクを消さないでください。** JS も meta refresh も辿らずに取得
するクローラ（App Review を含む）に、条文の在り処が見えるようにするための
ものです。

`assets/` は条文を持っていた頃の名残で、いまはどこからも参照していません。

## 中身を直したいとき

**このリポジトリではなく、事業サイトのほうを直してください。**
条文の実体は `cleardrop-hp` の `content/products/suguiko/legal.tsx` です。

App Store Connect の「サポートURL」「プライバシーポリシーURL」も、転送板を
経由させず `https://cleardrop.jp/suguiko/support` ／
`https://cleardrop.jp/suguiko/legal#privacy` を直接指すのが望ましいです
（審査中のアプリでは特に、転送を挟まないほうが確実です）。
