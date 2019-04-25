# Spark + AI Summit 2019

## WEDNESDAY, APRIL 24

### 9:00 AM

#### Keynote A

* Reynold Xin (Databricks),Brooke Wenig (Databricks)
* What's next for Apache Spark?
 　* Apache Spark 3.0が今年の早いタイミングにリリースされる
*　Unify datas + AI
  * 機械学習ライブラリの氾濫
  * Project hydrogen（Spark 3.xでのトピック）
      * SPARK-24615
      * SPARK-24579
  * mlflow 
* Run Everywhere
  * MESOS, Hadoop, Kubernates
  * HadoopとKubernetesの
  * ２.０でk8sをサポート
  * ３.０でもサポートを強化
* Easy to use APIs 
  * 2013 : API's for DataEngineers 
  * 2015 : API's for DataEngineers & DataScientists
  * Typical journey of a Data Scientist
      * Education -> Pandas
      * Alanlyze small datasets -> Pandas
      * Alanlyze large datasets -> Pandas?
      * Spark DataFrameとPandasDataFrameは書き方が違うので覚えづらい
      * [Koalas : Pandas DataFrame API for Spark](https://github.com/databricks/koalas
)
  * Koalasのデモ
  * Pandasの書き方でSparkDataFrameを使う
  * ex) pandas.get_dammies() -> koalas.get_dammies()
  * Apache 2.0 License
  * pip で利用可能

#### Keynote B

* Ali Ghodsi (Databricks),Michael Armbrust (Databricks)
* Reliability with Delta
* The data is not prepared for Data Sienctists
* Prepares data for analystics
  * Databricks Delta
* Reliability and Quality Data
  * ACID transaction on data lakes
  * Schema enforcement
  * Mixing streaming and batch
  * Scalable metadata handling
  * Time Travel capabilities
