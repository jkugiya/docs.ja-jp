---
title: .NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイする
description: .NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイする方法を説明します。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a0904b5b692e1c32ba12a685f2c3a3f7d86c2c58
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874057"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>.NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイする

このチュートリアルでは、.NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイする方法について説明します。 [Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) は、AWS でのビッグ データ フレームワークの実行を簡略化する、マネージド クラスター プラットフォームです。

このチュートリアルでは、以下の内容を学習します。

> [!div class="checklist"]
>
> * Microsoft.Spark.Worker を準備する
> * Spark .NET アプリを発行する
> * アプリを Amazon EMR Spark にデプロイする
> * アプリを実行する

> [!Note]
> AWS EMR Spark は Linux ベースです。 そのため、AWS EMR Spark へのアプリのデプロイに関心がある場合は、アプリが .NET Standard と互換性があることと、アプリのコンパイルに .NET Core コンパイラを使用していることを確認してください。

## <a name="prerequisites"></a>前提条件

開始する前に、以下を行います。

* [AWS CLI](https://aws.amazon.com/cli/) をダウンロードします。
* [install-worker.sh](https://github.com/dotnet/spark/blob/main/deployment/install-worker.sh) をお使いのローカル コンピューターにダウンロードします。 これは、後で .NET for Apache Spark の依存ファイルを Spark クラスターのワーカー ノードにコピーするために使用するヘルパー スクリプトです。

## <a name="prepare-worker-dependencies"></a>ワーカーの依存関係を準備する

**Microsoft.Spark.Worker** は、Spark クラスターの個々のワーカー ノードに存在するバックエンド コンポーネントです。 C# UDF (ユーザー定義関数) を実行する場合、.NET CLR を起動して UDF を実行する方法が Spark で認識されている必要があります。 **Microsoft.Spark.Worker** により、この機能を有効にするクラスのコレクションが Spark に提供されます。

1. お使いのクラスターにデプロイされる [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp リリースを選択します。

   たとえば、`netcoreapp3.1` を使用する `.NET for Apache Spark v1.0.0` が必要な場合は、[Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz) をダウンロードします。

2. クラスターからアクセスできる分散ファイル システム (S3 など) に、`Microsoft.Spark.Worker.<release>.tar.gz` と [install-worker.sh](https://github.com/dotnet/spark/blob/main/deployment/install-worker.sh) をアップロードします。

## <a name="prepare-your-net-for-apache-spark-app"></a>.NET for Apache Spark アプリを準備する

1. [入門](get-started.md)チュートリアルに従ってアプリをビルドします。

2. Spark .NET アプリを自己完結型として発行します。

   Linux で次のコマンドを実行します。

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

3. 発行されたファイル用に `<your app>.zip` を生成します。

   `zip` を使用して Linux で次のコマンドを実行します。

   ```bash
   zip -r <your app>.zip .
   ```

4. クラスターからアクセスできる分散ファイル システム (S3 など) に、次の項目をアップロードします。

   * `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`: この jar は、[Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet パッケージの一部として含まれており、アプリのビルド出力ディレクトリに併置されています。
   * `<your app>.zip`
   * 各 Executor の作業ディレクトリ内に配置されるファイル (依存関係ファイルや、すべてのワーカーからアクセスできる共通データなど) またはアセンブリ (アプリが依存しているユーザー定義関数またはライブラリを含む DLL など)。

## <a name="deploy-to-amazon-emr-spark"></a>Amazon EMR Spark にデプロイする

[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) は、AWS でのビッグ データ フレームワークの実行を簡略化する、マネージド クラスター プラットフォームです。

> [!NOTE]
> Amazon EMR Spark は Linux ベースです。 そのため、Amazon EMR Spark へのアプリのデプロイに関心がある場合は、アプリが .NET Standard と互換性があることと、アプリのコンパイルに [.NET Core コンパイラ](https://dotnet.microsoft.com/download)を使用していることを確認してください。

### <a name="deploy-microsoftsparkworker"></a>Microsoft.Spark.Worker をデプロイする

この手順は、クラスターの作成時にのみ必要です。

[ブートストラップ アクション](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)を使用してクラスターの作成中に、`install-worker.sh` を実行します。

AWS CLI を使用して Linux で次のコマンドを実行します。

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a>アプリを実行する

Amazon EMR Spark でアプリを実行するには、spark submit ステップと Amazon EMR ステップの 2 通りの方法があります。

### <a name="use-spark-submit"></a>spark-submit を使用する

[spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) コマンドを使用して、.NET for Apache Spark ジョブを Amazon EMR Spark に送信できます。

1. クラスター内のいずれかのノードに `ssh` で接続します。

2. `spark-submit` を実行します。

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Amazon EMR ステップを使用する

[Amazon EMR ステップ](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html)を使用して、EMR クラスターにインストールされている Spark フレームワークにジョブを送信できます。

AWS CLI を使用して Linux で次のコマンドを実行します。

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、.NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイしました。 .NET for Apache Spark のプロジェクト例については、GitHub に進んでください。

> [!div class="nextstepaction"]
> [.NET for Apache Spark サンプル](https://github.com/dotnet/spark/tree/main/examples)
