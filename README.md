## Who I am

金融・不動産領域の実務経験をバックグラウンドに、データエンジニアリングに取り組んでいます。

- **キャリアの背景**: 銀行の担保評価やFASでの資産評価レビューを通じ、「説明可能な意思決定にはデータの収集・構造化・品質管理が不可欠」と痛感し、データエンジニアリングへシフト。
- **データ設計の考え方**: データ活用を「観測データ → 評価 → 意思決定 → 行動 → 結果検証」の一連のプロセスとして捉えています。
- **現在のテーマ**: 一次情報、オープンデータ、外部API、データベンダー等の複数のデータソースを、提供元での加工過程や元データとの関係まで含めて追跡しながら、利用者固有のデータ・評価ロジック・意思決定プロセスへ接続するデータ基盤をテーマに個人開発しています。データの取得元・取得時点・加工経路・利用関係を残し、「その時点でどの情報をもとに、どう評価し、何を判断し、その結果どうなったか」を後から再現・検証できることを重視しています。

---

## Portfolio

金融・不動産領域を中心に、データ取得・ETL・品質管理・DB設計・分析・運用までを一貫して扱うプロジェクトを開発しています。

観測データを取得時点・来歴まで追跡できる形で整備したうえで、現在は「継続監視する条件を登録し、判定し、人がどう対応したかを残す」運用層まで実装しています。

詳細は各プロジェクトのREADMEをご参照ください。

| Project | Output | Why | What | How | Tech Stack |
|---|---|---|---|---|---|
| **Investment Monitoring Data Platform**<br>投資モニタリングデータ基盤<br>[Repository](https://github.com/3110mmn/invest-monitoring-platform) | [Live Demo](https://invest-monitoring-frontend-540015602390.australia-southeast1.run.app) / [OpenAPI](https://invest-monitoring-public-api-540015602390.australia-southeast1.run.app/docs) / [dbt docs](https://3110mmn.github.io/invest-monitoring-platform/dbt/) | 投資判断に使う市場・財務データが複数の取得元に分散し、取得時点・来歴・加工過程を含めて継続的に検証できる基盤が必要だった | 株価・財務の一次観測をraw → Parquet / BigQueryとして蓄積し、継続監視する条件（Trigger）の登録・判定・対応履歴までをPostgreSQLで運用 | GCS rawを原本として、Parquet/DuckDB（読み出し）とBigQuery/dbt（横断・分析履歴）へ分岐。会社予想は「その時点で見えていた値」だけを使う時点整合をdbtテストで固定し、Airflowが取得→品質ゲート→Trigger評価を順序制御（ローカル検証段階、定時取得はGitHub Actions）。冪等ETL、部分失敗、Public/Admin権限分離、実データとsynthetic demoのIAM分離を実装 | Python / FastAPI / PostgreSQL(Neon) / Alembic / GCS / Parquet / DuckDB / pyarrow / BigQuery / dbt / Airflow / Next.js / TypeScript / GitHub Actions / Cloud Run |
| **Hotel Supply & Demand ETL**<br>宿泊市場データ基盤<br>[Repository](https://github.com/3110mmn/hotel-supply-demand-etl) | [Live Demo](https://3110mmn.github.io/hotel-supply-demand-etl/) / [Tableau Public](https://public.tableau.com/views/_17880794228750/1?:language=ja-JP&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) | ホテル担保評価で、公的統計の取得・加工を分析のたびに手作業で行う負荷があった | 観光庁・e-Statの宿泊統計を取得・正規化し、全国・都道府県・市区町村の市場分析レポートを自動生成 | Source discovery → Fetch → Parse → Validation → SQLite → Report。取得元・SHA-256・訂正履歴を記録し、品質検証後のみDB・レポートを更新。GitHub Actionsで更新・配信を自動化 | Python / openpyxl / SQLite / pytest / Ruff / mypy / GitHub Actions / HTML / CSS / JavaScript / Tableau |
