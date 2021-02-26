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
# <a name="set-up-your-local-environment"></a><span data-ttu-id="f1303-103">ローカル環境を設定する</span><span class="sxs-lookup"><span data-stu-id="f1303-103">Set up your local environment</span></span>

<span data-ttu-id="f1303-104">コンピューターでチュートリアルを実行する最初の手順は、開発環境を設定することです。</span><span class="sxs-lookup"><span data-stu-id="f1303-104">The first step in running a tutorial on your machine is to set up a development environment.</span></span> <span data-ttu-id="f1303-105">次の方法のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f1303-105">Choose one of the following alternatives:</span></span>

* <span data-ttu-id="f1303-106">.NET CLI と好みのテキストまたはコード エディターを使用するには、.NET のチュートリアル「[Hello World を 10 分で](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1303-106">To use the .NET CLI and your choice of text or code editor, see the .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span></span> <span data-ttu-id="f1303-107">このチュートリアルでは、Windows、Linux、または macOS で開発環境を設定するための手順について説明しています。</span><span class="sxs-lookup"><span data-stu-id="f1303-107">The tutorial has instructions for setting up a development environment on Windows, Linux, or macOS.</span></span>
* <span data-ttu-id="f1303-108">.NET CLI と Visual Studio Code を使用するには、[.NET SDK](https://dotnet.microsoft.com/download) と [Visual Studio Code](https://code.visualstudio.com/) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="f1303-108">To use the .NET CLI and Visual Studio Code, install the [.NET SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>
* <span data-ttu-id="f1303-109">Visual Studio 2019 を使用するには、「[チュートリアル: Visual Studio でシンプルな C# コンソール アプリを作成する](/visualstudio/get-started/csharp/tutorial-console)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1303-109">To use Visual Studio 2019, see [Tutorial: Create a simple C# console app in Visual Studio](/visualstudio/get-started/csharp/tutorial-console).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="f1303-110">アプリケーション開発の基本フロー</span><span class="sxs-lookup"><span data-stu-id="f1303-110">Basic application development flow</span></span>

<span data-ttu-id="f1303-111">これらのチュートリアルの手順は、.NET CLI を使用してアプリケーションを作成、構築、および実行していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="f1303-111">The instructions in these tutorials assume that you're using the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="f1303-112">次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1303-112">You'll use the following commands:</span></span>

* <span data-ttu-id="f1303-113">[`dotnet new`](../../../core/tools/dotnet-new.md) を使用して、アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1303-113">[`dotnet new`](../../../core/tools/dotnet-new.md) creates an application.</span></span> <span data-ttu-id="f1303-114">このコマンドによってアプリケーションに必要なファイルとアセットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f1303-114">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="f1303-115">C# の概要チュートリアルではすべて、アプリケーションの種類 `console` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f1303-115">The introduction to C# tutorials all use the `console` application type.</span></span> <span data-ttu-id="f1303-116">基本を習得したら、他の種類のアプリケーションに応用できます。</span><span class="sxs-lookup"><span data-stu-id="f1303-116">Once you've got the basics, you can expand to other application types.</span></span>
* <span data-ttu-id="f1303-117">[`dotnet build`](../../../core/tools/dotnet-build.md) を使用して、実行可能ファイルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="f1303-117">[`dotnet build`](../../../core/tools/dotnet-build.md) builds the executable.</span></span>
* <span data-ttu-id="f1303-118">[`dotnet run`](../../../core/tools/dotnet-run.md) を使用して、実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="f1303-118">[`dotnet run`](../../../core/tools/dotnet-run.md) runs the executable.</span></span>

<span data-ttu-id="f1303-119">これらのチュートリアルに Visual Studio 2019 を使用している場合、チュートリアルでこれらの CLI コマンドのいずれかを実行するように指示されたら、次の Visual Studio のメニューを選択します。</span><span class="sxs-lookup"><span data-stu-id="f1303-119">If you use Visual Studio 2019 for these tutorials, you'll choose a Visual Studio menu selection when a tutorial directs you to run one of these CLI commands:</span></span>

* <span data-ttu-id="f1303-120">**[ファイル]**  >  **[新規]**  >  **[プロジェクト]** を選択して、アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1303-120">**File** > **New** > **Project** creates an application.</span></span>
* <span data-ttu-id="f1303-121">**[ビルド]**  >   **[ソリューションのビルド]** を選択して、実行可能ファイルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="f1303-121">**Build** >  **Build Solution** builds the executable.</span></span>
* <span data-ttu-id="f1303-122">**[デバッグ]**  >  **[デバッグなしで開始]** を選択して、実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="f1303-122">**Debug** > **Start Without Debugging** runs the executable.</span></span>

## <a name="pick-your-tutorial"></a><span data-ttu-id="f1303-123">チュートリアルを選択する</span><span class="sxs-lookup"><span data-stu-id="f1303-123">Pick your tutorial</span></span>

<span data-ttu-id="f1303-124">最初に次のいずれかのチュートリアルを選択します。</span><span class="sxs-lookup"><span data-stu-id="f1303-124">You can start with any of the following tutorials:</span></span>

## <a name="numbers-in-c"></a><span data-ttu-id="f1303-125">C\# における数値</span><span class="sxs-lookup"><span data-stu-id="f1303-125">Numbers in C\#</span></span>

<span data-ttu-id="f1303-126">[C# における数値](numbers-in-csharp-local.md)チュートリアルでは、コンピューターに数値が格納されるしくみとさまざまな数値型で計算するしくみが紹介されます。</span><span class="sxs-lookup"><span data-stu-id="f1303-126">In the [Numbers in C#](numbers-in-csharp-local.md) tutorial, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="f1303-127">丸めの基本と C# を使用した数学計算方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="f1303-127">You'll learn the basics of rounding and how to perform mathematical calculations using C#.</span></span>

<span data-ttu-id="f1303-128">このチュートリアルでは、[Hello world](hello-world.yml) レッスンを修了していることが前提条件となります。</span><span class="sxs-lookup"><span data-stu-id="f1303-128">This tutorial assumes that you have finished the [Hello world](hello-world.yml) lesson.</span></span>

## <a name="branches-and-loops"></a><span data-ttu-id="f1303-129">分岐とループ</span><span class="sxs-lookup"><span data-stu-id="f1303-129">Branches and loops</span></span>

<span data-ttu-id="f1303-130">[分岐とループ](branches-and-loops-local.md) チュートリアルでは、変数に格納されている値に基づき、コード実行のさまざまなパスを選択することの基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="f1303-130">The [Branches and loops](branches-and-loops-local.md) tutorial teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="f1303-131">プログラムが決定して異なる操作を選択する上で基本となる、制御フローの基礎を学習します。</span><span class="sxs-lookup"><span data-stu-id="f1303-131">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span>

<span data-ttu-id="f1303-132">このチュートリアルでは、[Hello world](hello-world.yml) レッスンと [C# における数値](numbers-in-csharp-local.md)レッスンを修了していることが前提条件となります。</span><span class="sxs-lookup"><span data-stu-id="f1303-132">This tutorial assumes that you have finished the [Hello world](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collection"></a><span data-ttu-id="f1303-133">リスト コレクション</span><span class="sxs-lookup"><span data-stu-id="f1303-133">List collection</span></span>

<span data-ttu-id="f1303-134">「[リスト コレクション](arrays-and-collections.md)」レッスンでは、データのシーケンスを格納するリスト コレクション型について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1303-134">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="f1303-135">項目の追加方法や削除方法、項目の検索方法、リストを並べ替える方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="f1303-135">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="f1303-136">さまざまな種類のリストを紹介します。</span><span class="sxs-lookup"><span data-stu-id="f1303-136">You'll explore different kinds of lists.</span></span>

<span data-ttu-id="f1303-137">このチュートリアルでは、上に挙げたレッスンを終了していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="f1303-137">This tutorial assumes that you have finished the lessons listed above.</span></span>
