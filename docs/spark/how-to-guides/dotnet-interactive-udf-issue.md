---
title: .NET for Apache Spark 対話型環境で、UDF を記述して呼び出します。
description: .NET for Apache Spark 対話型シェルで UDF を記述して呼び出す方法について説明します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: c29c3a9f6269a342d1051d6d979a4e3adb42da02
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875552"
---
# <a name="write-and-call-udfs-in-net-for-apache-spark-interactive-environments"></a>.NET for Apache Spark 対話型環境で UDF を記述して呼び出す

この記事では、.NET for Apache Spark 対話型環境でユーザー定義関数 (UDF) を使用する方法について説明します。

## <a name="prerequisites"></a>前提条件

1. [.NET Interactive](https://github.com/dotnet/interactive) をインストールする
2. [Jupyter Lab](https://jupyter.org/) をインストールする

## <a name="net-for-apache-spark-interactive-experience"></a>.NET for Apache 対話型エクスペリエンス

[.Net for Apache Spark](https://github.com/dotnet/spark) では [.NET Interactive](https://devblogs.microsoft.com/dotnet/net-interactive-is-here-net-notebooks-preview-2/) を使用して、Spark 内の対話型エクスペリエンスに対する .NET サポートが提供されます。 Jupyter Notebook で .NET Interactive を試すように環境を設定する方法については、[.NET Interactive リポジトリ](https://github.com/dotnet/interactive)を参照してください。

また、[.NET for Apache Spark での UDF のシリアル化に関するこの記事](udf-guide.md)を参照して、UDF の詳細と、それが .NET for Apache Spark でどのようにシリアル化されるかについて理解することをお勧めします。
このガイドでは、Jupyter Notebook を使用して、対話型エクスペリエンスで UDF を使用する方法について説明します。

## <a name="define-a-udf-in-net-interactive"></a>.NET Interactive で UDF を定義する

対話型エクスペリエンスでは、セルは、[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) の 1 回の反復処理の一部として送信されるコード スニペットと考えることができます。 たとえば、次のノートブックを確認して、その意味を理解してください。

![Jupyter Notebook のセル](./media/dotnet-interactive/dotnet-interactive-cells.png)

赤い矢印でマークされている各ブロックは、1 つのセル、または Spark へのコードの 1 回の送信です。 ここでは、カスタムのユーザー定義オブジェクトを参照する UDF を定義するときに、参照するオブジェクトが定義されているのと同じセルに UDF を定義する必要があります。 その例を見てみましょう。

![UDF の操作](./media/dotnet-interactive/working-udf.png)

## <a name="call-a-udf-on-a-dataframe"></a>DataFrame で UDF を呼び出す

以前に定義された UDF を `DataFrame` で呼び出すときは、前の例で示したように、呼び出しの前に、以前に送信されたセルに UDF が定義されていることを確認することが重要です。

次に、UDF が定義されているのと同じセルで UDF を呼び出すとどうなるかを見てみましょう。

![UDF 呼び出しの失敗](./media/dotnet-interactive/udf_fails.png)

強調表示されている上のエラーは、UDF アセンブリを DataFrame で呼び出す前に最初にコンパイルしてワーカーに配布する必要があるために発生しました。

.NET for Apache Spark 対話型エクスペリエンス ([Azure Synapse Notebooks](/azure/synapse-analytics/spark/apache-spark-development-using-notebooks) など) で UDF を実装するときは、いくつかの重要な点に注意する必要があります。

## <a name="faqs"></a>FAQ

1. **カスタムのユーザー定義オブジェクトを参照する UDF でエラーがスローされるのはなぜですか`Type Submission#_ is not marked as serializable`。**
    .NET Interactive により、送信される各セルを一意に識別するために、セル送信番号のラッパー クラスでこれらの各セルがラップされます。 [このガイド](udf-guide.md)で詳しく説明しているように、カスタム オブジェクトを参照する UDF がシリアル化されると、そのターゲットもシリアル化の対象となります。.NET Interactive の場合、これはカスタム オブジェクトが定義されているセルのラッパー クラスでラップされます。
    次に、このことがノートブックの UDF 定義にどのように影響するかを見てみましょう。

    ![UDF のシリアル化エラー](./media/dotnet-interactive/udf-serialization-error.png)

    `udf2_fails` の場合と同様に、型 `Submission#7` がシリアル化可能としてマークされていないことを示すエラー メッセージが表示されます。これは、実行時に生成されるために `Serializable` としてマークされていない、セルに定義されているすべてのオブジェクトが、NET Interactive によって `Submission#` クラスでラップされるためです。

    したがって、**カスタム オブジェクトを参照する UDF は、そのオブジェクトと同じセルに定義されている必要があります**。

2. **.NET Interactive でブロードキャスト変数が機能しないのはなぜですか。**
    前に説明した理由により、ブロードキャスト変数は .NET Interactive では機能しません。 [ブロードキャスト変数に関するこのガイド](broadcast-guide.md)を参照して、ブロードキャスト変数の詳細とその使用方法について理解を深めることをお勧めします。 ブロードキャスト変数が対話型のシナリオでは機能しないのは、セルに定義されている各オブジェクトにセル送信クラスを追加する .NET Interactive の設計によるものです。これは、シリアル化可能としてマークされていないため、前に示したものと同じ例外で失敗します。
    次の例でもう少し掘り下げてみましょう。

    ![ブロードキャスト変数の失敗](./media/dotnet-interactive/broadcast-fails.png)

    前のセクションで推奨されているように、UDF とそれが参照するオブジェクト (この場合はブロードキャスト変数) の両方を同じセルに定義しても、`Microsoft.Spark.Sql.Session` がシリアル化可能としてマークされていないことを示す `SerializationException` エラーが引き続き表示されます。 これは、コンパイラによってブロードキャスト変数オブジェクト `bv` のシリアル化が試行されたときに、その名前に [`SparkSession`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) オブジェクト `spark` が追加されることが認識され、これをシリアル化可能としてマークする必要があるためです。 このことは、このセル送信のデコンパイル アセンブリを参照することで、より簡単に示すことができます。

    ![デコンパイル アセンブリ コード](./media/dotnet-interactive/decompiledAssembly.png)

    [`SparkSession`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) クラスを `[Serializable]` としてマークすると機能するようになりますが、これは理想的な解決策ではありません。SparkSession オブジェクトのシリアル化をユーザーに許可すると、望ましくない不可解な動作が生じる可能性があるためです。 これは[既知の問題](https://github.com/dotnet/spark/issues/619)であり、今後のバージョンで解決される予定です。
