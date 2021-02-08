---
description: 詳細については、「非同期通信」を参照してください。
title: 非同期通信
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 3e824c03a07682faaf60d8434f6af1a26742ead7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792597"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="408ad-103">非同期通信</span><span class="sxs-lookup"><span data-stu-id="408ad-103">Asynchronous Communication</span></span>

<span data-ttu-id="408ad-104">このサンプルでは、2つの異なる Windows Workflow Foundation (WF) サービス間の通信が既定で非同期に実行される方法を示します。</span><span class="sxs-lookup"><span data-stu-id="408ad-104">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="408ad-105">対象</span><span class="sxs-lookup"><span data-stu-id="408ad-105">Demonstrates</span></span>  

 <span data-ttu-id="408ad-106">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] サービス間の非同期通信</span><span class="sxs-lookup"><span data-stu-id="408ad-106">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="408ad-107">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="408ad-107">Discussion</span></span>  

 <span data-ttu-id="408ad-108">このサンプルでは、.NET Framework が提供するメッセージング アクティビティを使用して、[!INCLUDE[wf1](../../../../includes/wf1-md.md)] アプリケーション間の非同期通信がどのように行われるのかを示します。</span><span class="sxs-lookup"><span data-stu-id="408ad-108">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="408ad-109">このサンプルは、次の 3 つのプロジェクトで構成されています。</span><span class="sxs-lookup"><span data-stu-id="408ad-109">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="408ad-110">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="408ad-110">CreditCheckService</span></span>  
 <span data-ttu-id="408ad-111">このサービスは、特定の個人のクレジット スコアまたは取得する項目の値を受け取り、その個人にクレジットを与えるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="408ad-111">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="408ad-112">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="408ad-112">RentalApprovalService</span></span>  
 <span data-ttu-id="408ad-113">このサービスは、特定のクレジットを必要としている個人から申請を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="408ad-113">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="408ad-114">このサービスは `CreditCheckService` と非同期で通信して、クレジットの申請が有効かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="408ad-114">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="408ad-115">クライアント</span><span class="sxs-lookup"><span data-stu-id="408ad-115">Client</span></span>  
 <span data-ttu-id="408ad-116">クライアントは `RentalApprovalService` と同期通信を行い、クレジットが承認されているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="408ad-116">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="408ad-117">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="408ad-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="408ad-118">**AsynchronousCommunication** ソリューションを右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="408ad-118">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="408ad-119">[ **共通プロパティ**] で、[ **スタートアッププロジェクト**] を選択し、[ **マルチスタートアッププロジェクト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="408ad-119">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="408ad-120">**RentalApprovalService** をリスト内の最初の位置、次に **CreditCheckService**、 **Client** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="408ad-120">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="408ad-121">3つのプロジェクトすべてに **開始** アクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="408ad-121">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="408ad-122">[ **OK**] をクリックし、F5 キーを押してサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="408ad-122">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="408ad-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="408ad-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="408ad-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="408ad-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="408ad-125">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="408ad-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="408ad-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="408ad-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
