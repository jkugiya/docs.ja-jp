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
# <a name="write-and-call-udfs-in-net-for-apache-spark-interactive-environments"></a><span data-ttu-id="9491e-103">.NET for Apache Spark 対話型環境で UDF を記述して呼び出す</span><span class="sxs-lookup"><span data-stu-id="9491e-103">Write and call UDFs in .NET for Apache Spark interactive environments</span></span>

<span data-ttu-id="9491e-104">この記事では、.NET for Apache Spark 対話型環境でユーザー定義関数 (UDF) を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9491e-104">In this article, you will learn how to use user-defined functions (UDFs) in a .NET for Apache Spark interactive environment.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9491e-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="9491e-105">Prerequisites</span></span>

1. <span data-ttu-id="9491e-106">[.NET Interactive](https://github.com/dotnet/interactive) をインストールする</span><span class="sxs-lookup"><span data-stu-id="9491e-106">Install [.NET Interactive](https://github.com/dotnet/interactive)</span></span>
2. <span data-ttu-id="9491e-107">[Jupyter Lab](https://jupyter.org/) をインストールする</span><span class="sxs-lookup"><span data-stu-id="9491e-107">Install [Jupyter lab](https://jupyter.org/)</span></span>

## <a name="net-for-apache-spark-interactive-experience"></a><span data-ttu-id="9491e-108">.NET for Apache 対話型エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="9491e-108">.NET for Apache Spark Interactive experience</span></span>

<span data-ttu-id="9491e-109">[.Net for Apache Spark](https://github.com/dotnet/spark) では [.NET Interactive](https://devblogs.microsoft.com/dotnet/net-interactive-is-here-net-notebooks-preview-2/) を使用して、Spark 内の対話型エクスペリエンスに対する .NET サポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="9491e-109">[.NET for Apache Spark](https://github.com/dotnet/spark) uses [.NET Interactive](https://devblogs.microsoft.com/dotnet/net-interactive-is-here-net-notebooks-preview-2/) to provide .NET support for interactive experience inside Spark.</span></span> <span data-ttu-id="9491e-110">Jupyter Notebook で .NET Interactive を試すように環境を設定する方法については、[.NET Interactive リポジトリ](https://github.com/dotnet/interactive)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9491e-110">To understand how to set up the environment to try .NET Interactive with Jupyter notebooks, see the [.NET Interactive repository](https://github.com/dotnet/interactive).</span></span>

<span data-ttu-id="9491e-111">また、[.NET for Apache Spark での UDF のシリアル化に関するこの記事](udf-guide.md)を参照して、UDF の詳細と、それが .NET for Apache Spark でどのようにシリアル化されるかについて理解することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9491e-111">Also, it is recommended to go through [this article about UDF serialization in .NET for Apache Spark](udf-guide.md) to understand what UDFs are and how they are serialized in .NET for Apache Spark.</span></span>
<span data-ttu-id="9491e-112">このガイドでは、Jupyter Notebook を使用して、対話型エクスペリエンスで UDF を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9491e-112">This guide uses Jupyter Notebooks to illustrate how to use UDFs in an interactive experience.</span></span>

## <a name="define-a-udf-in-net-interactive"></a><span data-ttu-id="9491e-113">.NET Interactive で UDF を定義する</span><span class="sxs-lookup"><span data-stu-id="9491e-113">Define a UDF in .NET Interactive</span></span>

<span data-ttu-id="9491e-114">対話型エクスペリエンスでは、セルは、[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) の 1 回の反復処理の一部として送信されるコード スニペットと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="9491e-114">In the interactive experience, a cell can be thought of as the code snippet being submitted as part of one iteration of the [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop).</span></span> <span data-ttu-id="9491e-115">たとえば、次のノートブックを確認して、その意味を理解してください。</span><span class="sxs-lookup"><span data-stu-id="9491e-115">For example, take a look at the following notebook to understand what that means:</span></span>

![Jupyter Notebook のセル](./media/dotnet-interactive/dotnet-interactive-cells.png)

<span data-ttu-id="9491e-117">赤い矢印でマークされている各ブロックは、1 つのセル、または Spark へのコードの 1 回の送信です。</span><span class="sxs-lookup"><span data-stu-id="9491e-117">Each of those blocks marked by the red arrow is one cell, or one submission of code to Spark.</span></span> <span data-ttu-id="9491e-118">ここでは、カスタムのユーザー定義オブジェクトを参照する UDF を定義するときに、参照するオブジェクトが定義されているのと同じセルに UDF を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9491e-118">Now when defining a UDF that references a custom user-defined object, it is required that the UDF be defined in the same cell where the object it references is defined.</span></span> <span data-ttu-id="9491e-119">その例を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="9491e-119">Let's look at what that looks like as an example:</span></span>

![UDF の操作](./media/dotnet-interactive/working-udf.png)

## <a name="call-a-udf-on-a-dataframe"></a><span data-ttu-id="9491e-121">DataFrame で UDF を呼び出す</span><span class="sxs-lookup"><span data-stu-id="9491e-121">Call a UDF on a DataFrame</span></span>

<span data-ttu-id="9491e-122">以前に定義された UDF を `DataFrame` で呼び出すときは、前の例で示したように、呼び出しの前に、以前に送信されたセルに UDF が定義されていることを確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="9491e-122">When calling a previously defined UDF on a `DataFrame` it is important to make sure the UDF is defined in a previously submitted cell, before calling it, as can be seen in the previous example.</span></span>

<span data-ttu-id="9491e-123">次に、UDF が定義されているのと同じセルで UDF を呼び出すとどうなるかを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="9491e-123">Now let's see what happens if we call the UDF in the same cell where it is defined.</span></span>

![UDF 呼び出しの失敗](./media/dotnet-interactive/udf_fails.png)

<span data-ttu-id="9491e-125">強調表示されている上のエラーは、UDF アセンブリを DataFrame で呼び出す前に最初にコンパイルしてワーカーに配布する必要があるために発生しました。</span><span class="sxs-lookup"><span data-stu-id="9491e-125">The above highlighted error is because the UDF assemblies need to first be compiled and shipped to the workers before it can be called on a DataFrame.</span></span>

<span data-ttu-id="9491e-126">.NET for Apache Spark 対話型エクスペリエンス ([Azure Synapse Notebooks](/azure/synapse-analytics/spark/apache-spark-development-using-notebooks) など) で UDF を実装するときは、いくつかの重要な点に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9491e-126">These are a few important things to keep in mind while implementing UDFs in .NET for Apache Spark interactive experience (such as [Azure Synapse Notebooks](/azure/synapse-analytics/spark/apache-spark-development-using-notebooks)).</span></span>

## <a name="faqs"></a><span data-ttu-id="9491e-127">FAQ</span><span class="sxs-lookup"><span data-stu-id="9491e-127">FAQs</span></span>

1. <span data-ttu-id="9491e-128">**カスタムのユーザー定義オブジェクトを参照する UDF でエラーがスローされるのはなぜですか`Type Submission#_ is not marked as serializable`。**</span><span class="sxs-lookup"><span data-stu-id="9491e-128">**Why does my UDF referencing a custom user-defined object throw the error `Type Submission#_ is not marked as serializable`?**</span></span>
    <span data-ttu-id="9491e-129">.NET Interactive により、送信される各セルを一意に識別するために、セル送信番号のラッパー クラスでこれらの各セルがラップされます。</span><span class="sxs-lookup"><span data-stu-id="9491e-129">.NET Interactive wraps each of these cells with a wrapper class of the cell submission number, to uniquely identify each cell being submitted.</span></span> <span data-ttu-id="9491e-130">[このガイド](udf-guide.md)で詳しく説明しているように、カスタム オブジェクトを参照する UDF がシリアル化されると、そのターゲットもシリアル化の対象となります。.NET Interactive の場合、これはカスタム オブジェクトが定義されているセルのラッパー クラスでラップされます。</span><span class="sxs-lookup"><span data-stu-id="9491e-130">Now as explained in detail in [this guide](udf-guide.md), when a UDF that references a custom object is being serialized its target is also picked up for serialization, which in the case of .NET Interactive gets wrapped by the wrapper class of the cell where the custom object is defined.</span></span>
    <span data-ttu-id="9491e-131">次に、このことがノートブックの UDF 定義にどのように影響するかを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="9491e-131">Now let's see how that affects our UDF definition in the notebook:</span></span>

    ![UDF のシリアル化エラー](./media/dotnet-interactive/udf-serialization-error.png)

    <span data-ttu-id="9491e-133">`udf2_fails` の場合と同様に、型 `Submission#7` がシリアル化可能としてマークされていないことを示すエラー メッセージが表示されます。これは、実行時に生成されるために `Serializable` としてマークされていない、セルに定義されているすべてのオブジェクトが、NET Interactive によって `Submission#` クラスでラップされるためです。</span><span class="sxs-lookup"><span data-stu-id="9491e-133">As can be seen in the case of `udf2_fails`, we see the error message that says Type `Submission#7` is not marked as serializable, this is because .NET Interactive wraps every object defined in a cell with its `Submission#` class, which is generated on the fly and hence is not marked as `Serializable`.</span></span>

    <span data-ttu-id="9491e-134">したがって、**カスタム オブジェクトを参照する UDF は、そのオブジェクトと同じセルに定義されている必要があります**。</span><span class="sxs-lookup"><span data-stu-id="9491e-134">For this reason, it is **required that a UDF referencing a custom object is defined in the same cell as that object**.</span></span>

2. <span data-ttu-id="9491e-135">**.NET Interactive でブロードキャスト変数が機能しないのはなぜですか。**</span><span class="sxs-lookup"><span data-stu-id="9491e-135">**Why don't Broadcast Variables work with .NET Interactive?**</span></span>
    <span data-ttu-id="9491e-136">前に説明した理由により、ブロードキャスト変数は .NET Interactive では機能しません。</span><span class="sxs-lookup"><span data-stu-id="9491e-136">For the reasons explained previously, broadcast variables don't work with .NET Interactive.</span></span> <span data-ttu-id="9491e-137">[ブロードキャスト変数に関するこのガイド](broadcast-guide.md)を参照して、ブロードキャスト変数の詳細とその使用方法について理解を深めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9491e-137">It is a good idea to go through [this guide on broadcast variables](broadcast-guide.md) to get a deeper understanding of what broadcast variables are and how to use them.</span></span> <span data-ttu-id="9491e-138">ブロードキャスト変数が対話型のシナリオでは機能しないのは、セルに定義されている各オブジェクトにセル送信クラスを追加する .NET Interactive の設計によるものです。これは、シリアル化可能としてマークされていないため、前に示したものと同じ例外で失敗します。</span><span class="sxs-lookup"><span data-stu-id="9491e-138">The reason broadcast variables don't work with interactive scenarios is because of .NET interactive's design of appending each object defined in a cell with its cell submission class, which since is not marked serializable, fails with the same exception as shown previously.</span></span>
    <span data-ttu-id="9491e-139">次の例でもう少し掘り下げてみましょう。</span><span class="sxs-lookup"><span data-stu-id="9491e-139">Let's dive a little deeper with the following example:</span></span>

    ![ブロードキャスト変数の失敗](./media/dotnet-interactive/broadcast-fails.png)

    <span data-ttu-id="9491e-141">前のセクションで推奨されているように、UDF とそれが参照するオブジェクト (この場合はブロードキャスト変数) の両方を同じセルに定義しても、`Microsoft.Spark.Sql.Session` がシリアル化可能としてマークされていないことを示す `SerializationException` エラーが引き続き表示されます。</span><span class="sxs-lookup"><span data-stu-id="9491e-141">As recommended in the previous sections, we define both the UDF and the object it is referencing (broadcast variable in this case) in the same cell, but we still see the `SerializationException` error complaining about `Microsoft.Spark.Sql.Session` not being marked as serializable.</span></span> <span data-ttu-id="9491e-142">これは、コンパイラによってブロードキャスト変数オブジェクト `bv` のシリアル化が試行されたときに、その名前に [`SparkSession`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) オブジェクト `spark` が追加されることが認識され、これをシリアル化可能としてマークする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="9491e-142">This is because when the compiler tries to serialize the broadcast variable object `bv`, it finds its name to be appended with [`SparkSession`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) object `spark`, which it requires to be marked as serializable.</span></span> <span data-ttu-id="9491e-143">このことは、このセル送信のデコンパイル アセンブリを参照することで、より簡単に示すことができます。</span><span class="sxs-lookup"><span data-stu-id="9491e-143">This can be demonstrated with more ease by taking a peek at the decompiled assembly of this cell submission:</span></span>

    ![デコンパイル アセンブリ コード](./media/dotnet-interactive/decompiledAssembly.png)

    <span data-ttu-id="9491e-145">[`SparkSession`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) クラスを `[Serializable]` としてマークすると機能するようになりますが、これは理想的な解決策ではありません。SparkSession オブジェクトのシリアル化をユーザーに許可すると、望ましくない不可解な動作が生じる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="9491e-145">If we mark the [`SparkSession`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) class as `[Serializable]`, we can get this to work, but this is not an ideal solution as we don't want to give the user the ability to serialize a SparkSession object, as that could lead to some weird, undesirable behavior.</span></span> <span data-ttu-id="9491e-146">これは[既知の問題](https://github.com/dotnet/spark/issues/619)であり、今後のバージョンで解決される予定です。</span><span class="sxs-lookup"><span data-stu-id="9491e-146">This is a [known issue](https://github.com/dotnet/spark/issues/619) and will be resolved in future versions.</span></span>
