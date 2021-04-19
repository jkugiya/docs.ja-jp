---
title: 基本的なプログラミング ライフサイクル
description: WCF アプリケーションを構築するためのタスクについて説明します。 WCF を使用すると、アプリは、同じコンピューター、ネットワーク経由、または異なるアプリケーション プラットフォーム上で通信できます。
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: f958bd06f617a5648b31332ebe9e7662d45cd241
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294847"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="44913-104">基本的なプログラミング ライフサイクル</span><span class="sxs-lookup"><span data-stu-id="44913-104">Basic Programming Lifecycle</span></span>

<span data-ttu-id="44913-105">Windows Communication Foundation (WCF) を使用すると、アプリケーションは、同一のコンピューター上、インターネット経由、異なるアプリケーション プラットフォーム上のいずれに存在していても通信できます。</span><span class="sxs-lookup"><span data-stu-id="44913-105">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="44913-106">ここでは、WCF アプリケーションを構築するために必要なタスクについて概説します。</span><span class="sxs-lookup"><span data-stu-id="44913-106">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="44913-107">実際のサンプル アプリケーションについては、「[チュートリアル入門](getting-started-tutorial.md)」参照してください。</span><span class="sxs-lookup"><span data-stu-id="44913-107">For a working sample application, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="44913-108">基本的なタスク</span><span class="sxs-lookup"><span data-stu-id="44913-108">The Basic Tasks</span></span>  

 <span data-ttu-id="44913-109">基本的な作業は、次の順序で行います。</span><span class="sxs-lookup"><span data-stu-id="44913-109">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="44913-110">サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="44913-110">Define the service contract.</span></span> <span data-ttu-id="44913-111">サービス コントラクトでは、サービスの署名、交換するデータ、およびコントラクトに必要なその他のデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="44913-111">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="44913-112">詳細については、「[サービス コントラクトの設計](designing-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44913-112">For more information, see [Designing Service Contracts](designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="44913-113">コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="44913-113">Implement the contract.</span></span> <span data-ttu-id="44913-114">サービス コントラクトを実装するには、そのコントラクトを実装するクラスを作成し、ランタイムに必要なカスタム動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="44913-114">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="44913-115">詳細については、「[サービス コントラクトの実装](implementing-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44913-115">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="44913-116">エンドポイントおよびその他の動作情報を指定して、サービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="44913-116">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="44913-117">詳細については、「[サービスの構成](configuring-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44913-117">For more information, see [Configuring Services](configuring-services.md).</span></span>  
  
4. <span data-ttu-id="44913-118">サービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="44913-118">Host the service.</span></span> <span data-ttu-id="44913-119">詳細については、「[ホスティング サービス](hosting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44913-119">For more information, see [Hosting Services](hosting-services.md).</span></span>  
  
5. <span data-ttu-id="44913-120">クライアント アプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="44913-120">Build a client application.</span></span> <span data-ttu-id="44913-121">詳細については、「[クライアントを構築する](building-clients.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44913-121">For more information, see [Building Clients](building-clients.md).</span></span>  
  
 <span data-ttu-id="44913-122">このセクションのトピックではこの順に従って説明しますが、手順を最初から実行しないシナリオもあります。</span><span class="sxs-lookup"><span data-stu-id="44913-122">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="44913-123">たとえば、既存のサービスを使用するクライアントを構築する場合は、手順 5. から開始します。</span><span class="sxs-lookup"><span data-stu-id="44913-123">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="44913-124">また、既存のクライアント アプリケーションが使用するサービスを構築する場合は、手順 5. を省略できます。</span><span class="sxs-lookup"><span data-stu-id="44913-124">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="44913-125">サービス コントラクトの開発について理解したら、「[拡張機能の概要](introduction-to-extensibility.md)」に目を通すこともできます。</span><span class="sxs-lookup"><span data-stu-id="44913-125">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](introduction-to-extensibility.md).</span></span> <span data-ttu-id="44913-126">サービスで問題が発生した場合は、「[WCF トラブルシューティング クイックスタート](wcf-troubleshooting-quickstart.md)」をチェックし、同様の問題が他で発生していないかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="44913-126">If you have problems with your service, check [WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44913-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="44913-127">See also</span></span>

- [<span data-ttu-id="44913-128">サービス コントラクトの実装</span><span class="sxs-lookup"><span data-stu-id="44913-128">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
