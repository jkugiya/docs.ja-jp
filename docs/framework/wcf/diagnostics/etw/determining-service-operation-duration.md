---
description: 詳細については、「サービス操作の期間の決定」を参照してください。
title: サービス操作の実行時間の確認
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: e9dd9ee4113ee4b4521afb6dfaf6a913e72ea5d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798811"
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="a95e2-103">サービス操作の実行時間の確認</span><span class="sxs-lookup"><span data-stu-id="a95e2-103">Determining service operation duration</span></span>

<span data-ttu-id="a95e2-104">Windows Communication Foundation (WCF) アプリケーションで分析トレースが有効になっている場合、サービス操作の実行時間は、イベントログを調べることで簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="a95e2-104">If analytic tracing is enabled in a Windows Communication Foundation (WCF) application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="a95e2-105">ここでは、サービス操作の実行にかかる時間を確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a95e2-105">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="a95e2-106">サービス操作の実行時間の確認</span><span class="sxs-lookup"><span data-stu-id="a95e2-106">Determining service operation execution duration</span></span>  
  
1. <span data-ttu-id="a95e2-107">[ **開始**]、[ **実行**] の順にクリックしてイベントビューアーを開き、「」と入力し `eventvwr.exe` ます。</span><span class="sxs-lookup"><span data-stu-id="a95e2-107">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2. <span data-ttu-id="a95e2-108">分析トレースを有効にしていない場合は、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="a95e2-108">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="a95e2-109">[ **表示**]、[ **分析およびデバッグログの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a95e2-109">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="a95e2-110">[ **分析** ] を右クリックし、[ **ログを有効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a95e2-110">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="a95e2-111">サービス操作が実行された後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="a95e2-111">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3. <span data-ttu-id="a95e2-112">次に、サービスプロジェクトと、そのサービスと対話するクライアントプロジェクトを含む WCF アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="a95e2-112">Next, open a WCF application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="a95e2-113">このようなアプリケーションを作成するには、 [はじめにチュートリアル](../../getting-started-tutorial.md)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="a95e2-113">You can create such an application by following the [Getting Started Tutorial](../../getting-started-tutorial.md).</span></span>  <span data-ttu-id="a95e2-114">WCF サンプルがインストールされている場合は、チュートリアルで作成した完成したプロジェクトを含む [はじめに](../../samples/getting-started-sample.md)を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="a95e2-114">If you have the WCF samples installed, you can open the [Getting Started](../../samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4. <span data-ttu-id="a95e2-115">**F5** キーを押して、サーバーアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="a95e2-115">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="a95e2-116">**クライアントプロジェクトを** 右クリックし、[**デバッグ**]、[**新しいインスタンスを開始**] の順に選択して、クライアントアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="a95e2-116">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5. <span data-ttu-id="a95e2-117">イベント ビューアーで、分析ログを更新し、イベント ID でイベントを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="a95e2-117">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="a95e2-118">イベント ID [214-OperationCompleted](214-operationcompleted.md)のイベントを探します。</span><span class="sxs-lookup"><span data-stu-id="a95e2-118">Look for events with Event ID [214 - OperationCompleted](214-operationcompleted.md).</span></span>  <span data-ttu-id="a95e2-119">これらのイベントは、完了した操作、およびその操作にかかった時間を示します。</span><span class="sxs-lookup"><span data-stu-id="a95e2-119">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="a95e2-120">次のイベントは、追加操作の時間を示しています。</span><span class="sxs-lookup"><span data-stu-id="a95e2-120">The following event shows the duration of an Add operation.</span></span>  
  
    ```output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
