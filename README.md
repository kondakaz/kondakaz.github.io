# kondakaz.github.io — robots.txt 配信用リポジトリ

授業用の架空サイト (jissen-webdata-lecture) のための robots.txt をドメイン直下で配信するリポジトリ。

## なぜこのリポジトリが必要か

robots.txt はドメインのルート (`https://kondakaz.github.io/robots.txt`) に置かれたものだけが有効という Web の標準仕様がある。GitHub Pages のプロジェクトサイト (`/jissen-webdata-lecture/` 配下) には robots.txt を機能する形で置けないため、ユーザサイト (このリポジトリ。リポジトリ名がそのままドメインルートになる) に置く。

検索クローラが HTML の `noindex` を読めるよう、Googlebot などを robots.txt で一律に拒否しない。

polite::bow が読むのはこのファイルである。授業で見せる内容:

- `Disallow: /jissen-webdata-lecture/private/` — 練習サイトの「関係者専用ページ」を拒否 (bow で not scrapable になる体験)
- `Crawl-delay: 5` — bow の出力に表示され、Sys.sleep の目安になる
- `User-agent: BadPracticeBot` への全面拒否 — 特定ボットの名指し拒否の実例 (昨年の gihyo.jp の例の代替)。`bow(url, user_agent = "BadPracticeBot")` で拒否される体験ができる
- GPTBot・CCBot・Google-Extended への全面拒否 — 生成 AI の学習用クローラを拒否する実在の書き方 (報道機関等で増加中)。本サイトでも実際に有効なルールとして機能する
- 各行の `#` コメント — 教材のため、ルールの意図をファイル内に説明してある

解説ページ (書式・パターン集・実在サイトのリンク集) は練習サイト側の
`https://kondakaz.github.io/jissen-webdata-lecture/robots-guide.html` にある。
**robots.txt を書き換えたら、解説ページ (jissen-webdata-lecture リポジトリの tools/build_site.py 内 build_robots_guide) の引用も追随させること。**

## 公開手順 (2026年9月の開講前に実施)

現在は private リポジトリとして push 済み (2026-07-05)。ユーザサイト (kondakaz.github.io) の Pages 公開には public 化が必須のため、開講前に次を行う。

1. リポジトリを public 化する: `gh repo edit kondakaz/kondakaz.github.io --visibility public --accept-visibility-change-consequences`
2. Settings → Pages → Branch: main / (root) を選択 (ユーザサイトは自動で有効になる場合もある)
3. `https://kondakaz.github.io/robots.txt` が表示されることを確認する
4. 本体リポジトリ `jissen-webdata-lecture` も public 化＋Pages 有効化する (そちらの README 参照)