* Delta use statistics
  * 10^18 datas per day
  * 1000 of customers
  * Apple (2018's keynote Talks)
* Delta Lakeとしてオープンソース化する <https://delta.io/>
  * Apache 2.0 License
* Evolution of the Data Lake
  * 従来までのデータパイプラインについて一般的なものを説明
  * とても複雑で
  * Delta Lakeを使うことで一元化できるのでとても楽
  * もちろん信頼性は担保

#### Keynote C

* Rohan Kumar (Microsoft)
* IDC White Paperからの引用でインテリジェント・クラウドとインテリジェント・エッジの話
* Microsoft Azureによるインテリジェント・クラウドとインテリジェント・エッジのサービスの説明
* MLflowや.NET for Apache SparkなどDatabricksとの緊密性を強調
* 事例紹介
* AzureのSeeing AIのデモ <https://www.microsoft.com/en-us/garage/wall-of-fame/seeing-ai/>

#### Keynote D - New Golden Age For Computer Architecture

* David Patterson (University of California at Berkeley)
* コンピュータの性能の話
  * 命令セットの話（ISA : Instruction Set Architecture）
  * RISCの話
  * なんでオープンソースソフトがあって、命令セットにはそれがないの？
      * RISC-Vの開発
  * クラウドやエッジでの利用を考えている
  * オープンだからセキュア

### 11:00 AM

#### Horizon: Deep Reinforcement Learning at Scale

* Jason Gauci (Facebook AI)
* レコメンダシステムの説明
  * レコメンダシステムはコントロールシステム（Retrival、Rankingはコントロールするもの）
      * ユーザ体験や将来のモデル・データをコントロールする
  * クラス分離と意思決定の対比
      * クラス分類はそれが何であるか、意思決定支援はどのようにするのが良いかを尋ねる など
  * レコメンデーションを数理モデルで体系化したものを紹介
  * 価値関数の学習は難しい
      * 強化学習の登場
* 強化学習の説明
  * SARSA : State Action Reward State Action
  * Q-Learing : Off-Policy SARSA
  * 強化学習のスケールの適用について
  *	 （数学的知識にかけるのでよくわからん）
* Horizon : Applying RL Pratform
  * Facebook開発のPytorch用強化学習フレームワーク
  * Safe, Large scale deployment
  * Counterfactual Policy Evaluation(CPE)
  * Githubで公開中	
* 参考<https://code.fb.com/ml-applications/horizon/>
* 調べてる時に気になったスライド<https://www.slideshare.net/recruitcojp/ss-42745505>

### 11:50 AM

#### Apache Spark on K8S Best Practice and Performance in the Cloud

* Junjie Chen (Tencent),Junping Du (Tencent)
* 元Intelと元VMwareの社員で[Tencent Cloud](https://intl.cloud.tencent.com/product/sparkling)を担当している
* Sparkling : Case study for Spark in the Cloud
  * <https://intl.cloud.tencent.com/product/sparkling>
  * Dockerized Sparkのモチベーション（サーバレス（疎結合）、オンプレミス）
* KubernetesをSparklingで
  * 各機能をKubernetesの機能で置き換えていく
  * Kubernetesを選ぶ理由は他社と同様
  * k8sで動かすSparkの状況について説明
  * 各サービス単位でPodを分割し独立で動作
  * MetastoreやLivy Serverをk8s clusterとしてまとめ上げる
  * [Pod? Cluster?](https://medium.com/google-cloud/kubernetes-101-pods-nodes-containers-and-clusters-c1509e409e16)
* yarn上のSparkよりもk8sのSparkは遅い
  * 根本原因を分析した結果、emptyDirというエフェメラルなディスクに問題がある
  * RAM backed volumesと一緒にemptyDirをマウントともう一個（tmpfs）
  * 対策するとyarn上のSparkよりも早くなった!
  * でも、[tpcds@1000](http://www.tpc.org/tpcds/)で見るとやはり遅い…
  * [kubelet](https://qiita.com/tkusumi/items/c2a92cd52bfdb9edd613#kubelet)の使用するデイスクがスケールしない？
  * RAM backed media as spark scratch space
  * ワークアラウンドによって、場合によっては速度が上回る

### 12:30 PM

#### Lunch

### 1:40 PM

#### Moving a Fraud-Fighting Random Forest from scikit-learn to Spark with MLlib, MLflow, and Jupyter

* Josh Johnston (Kount)
* [Data Science LifeCycle](https://docs.microsoft.com/en-us/azure/machine-learning/team-data-science-process/overview)
* Manage the model lifecycle
  * Governance Questions
      * Which model are you using?
      * How did you train it?
      * How well does it work?
  * After each anser : Why?
  * Science is repeatble.
* クレジットカードのトランザクションは尋常ではない
* KountのBoost Technology Custmer Viewの説明
* 巨大で大量なRandom Forestを使っている
  * 250 trees 100k nodes, 1GB serialized representation
* 最初のアプローチでは２.５日モデル作成に時間がかかった
  * Databricks Database, Scikit-learn model(Machine Spec : 400GB RAM, 1TB int swap)
  * 価値の高いモデルを作ることができたが、課題もたくさん
  * 遅い、失敗すると一からやり直し、検証架橋とかいまいち
* 次に分散コンピューティングを採用した（HDFS）
  * Spark MLに切り替え、MLflowでロギングするようにした
  * 半日未満に時間が縮まった
  * Jupyterを導入した
  * gitでバージョン管理した
  * 研究段階から実用段階に移るにつれてJupyterではなくPython PackageやPySpark Applicationに移行した
  * まだ改善余地がある
  * [Luigi](https://luigi.readthedocs.io/en/stable/index.html)によるデータパイプラインの可視化
* mlflowによるモデルの管理の説明
  * 出て1年だけど、PySparkやMLlibを使う人たちの研究には役立っているみたい
* まとめ
  * Luigiでデータパイプラインを可視化してエラーをハンドリング
  * 再現性とドキュメンテーションを支援
  * mlflowもモデルの管理という意味で同じ

### 2:30 PM

#### Best Practices for Hyperparameter Tuning with MLflow

* Joseph Bradley (Databricks)
* ハイパーパラメータのチューニングは大切だが色々なコストがかかる
  * 次元の呪い
  * 非凸
  * 計算コスト
  * 直感的
* ハイパーパラメータの一般的な手法
  * 手探り（Manual Search）
  * グリッドサーチ
  * ランダムサーチ
  * Population Based Algorithms
  * Bayesian Optimization
  * Open Source Tools（写真に収めた）
* mlflowでのプラクティス
  * ハイパーパラメータ、メトリクス、タグ、アーティファクトを記録できるmlflow
  * 再現性のある環境の提供など、優れた研究環境を提供
  * 試行錯誤を記録できるので効率的なチューニングができるねって話
* この話の先
  * 並列での探索、アーリー・ストッピング、転移学習なんてのもあるね

### 3:20 PM

#### A Virtual Assistant Ecosystem for Workflow and Workplace Optimization

* Rafael Dal Zotto (HP),Franco Vieira (HP)
* 自然言語からSQLを生成する（SEQ2SQLなど）
* インテント・レコグニションやチャットボットのプラットフォームはAWS　LEX
* 割とよくあるチャットボット使った業務最適化の話
* 音声のボットもある

### 4:30 PM

#### How Graph Technology is Changing AI

* Jake Graham (Neo4j),Alicia Frame (Neo4j)
* Where do graphs matter?
  * Finance Crime Detection
  * Drug Discovery
  * Recommendations
  * Customer Segmentation
  * Cybersecurity
  * Churn Prediction
  * Predictive Meintenance
  * Search / MDM
* Labeled Property Graph
  *  世の中の多くのことを表せそう
* DeepMindもGoogleもみんな注目して研究している
* Spark Graph <-> Neo4j Morpheus <-> Neo4j Graph Platform
  * グラフの探索はSpark、グラフを構築するのはNeo4jという使い分け
* 実例の紹介
  * ナレッジグラフ→グラフ特徴量エンジニアリング→グラフネイティブ学習の順に複雑になる
  * [Knowledge Graph](https://neo4j.com/blog/nasa-critical-data-knowledge-graph/)の話
  * Drug Discoveryの話[het.io](https://het.io/)
* グラフ特徴量エンジニアリング
  * グラフの代表的特徴（in Neo４j)
      * Community Detection
      * Centrality / Importance
      * Pathfinding / Search
      * Heuristic link prediction
      * Embededdings
      * Similarity
  * 事例：金融機関での不正検知
  * 事例：ebay
  * Graph Native Learning
  * O'REILLY から本出てる 
### 5:20 PM

#### Tackling Network Bottlenecks with Hardware Accelerations: Cloud vs. On-Premise

* Yuval Degani (LinkedIn),Jithin Jose (Microsoft)
* Network BOttleneck in th wild
  * バンド幅によってのみ引き起こされるような簡単な話でもない
  * ネットワークのトラフィックはシャッフルReadが多い
  * 分散トレーニングでのモデルのトレーニングでGPUとの間のネットワークがボトルネックに
  * ストレージについてもストレージ自体が高速化しても大容量データの移動が多くなってきているのでネットワークがボトルネックに
* 主要なハードウェアアクセラレーション
  * Speeds
      * 1G, 10G, 40G, ...
  * InfiniBand
      * Hi-Performance ComputingのDefact Standard
  * RDMA : Remote Direct Memory Access
      * Direct Network Card
  * NVIDIA GPU Direct
      *  No CPU Overhead
  * Smart NIC : FPGA / ASIC Offloads
  * Smart Switch
  * NVMeOF
* Azureの話

## THURSDAY, APRIL 25

### 9:00 AM

#### Keynote E - Accelerating the Machine Learning Lifecycle with MLflow 1.0

* Matei Zaharia (Databricks),Aaron Davidson (Databricks),Greg Buehrer (Microsoft)
* 機械学習環境は複雑
* ML Lifecycle
  * data prep(need Tuning) -> training(need Tuneing) -> deployment -> raw data
  * 様々なフレームワークやライブラリがある
  * 運用やガバナンスも気にしなければならない
  * 各社様々な環境を用意
      * Facebook FBLearner
      * Uber Michelangelo
      * Google TFC
  * 限られたアルゴリズムやフレームワーク、１つの会社に依存
  * MLflowはその解決策
* MLFlowの紹介
  * 開発が盛んとSparkの状況と比較してアピール
  * Azureでも使えるよって話でマイクロソフトの人が説明
* What's next for mlflow?
  * user feedbackを元にコンポーネント開発しているよ
  * アナウンス
      * MLflow Workflows(Apache Airflowみたいなもの)
      * MLflow Model Registry
      * DatabricksでマネージドMLflowを今GAした

#### Keynote F - Winning the Audience with AI: Comcast’s Journey to Building an Agile Data and AI Platform at Scale

* Jan Neumann (Comcast),Jim Forsythe (Comcast)
* DeltaLakeをフル活用してて魅力を説明
* 運用を開始してからのライフサイクルを回すスピードに課題
* 開発環境と本番環境を繋ぐのにMLflowを使い、kubeflowを使って本番環境を提供することで解決

#### Keynote G - How Netflix Data Science Powers Global Entertainment

* Caitlin Smallwood (Netflix)
* 動画のレコメンデーションの話
* 動画一つでもその内容やロケ地、ストーリーラインなどなどで深くタグ付けされる
* 世界の様々な言語、大量に集まるデータを捌いたりとても難しいチャレンジをし続けている

#### Keynote H

* [Michael I.Jordan (UC Berkeley)](https://medium.com/syncedreview/michael-i-jordan-interview-clarity-of-thought-on-ai-ed936d0dc421)
* 現在、知能システムと呼べるものは以下
  * 生き物の脳と心
  * マーケット
* 人を模倣したAIは正しいゴールではない
* AI(aka ML) Successes
  * backend
  * human
  * pattern recoginition <- now
  * markets
* Decisions
  * シンプルな意思決定
  * コンペ式の複数の意思決定
      * みんなが良いと言うもの選ぶことが正しいとは限らない
  * 代替手段が「マーケット」の構築

### 11:00 AM

#### Introduction to TensorFlow 2.0

* Paige Bailey (Google)
* Google Colab使っている人少ない（Python使っている人って聞くと沢山いるのに）
* AI/MLの基本の説明
* 古典的機械学習
	* データは大抵綺麗に揃っていない
	* データの形式も様々
	* 特徴量エンジニアリングは大変
* 深層学習
	* 画像
	* テキスト
	* 音声
	* などなどに強い
* 自分のモデルを作りたい
	* Tendor Flow
	* Tensor Flow Hubで公開
	* Colabと連携してノートブックも公開できる
	* TFはGithubへのコミット数もSOFへの投稿も一位
	* TF.jsの紹介
* [TensorFlow 2.0 alpha](https://medium.com/tensorflow/whats-coming-in-tensorflow-2-0-d3663832e9b8)
	* tf.keras
	* Egaer extension by default
	* Remove duplicate functionality
	* Consistent, intuitive syntax axross APOs
	* などなど
	* データセット強化
* どうアップグレードする？
	* 互換モード
	* 移行ガイド
	* コンバージョンスクリプト

### 1:30 PM

#### Keynote J - Understanding the limitations of AI: When Algorithms Fail

* Timnit Gebru (Google Brain) 
* 引用されてたスライドの[動画](https://www.youtube.com/watch?v=Af2VmR-iGkY)
* Fairnessの話
* [黒人の存在感がない](https://blackinai.github.io/)
* 我々は社会問題、構造的な問題を無視できない
* 電子機器のようにデータセットのデータシートが必要では
* 

#### Keynote K

* Anitha Vijayakumar (Google)
* TensorFlow 2.0の話
* Databricks Runtime for ML では TensorFlow をサポート

#### Keynote L Deep Visual Understanding from deep learning

* Jitendra Malik (Facebook AI Research)

### 2:40 PM

#### How to Utilize MLflow and Kubernetes to Build an Enterprise ML Platform

* Nicholas Pinckernell (Comcast)
* モデルを書き換えず、簡単にトラッキングできる環境づくりがしたい
	* mlflowとk8sに行き着く
	* SageMakerって言葉も出てたけど、検討して採用しなかったってことか？
* 頻繁にモデルを更新、変更したり開発するに当たってmlflowは便利みたい¥
* 運用時のモニタリングに[Grafana](https://grafana.com/)

### 3:30 PM

#### Advanced Hyperparameter Optimization for Deep Learning with MLflow

* Maneesh Bhide (Databricks)
* HyperBand
	* 最高のモデルではなく、そこそこ良くて早いモデルが良い
	* AWSでインスタンス建ててHPをチューニングするとなると大変お金かかる
	* HyperBandを用いてあげるとそこそこ良いモデルをお安く作れる
	* Baysian + HyperBand
		* ランダムよりも効率的
		* Basian Optimizationよりも20xスピードアップ
	* Kears/TF Early Stopping
		* Baysian + HyperBandと同じではないので注意
	* ライブラリ
		* <https://github.com/automl/HpBandSter>
		* <https://github.com/automl/RoBO/blob/master/robo/fmin/fabolas.py>
	* [Hyperparameters tuned when training MemN2N and associated range values](https://devblogs.nvidia.com/optimizing-end-to-end-memory-networks-using-sigopt-gpus/)
* ユースケース毎に複数最適化する対象がある

### 4:40 PM

#### Massive-Scale Entity Resolution Using the Power of Apache Spark and Graph

* Max Melnick (Deloitte Consulting LLP)


### 5:30 PM

#### Splice Machine's use of Apache Spark and MLflow

* Gene Davis (Splice Machine)