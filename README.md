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
claude --agent product:orchestrator
claude --agent product:executor
claude --agent product:solo
```

- orchestrator — 会話に徹する指揮者。設計判断は自分で下し、実装はすべて worker に委託する。GitHub（Issue / PR / worktree）を回すチーム開発向け
- executor — 自分の手で実装し、難しい実装だけ worker に委託する。判断は advisor に外出しする。GitHub を回すチーム開発向け
- solo — executor の軽量版。GitHub / Sentry を使わず、ローカルのブランチとコミットで完結する個人開発向け

## 含まれるもの

- エージェント: orchestrator / executor / solo（メインセッション用）、worker（実装専任）、loop（巡回バグ検知）
- スキル: dev — 設計手法（UX 5 planes / OOUI / DDD / Simple Design）、`.docs/` のドキュメント運用、依頼の振り分け、GitHub の手順。`/product:dev drift` などのサブコマンドも提供
