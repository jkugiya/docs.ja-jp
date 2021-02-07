---
description: 詳細については、「トランザクションモデル」を参照してください。
title: トランザクション モデル
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9abccf74ef5b242cfbe63605046e30e397b8eda6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752705"
---
# <a name="transaction-models"></a><span data-ttu-id="46c47-103">トランザクション モデル</span><span class="sxs-lookup"><span data-stu-id="46c47-103">Transaction Models</span></span>

<span data-ttu-id="46c47-104">ここでは、トランザクション プログラミング モデルと、マイクロソフトが提供するインフラストラクチャ コンポーネントとの関係を説明します。</span><span class="sxs-lookup"><span data-stu-id="46c47-104">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="46c47-105">Windows Communication Foundation (WCF) でトランザクションを使用する場合は、異なるトランザクションモデルを選択するのではなく、統合された一貫性のあるモデルの異なる層で操作することを理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="46c47-105">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="46c47-106">以下に、3 つの主要なトランザクション コンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="46c47-106">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="46c47-107">Windows Communication Foundation トランザクション</span><span class="sxs-lookup"><span data-stu-id="46c47-107">Windows Communication Foundation Transactions</span></span>  

 <span data-ttu-id="46c47-108">WCF でのトランザクションのサポートにより、トランザクションサービスを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="46c47-108">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="46c47-109">さらに、WS-AtomicTransaction (WS-AT) プロトコルがサポートされているため、アプリケーションは WCF またはサードパーティのテクノロジを使用して構築された Web サービスにトランザクションをフローできます。</span><span class="sxs-lookup"><span data-stu-id="46c47-109">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="46c47-110">WCF サービスまたはアプリケーションでは、WCF トランザクション機能によって属性と構成が提供され、インフラストラクチャがトランザクションを作成、フロー、および同期する方法とタイミングを宣言によって指定できます。</span><span class="sxs-lookup"><span data-stu-id="46c47-110">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="46c47-111">System.Transactions トランザクション</span><span class="sxs-lookup"><span data-stu-id="46c47-111">System.Transactions Transactions</span></span>  

 <span data-ttu-id="46c47-112"><xref:System.Transactions> 名前空間は、<xref:System.Transactions.Transaction> クラスに基づく明示的なプログラミング モデルだけでなく、インフラストラクチャがトランザクションを自動的に管理する、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なプログラミング モデルも提供します。</span><span class="sxs-lookup"><span data-stu-id="46c47-112">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="46c47-113">これら2つのモデルを使用してトランザクションアプリケーションを作成する方法の詳細については、「 [トランザクションアプリケーションの](https://go.microsoft.com/fwlink/?LinkId=94947)作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46c47-113">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="46c47-114">WCF サービスまたはアプリケーションでは、は、 <xref:System.Transactions> クライアントアプリケーション内でトランザクションを作成するためのプログラミングモデルを提供し、必要に応じてサービス内でトランザクションを明示的に操作します。</span><span class="sxs-lookup"><span data-stu-id="46c47-114">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="46c47-115">MSDTC トランザクション</span><span class="sxs-lookup"><span data-stu-id="46c47-115">MSDTC Transactions</span></span>  

 <span data-ttu-id="46c47-116">Microsoft 分散トランザクション コーディネーター (MSDTC) は、分散トランザクションをサポートするトランザクション マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="46c47-116">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="46c47-117">詳細については、「 [DTC プログラマーズリファレンス](/previous-versions/windows/desktop/ms686108(v=vs.85))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46c47-117">For more information, see the [DTC Programmer's Reference](/previous-versions/windows/desktop/ms686108(v=vs.85)).</span></span>  
  
 <span data-ttu-id="46c47-118">WCF サービスまたはアプリケーションでは、MSDTC によって、クライアントまたはサービス内で作成されたトランザクションを調整するためのインフラストラクチャが提供されます。</span><span class="sxs-lookup"><span data-stu-id="46c47-118">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
