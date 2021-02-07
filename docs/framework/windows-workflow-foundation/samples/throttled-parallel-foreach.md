---
description: '詳細情報: 調整された並列 ForEach'
title: 制限された並列 ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 2c1d1386f0b8c5b3c68d60bc83386ccfdf5e7875
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741680"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="d1944-103">制限された並列 ForEach</span><span class="sxs-lookup"><span data-stu-id="d1944-103">Throttled Parallel ForEach</span></span>

<span data-ttu-id="d1944-104">ph x="1" /&gt; アクティビティは、実行する同時分岐の数を制限するためのコンカレンシー要因を設定できるという 1 つの例外を除き、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティと似ていることについて示します。</span><span class="sxs-lookup"><span data-stu-id="d1944-104">The `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="d1944-105">`ThrottleParallelForEach` アクティビティは、<xref:System.Activities.NativeActivity> クラスを介してのみアクセスできる他のアクティビティ (子アクティビティ) をスケジュールする必要があるため、<xref:System.Activities.NativeActivityContext> クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="d1944-105">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>

## <a name="projects"></a><span data-ttu-id="d1944-106">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="d1944-106">Projects</span></span>

|<span data-ttu-id="d1944-107">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="d1944-107">**ProjectName**</span></span>|<span data-ttu-id="d1944-108">**説明**</span><span class="sxs-lookup"><span data-stu-id="d1944-108">**Description**</span></span>|<span data-ttu-id="d1944-109">**メイン ファイル**</span><span class="sxs-lookup"><span data-stu-id="d1944-109">**Main Files**</span></span>|
|-|-|-|
|<span data-ttu-id="d1944-110">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="d1944-110">ThrottledParallelForEach</span></span>|<span data-ttu-id="d1944-111">`ThrottledParallelForEach` アクティビティとそのデザイナーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1944-111">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="d1944-112">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="d1944-112">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="d1944-113">`ThrottledParallelForEach` アクティビティ定義。</span><span class="sxs-lookup"><span data-stu-id="d1944-113">The `ThrottledParallelForEach` activity definition.</span></span>|
|<span data-ttu-id="d1944-114">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="d1944-114">CodeTestClient</span></span>|<span data-ttu-id="d1944-115">命令型コードを使用して、`ThrottledParallelForEach` を含むワークフローを構成および実行するサンプル クライアント アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="d1944-115">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="d1944-116">Program.cs</span><span class="sxs-lookup"><span data-stu-id="d1944-116">Program.cs</span></span><br /><br /> <span data-ttu-id="d1944-117">サンプル ワークフローのインスタンスを定義および実行します。</span><span class="sxs-lookup"><span data-stu-id="d1944-117">Defines and runs an instance of the sample workflow.</span></span>|

## <a name="to-use-this-sample"></a><span data-ttu-id="d1944-118">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="d1944-118">To use this sample</span></span>

1. <span data-ttu-id="d1944-119">Visual Studio 2010 を使用して、ThrottledParallelForEach ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d1944-119">Using Visual Studio 2010, open the ThrottledParallelForEach.sln file.</span></span>

2. <span data-ttu-id="d1944-120">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d1944-120">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="d1944-121">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d1944-121">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1944-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d1944-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d1944-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d1944-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d1944-124">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="d1944-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d1944-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d1944-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
