## Who I am

金融・不動産領域の実務経験をバックグラウンドに、データエンジニアリングに取り組んでいます。

- **キャリアの背景**: 銀行の担保評価やFASでの資産評価レビューを通じ、「説明可能な意思決定にはデータの収集・構造化・品質管理が不可欠」と痛感し、データエンジニアリングへシフト。

- **データ設計の考え方**: データ活用を「観測データ → 評価 → 意思決定 → 行動 → 結果検証」の一連のプロセスとして捉えています。

- **現在のテーマ**: 未整備なデータを再現可能な基盤へ構造化し、取得時点・来歴・加工過程を追跡できるデータ設計に取り組んでいます。データ基盤を単なる蓄積先ではなく、将来的に「その時点で何を根拠に判断し、その結果どうなったか」を検証・改善できる意思決定支援基盤へ発展させることを重視しています。

---

## Portfolio

金融・不動産領域を中心に、データ取得・ETL・品質管理・DB設計・分析・運用までを一貫して扱うプロジェクトを開発しています。

現在のポートフォリオでは、その土台となる「観測データ」を、取得時点・来歴まで追跡できる再現可能な形で整備することを中心に実装しています。今後は、評価・意思決定・結果検証までを分離して扱える基盤へ拡張していきます。

詳細は各プロジェクトのREADMEをご参照ください。



| Project                                                                                                                           | Output                                                                                                                                                                                                                | Why                                                     | What                                                | How                                                                                                                                  | Tech Stack                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| **Investment Monitoring Data Platform**<br>投資モニタリングデータ基盤<br>[Repository](https://github.com/saito-mmn/invest-monitoring-platform) | [Live Demo](https://invest-monitoring-frontend-540015602390.australia-southeast1.run.app) / [OpenAPI](https://invest-monitoring-public-api-540015602390.australia-southeast1.run.app/docs) | 投資判断に使う市場・財務データが複数の取得元に分散し、取得時点・来歴・加工過程を含めて継続的に検証できる基盤が必要だった | 投資テーマ・監視対象をPostgreSQLで管理し、株価・財務の一次観測をraw → Parquetとして蓄積。取得元・取込実行まで追跡可能な分析・Serving基盤を構築 | GCS raw → Parquet → DuckDBを分析層、PostgreSQLをControl Planeとして分離。FastAPI / Next.jsから同一の読み出し経路を利用し、冪等ETL、部分失敗、CI/CD、バックアップ、Public/Admin権限分離、実データとsynthetic demoの物理分離を実装 | Python / FastAPI / PostgreSQL / Alembic / GCS / Parquet / DuckDB / pyarrow / Next.js / TypeScript / GitHub Actions / Cloud Run / Neon |
| **Hotel Supply & Demand ETL**<br>宿泊市場データ基盤<br>[Repository](https://github.com/saito-mmn/hotel-supply-demand-etl)                  | [Live Demo](https://3110mmn.github.io/hotel-supply-demand-etl/) / [Tableau Public](https://public.tableau.com/views/_17880794228750/1?:language=ja-JP&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) | ホテル担保評価で、公的統計の取得・加工を分析のたびに手作業で行う負荷があった                  | 観光庁・e-Statの宿泊統計を取得・正規化し、全国・都道府県・市区町村の市場分析レポートを自動生成  | Source discovery → Fetch → Parse → Validation → SQLite → Report。取得元・SHA-256・訂正履歴を記録し、品質検証後のみDB・レポートを更新。GitHub Actionsで更新・配信を自動化      | Python / openpyxl / SQLite / pytest / Ruff / mypy / GitHub Actions / HTML / CSS / JavaScript / Tableau   |



