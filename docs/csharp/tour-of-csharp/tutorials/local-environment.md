---
title: C# の概要 - 開発ツールに対する理解を深める
description: この記事では、コンピューターで C# アプリケーションと .NET アプリケーションを開発するためのツールの基礎を提供します。
ms.date: 02/02/2021
ms.openlocfilehash: 72116154126b0a97fffe417b2807576b1d9689df
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100626631"
---
# <a name="set-up-your-local-environment"></a>ローカル環境を設定する

コンピューターでチュートリアルを実行する最初の手順は、開発環境を設定することです。 次の方法のいずれかを選択します。

* .NET CLI と好みのテキストまたはコード エディターを使用するには、.NET のチュートリアル「[Hello World を 10 分で](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)」を参照してください。 このチュートリアルでは、Windows、Linux、または macOS で開発環境を設定するための手順について説明しています。
* .NET CLI と Visual Studio Code を使用するには、[.NET SDK](https://dotnet.microsoft.com/download) と [Visual Studio Code](https://code.visualstudio.com/) をインストールします。
* Visual Studio 2019 を使用するには、「[チュートリアル: Visual Studio でシンプルな C# コンソール アプリを作成する](/visualstudio/get-started/csharp/tutorial-console)」を参照してください。

## <a name="basic-application-development-flow"></a>アプリケーション開発の基本フロー

これらのチュートリアルの手順は、.NET CLI を使用してアプリケーションを作成、構築、および実行していることを前提としています。 次のコマンドを使用します。

* [`dotnet new`](../../../core/tools/dotnet-new.md) を使用して、アプリケーションを作成します。 このコマンドによってアプリケーションに必要なファイルとアセットが生成されます。 C# の概要チュートリアルではすべて、アプリケーションの種類 `console` が使用されます。 基本を習得したら、他の種類のアプリケーションに応用できます。
* [`dotnet build`](../../../core/tools/dotnet-build.md) を使用して、実行可能ファイルをビルドします。
* [`dotnet run`](../../../core/tools/dotnet-run.md) を使用して、実行可能ファイルを実行します。

これらのチュートリアルに Visual Studio 2019 を使用している場合、チュートリアルでこれらの CLI コマンドのいずれかを実行するように指示されたら、次の Visual Studio のメニューを選択します。

* **[ファイル]**  >  **[新規]**  >  **[プロジェクト]** を選択して、アプリケーションを作成します。
* **[ビルド]**  >   **[ソリューションのビルド]** を選択して、実行可能ファイルをビルドします。
* **[デバッグ]**  >  **[デバッグなしで開始]** を選択して、実行可能ファイルを実行します。

## <a name="pick-your-tutorial"></a>チュートリアルを選択する

最初に次のいずれかのチュートリアルを選択します。

## <a name="numbers-in-c"></a>C\# における数値

[C# における数値](numbers-in-csharp-local.md)チュートリアルでは、コンピューターに数値が格納されるしくみとさまざまな数値型で計算するしくみが紹介されます。 丸めの基本と C# を使用した数学計算方法を学習します。

このチュートリアルでは、[Hello world](hello-world.yml) レッスンを修了していることが前提条件となります。

## <a name="branches-and-loops"></a>分岐とループ

[分岐とループ](branches-and-loops-local.md) チュートリアルでは、変数に格納されている値に基づき、コード実行のさまざまなパスを選択することの基本を説明します。 プログラムが決定して異なる操作を選択する上で基本となる、制御フローの基礎を学習します。

このチュートリアルでは、[Hello world](hello-world.yml) レッスンと [C# における数値](numbers-in-csharp-local.md)レッスンを修了していることが前提条件となります。

## <a name="list-collection"></a>リスト コレクション

「[リスト コレクション](arrays-and-collections.md)」レッスンでは、データのシーケンスを格納するリスト コレクション型について説明します。 項目の追加方法や削除方法、項目の検索方法、リストを並べ替える方法を学習します。 さまざまな種類のリストを紹介します。

このチュートリアルでは、上に挙げたレッスンを終了していることを前提としています。
