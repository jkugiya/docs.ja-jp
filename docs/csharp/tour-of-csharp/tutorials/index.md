---
title: C# の概要 - 対話型チュートリアル
description: お使いのブラウザーで C# を学習し、独自の開発環境で使用を開始します
ms.date: 02/02/2021
ms.custom: mvc
ms.openlocfilehash: ed869271cd6f4ec13f769f46d41aefae9e1dad8d
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872419"
---
# <a name="introduction-to-c"></a>C\# の概要

C# の概要に関するチュートリアルへようこそ。 これらのレッスンは、お使いのブラウザーで実行できる、対話形式のコードから開始します。 これらの対話型レッスンを開始する前に、[C# 101 ビデオ シリーズ](https://aka.ms/dotnet3-csharp)で C# の基本を学習できます。

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/CSharp-101/What-is-C/player]

最初のレッスンでは、小規模なコード スニペットを使用して C# の概念を説明します。 C# 構文の基礎や、文字列、数値、ブール値などのデータ型の使用方法を学習します。 すべて対話形式で、数分のうちにコードを記述して実行することになります。 この最初のレッスンでは、プログラミングや C# 言語について事前の知識をお持ちでないことを前提としています。

これらのチュートリアルは、さまざまな環境で試すことができます。 学習する概念は同じです。 違いは、どのエクスペリエンスをご希望かです。

- [ブラウザーの docs プラットフォームの場合](hello-world.yml): このエクスペリエンスでは、docs ページに実行可能な C# コードのウィンドウが埋め込まれます。 ブラウザーで C# コードを記述し、実行します。
- [Microsoft Learn エクスペリエンス](/learn/paths/csharp-first-steps/)。 このラーニングパスには、C# の基本を学習するいくつかのモジュールが含まれています。
- [Binder での Jupyter](https://mybinder.org/v2/gh/dotnet/try-samples/master?filepath=hello-csharp%2Fhello-world.ipynb)。 Binder の Jupyter Notebook で C# コードを試すことができます。
- [ローカル コンピューター](numbers-in-csharp-local.md)。 .NET Core SDK をオンラインで探索した後、お使いのマシンに[ダウンロード](https://dotnet.microsoft.com/download)して、プログラムをビルドすることができます。

Hello World レッスンに続くすべての入門用チュートリアルは、オンライン ブラウザー エクスペリエンスを使用するか[独自のローカル開発環境](local-environment.md)で使用できます。 各チュートリアルの最後に、次のレッスンをオンラインまたは自分のコンピューターのどちらで続行するかを決定します。 環境を設定し、ご利用のコンピューターで次のチュートリアルを続行するためのリンクがあります。

## <a name="hello-world"></a>[Hello World](hello-world.yml)

「[Hello World](hello-world.yml)」チュートリアルでは、最も基本的な C# プログラムを作成します。 `string` 型とテキストの操作方法について学習します。 [Microsoft Learn](/learn/paths/csharp-first-steps/) または [Binder での Jupyter](https://mybinder.org/v2/gh/dotnet/try-samples/master?filepath=hello-csharp%2Fhello-world.ipynb) でもパスを使用することができます。

## <a name="numbers-in-c"></a>[C# における数値](numbers-in-csharp.yml)

[C# における数値](numbers-in-csharp.yml)チュートリアルでは、コンピューターに数値が格納されるしくみとさまざまな数値型で計算するしくみが紹介されます。 丸め処理の基礎と、C# で算術演算を実行する方法を学習します。 このチュートリアルも[ご利用のコンピューターでローカルで実行するために](numbers-in-csharp-local.md)使用できます。

このチュートリアルは、[Hello world](hello-world.yml) レッスンを修了していることが前提条件となります。

## <a name="branches-and-loops"></a>[分岐とループ](branches-and-loops.yml)

[分岐とループ](branches-and-loops.yml) チュートリアルでは、変数に格納されている値に基づき、コード実行のさまざまなパスを選択することの基本を説明します。 プログラムが決定して異なる操作を選択する上で基本となる、制御フローの基礎を学習します。 このチュートリアルも[ご利用のコンピューターでローカルで実行するために](branches-and-loops-local.md)使用できます。

このチュートリアルは、[Hello world](hello-world.yml) レッスンと [C# における数値](numbers-in-csharp.yml)レッスンを修了していることが前提条件となります。

## <a name="list-collection"></a>[リスト コレクション](list-collection.yml)

「[リスト コレクション](list-collection.yml)」レッスンでは、データのシーケンスを格納するリスト コレクション型について説明します。 項目の追加方法や削除方法、項目の検索方法、リストを並べ替える方法を学習します。 さまざまな種類のリストを紹介します。 このチュートリアルも[ご利用のコンピューターでローカルで実行するために](arrays-and-collections.md)使用できます。

このチュートリアルは、上に挙げたレッスンを修了していることが前提条件となります。

## <a name="101-linq-samples"></a>[101 個の LINQ サンプル](https://github.com/dotnet/try-samples/tree/main/101-linq-samples)

このサンプルには [dotnet-try](https://github.com/dotnet/try/blob/main/README.md#setup) グローバルツールが必要です。 ツールをインストールし、[try-samples](https://github.com/dotnet/try-samples) リポジトリを複製すると、対話形式で実行できる一連の 101 個のサンプルを通じて、統合言語クエリ (LINQ) を学習できます。 さまざまな方法でデータ シーケンスのクエリ、探索、および変換を行うことができます。
