# claude-plugins

Claude Code プラグインのリポジトリ。プラグインやエージェントの構成を変更する前に、必ず公式ドキュメントで何がサポートされているか確認する。憶測でディレクトリやファイルを作らない。

- プラグインとマーケットプレイスの構成: https://code.claude.com/docs/en/plugin-marketplaces
- サブエージェント（agents/*.md）の仕様: https://code.claude.com/docs/ja/sub-agents

注意: agents/*.md は単体のシステムプロンプトであり、references/ などの補助ファイルを持てない。補助ファイルを持てるのはスキル（skills/*/references/）だけ。エージェントから参照させたい資料はスキル側に置く。

プラグインは product の 1 つ。チーム開発（orchestrator / executor、GitHub 運用あり）と個人開発（solo、ローカル完結）の両方を、起動するエージェントの選択で使い分ける。設計思想は plugins/product/CLAUDE.md に書く。このファイルにはリポジトリ全体に関わる内容だけを書く。
