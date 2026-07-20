# claude-plugins

[Claude Code](https://code.claude.com) 用プラグインマーケットプレイス。

## インストール

```shell
/plugin marketplace add nocker-sh/claude-plugins
/plugin install product@nocker
```

ローカルで試す場合。

```shell
/plugin marketplace add ./claude-plugins
/plugin install product@nocker
```

## 使い方

開発スタイルに合わせてエージェントを選んで起動し、あとは会話するだけでよい。要望・バグ報告・Issue 番号を投げると、dev スキルの振り分けに従って記録・実装・検証まで進む。

```shell
claude --agent product:fable
claude --agent product:sonnet
```

- fable — 会話に徹する指揮者。設計判断は自分で下し、実装はすべて worker に委託する。GitHub（Issue / PR / worktree）を回すチーム開発向け
- sonnet — 自分の手で実装し、難しい実装だけ worker に委託する。判断は advisor に外出しする。GitHub / Sentry を使わず、ローカルのブランチとコミットで完結する個人開発・軽量運用向け

## 含まれるもの

- エージェント: fable / sonnet（メインセッション用）、worker（実装専任）、loop（巡回バグ検知）
- スキル: dev — 設計手法（UX 5 planes / OOUI / DDD / Simple Design）、`.docs/` のドキュメント運用、依頼の振り分け、GitHub の手順。人間の入力だけでなく fable / sonnet も判断に応じて自分でサブコマンドを呼び出せる
  - `/product:dev drift` — 仕様書／README と実装の乖離を検出する
  - `/product:dev links` — `[[wikilink]]` の未定義リンク・孤児ページ・循環参照を検出する
  - `/product:dev next` — コードベースを多レンズで探索し、未捕捉タスクを洗い出す（重い処理、300+ agent 規模）
  - `/product:dev features-sync` — routes と features を突合し、ドキュメントを実装に同期する
  - `/product:dev skills` — 技術スタックを見て役に立ちそうな Skill パッケージ（react-doctor、shadcn/ui、cloudflare/skills 等）を自動追加する
