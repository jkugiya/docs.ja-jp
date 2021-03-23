---
title: .NET for Apache Spark アプリケーションから Java UDF を呼び出す
description: .NET for Apache Spark アプリケーションから Java UDF を呼び出す方法について説明します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f85ed5585c8daef0ca9a21275b8de71b2eead360
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875487"
---
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a><span data-ttu-id="6ea89-103">.NET for Apache Spark アプリケーションから Java UDF を呼び出す</span><span class="sxs-lookup"><span data-stu-id="6ea89-103">Call a Java UDF from your .NET for Apache Spark application</span></span>

<span data-ttu-id="6ea89-104">この記事では、[.NET for Apache Spark](https://github.com/dotnet/spark) アプリケーションから Java ユーザー定義関数 (UDF) を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ea89-104">In this article, you learn how to call a Java User-Defined Function (UDF) from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

1. <span data-ttu-id="6ea89-105">Java UDF を定義して jar にコンパイルする方法 - jar ファイルに UDF が既に定義されている場合、この手順は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="6ea89-105">How to define your Java UDFs and compile them into a jar - this step is not needed if you already have a UDF defined in a jar file.</span></span> <span data-ttu-id="6ea89-106">この場合、必要なのはパッケージを含む UDF 関数の完全な名前のみです。</span><span class="sxs-lookup"><span data-stu-id="6ea89-106">In which case, all you need is the full name of the UDF function including the package.</span></span>
2. <span data-ttu-id="6ea89-107">.NET for Apache Spark アプリケーションに Java UDF を登録して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6ea89-107">Register and call your Java UDF in your .NET for Apache Spark application.</span></span>

## <a name="define-and-compile-your-java-udfs"></a><span data-ttu-id="6ea89-108">Java UDF を定義してコンパイルする</span><span class="sxs-lookup"><span data-stu-id="6ea89-108">Define and compile your Java UDFs</span></span>

1. <span data-ttu-id="6ea89-109">Maven または SBT プロジェクトを作成し、次の依存関係をプロジェクト構成ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="6ea89-109">Create a Maven or SBT project and add the following dependencies into the project configuration file:</span></span>
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. <span data-ttu-id="6ea89-110">[関連するインターフェイス](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (UDF の署名に従って) を実装し、次の簡単な例で示すように、関連するパッケージをインポートして Java UDF を定義します。</span><span class="sxs-lookup"><span data-stu-id="6ea89-110">Define your Java UDF by implementing the [relevant interface](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (according to your UDF's signature) and importing the relevant package as shown below in a simple example</span></span>

    ```java
    package com.ScalaUdf.app; // Name of package where UDF is defined
    import org.apache.spark.sql.api.java.UDF1; // UDF interface to implement

    public class JavaUdf implements UDF1<Integer, Integer> { // Name of the Java UDF
        private static final int serialVersionUID = 1;
        @Override
        public Integer call(Integer num) throws Exception { // Define logic of UDF
            return (num + 5);
        }
    }
    ```

3. <span data-ttu-id="6ea89-111">プロジェクトをコンパイルしてパッケージ化し、実行可能な jar (`UdfApp-0.0.1.jar` など) を作成します。</span><span class="sxs-lookup"><span data-stu-id="6ea89-111">Compile and package your project to create and executable jar say `UdfApp-0.0.1.jar`.</span></span>

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a><span data-ttu-id="6ea89-112">.NET for Apache Spark に Java UDF を登録して呼び出す</span><span class="sxs-lookup"><span data-stu-id="6ea89-112">Register and call Java UDFs in .NET for Apache Spark</span></span>

1. <span data-ttu-id="6ea89-113">[`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API を使用して、Java UDF を Spark SQL に登録します。</span><span class="sxs-lookup"><span data-stu-id="6ea89-113">Use the [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API to register your Java UDF with Spark SQL.</span></span>
2. <span data-ttu-id="6ea89-114">[`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) 関数を使用して、UDF を SQL テーブルとして呼び出す `DataFrame` を登録します。</span><span class="sxs-lookup"><span data-stu-id="6ea89-114">Register the `DataFrame` on which you want to call your UDF as an SQL Table using the [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) function.</span></span>
3. <span data-ttu-id="6ea89-115">`SparkSession.Sql` を使用し、Spark SQL を使用してテーブル ビューで UDF を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6ea89-115">Use `SparkSession.Sql` to call the UDF on the table view using Spark SQL.</span></span>
<span data-ttu-id="6ea89-116">上記の手順を説明するための基本的な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6ea89-116">A basic example to illustrate the above steps:</span></span>

    ```csharp
    class Program
    {
        static void Main()
        {
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Scala/Java UDFs from .NET for Apache Spark")
                .GetOrCreate();
            spark.Udf().RegisterJava<int>("udfAdd5", "com.ScalaUdf.app.JavaUdf"); // Register your Java UDF as 'udfAdd5'
            DataFrame df = spark.CreateDataFrame(new int[] { 2, 5 });
            df.CreateOrReplaceTempView("numbersData"); // Create an SQL table from the DataFrame `df`
            DataFrame dfUdf = spark.Sql("SELECT udfAdd5(_1) As Result FROM numbersData"); // Call the registered UDF on the table
            dfUdf.Show();
            spark.Stop();
        }
    }
    ```

4. <span data-ttu-id="6ea89-117">以前にコンパイルした Java UDF jar を `--jars` オプションを介して渡すことで、`spark-submit` を使用してこのアプリケーションを送信します。</span><span class="sxs-lookup"><span data-stu-id="6ea89-117">Submit this application using `spark-submit` by passing the previously compiled Java UDF jar through the `--jars` option:</span></span>

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-2-4_2.11-1.0.0.jar InterRuntimeUDFs.exe
    ```

    <span data-ttu-id="6ea89-118">結果の `dfUdf` DataFrame には、`JavaUdf` で定義されているように入力列の各行に数値 5 が追加されています。</span><span class="sxs-lookup"><span data-stu-id="6ea89-118">The resultant `dfUdf` DataFrame had the number 5 added to each row of the input column as defined by `JavaUdf`:</span></span>

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a><span data-ttu-id="6ea89-119">Apache Spark で Scala または Python から .NET UDF を呼び出す</span><span class="sxs-lookup"><span data-stu-id="6ea89-119">Call .NET UDF from Scala or Python in Apache Spark</span></span>

<span data-ttu-id="6ea89-120">[sparkdotnetudf オープン ソース ツール](https://github.com/imback82/sparkdotnetudf)を使用して、Scala または Python で記述された Apache Spark アプリケーションから C# UDF を登録して呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="6ea89-120">You can also register and invoke a C# UDF from an Apache Spark application written in Scala or Python using [the sparkdotnetudf open source tool](https://github.com/imback82/sparkdotnetudf).</span></span>
