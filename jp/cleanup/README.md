# クリーンアップ

ここでは，本ワークショップで作成したリソース群の削除方法について説明します．このワークショップを実行した後は，忘れずに**必ず**リソースを削除してください．そうしないと，**継続して課金が発生し続けてしまいます**．

## Amazon ES

1. AWS マネジメントコンソールの画面左上にある [サービス] を押してサービス一覧を表示させ，**[Elasticsearch Service]** を選択してください
2. 表示させたら，一覧にある  **"workshop-esdomain"** を選択して，**[アクション]** ボタンの **[ドメインの削除]** を選択します．ポップアップが表示されたら，チェックボックスを選択して **[削除]** します

## Firehose

1. AWS マネジメントコンソールの画面左上にある [サービス] を押してサービス一覧を表示させ，**[Kinesis]** を選択してください
2. inesis Firehose 配信ストリームにある **"workshop-firehose"** を選択して，**[Delete delivery stream]** ボタンを押します．ポップアップが表示されたら **[Delete delivery stream]** を押して削除を確定させます
3. 続いて，Amazon ES に挿入する際にエラーになったレコードを保存するための S3 バケットを削除します．AWS マネジメントコンソールの画面左上にある [サービス] を押してサービス一覧を表示させ，**[S3]** を選択してください
4. S3 バケット一覧から，**"workshop-firehose-backup-YYYYMMDD-YOURNAME"** のチェックボックスを選択して，上部メニューにある **[削除]** ボタンを押します．ポップアップでバケット名を入力してから，**[確認]** を押して削除を確定します

## Kinesis Data Generator

1. AWS マネジメントコンソールの画面左上にある [サービス] を押してサービス一覧を表示させ，**[CloudFormation]** を選択してください
2. 画面右上のリージョン選択画面を **[オレゴン]** に変更してください
3. 一覧から **"Kinesis-Data-Generator-Cognito-User"** を選択して，**[削除]** ボタンを押し，ポップアップの **[スタックの削除]** を選択します
4. 続いて AWS マネジメントコンソールの画面左上にある [サービス] を押してサービス一覧を表示させ，**[Cognito]** を選択してください
5. **[ユーザープールの管理]** を押して一覧を表示させ，**[Kinesis Data-Generator Users]** を選択して，右上の **[プールの削除]** から削除を行います
6. 次に左上の **[フェデレーテッドアイデンティティ]** を押して，**[KinesisDataGeneratorUsers]** を選択します．メニュー下側の [ID プールの削除] メニューを表示させ，**[ID プールの削除]** ボタンを押し，**[プールの削除]** で削除を確定します

## Amazon SNS

1. AWS マネジメントコンソールの画面左上にある [サービス] を押してサービス一覧を表示させ，**[Simple Nortification Service]** を選択してください
2. 左側メニューから **[トピック]** を押し，"**amazon_es_alert**" を選択して **[削除]** ボタンを押して削除を実行します．ポップアップで **"これを削除"** と入力して **[削除]** を確定させます
3. 左側メニューから **[サブスクリプション]** を押し， **"amazon_es_alert"** トピックに対するサブスクリプションを選択し，**[削除]** します
4. 最後に，Amazon ES から SNS トピックに通知を送るための IAM ロールを削除します．AWS マネジメントコンソールの画面左上にある [サービス] を押してサービス一覧を表示させ，**[IAM]** を選択してください
5. 左側メニューから **[ロール]** を押し，検索窓に **"amazones_sns_alert_role"** と入力して **"amazones_sns_alert_role"** を表示させ，**[ロールの削除]** ボタンから削除します
6. 同様に左側メニューから **[ポリシー]** を押し，検索窓に **"amazones_sns_alert_policy"** と入力して **"amazones_sns_alert_policy"** を表示させ，**[ポリシーアクション]** ボタンから **[削除]** を押して削除します

以上で後片付けは終了です．



