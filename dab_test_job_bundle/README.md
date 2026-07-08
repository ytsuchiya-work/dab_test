# dab_test_job_bundle

このバンドルは既存ジョブ `dab_test_job` を Declarative Automation Bundles 化した最小構成です。

## 構成

* ジョブ定義: `resources/dab_test_job.job.yml`
* 実行ノートブック: `src/notebooks/dab_output.py`
* メイン設定: `databricks.yml`

現在の `dab_output.py` は 1 セル相当の内容で、`print("success")` を実行します。

## 含まれるジョブ

* ジョブ名: `dab_test_job`
* タスクキー: `dab_test`
* 実行方式: ノートブックタスク
* ノートブックパス: `src/notebooks/dab_output.py`
* パフォーマンスモード: `PERFORMANCE_OPTIMIZED`

## 使い方

バンドルルートで以下を実行します。

### Validate

`databricks bundle validate --strict --target dev`

### Deploy

`databricks bundle deploy --target dev`

### Run

`databricks bundle run dab_test_job --target dev`

## 補足

* `databricks.yml` の `include` 設定により `resources/*.yml` 配下のジョブ定義が読み込まれます。
* `dev` ターゲットは development モード、`prod` ターゲットは production モードです。
