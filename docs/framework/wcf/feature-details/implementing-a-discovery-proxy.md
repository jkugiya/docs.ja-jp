---
description: 詳細については、「探索プロキシの実装」を参照してください。
title: 探索プロキシの実装
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: cfd897e114c99bcacb24e9981ee4a3e99e06636c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734036"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="ecc7b-103">探索プロキシの実装</span><span class="sxs-lookup"><span data-stu-id="ecc7b-103">Implementing a Discovery Proxy</span></span>

<span data-ttu-id="ecc7b-104">ここでは、探索プロキシの実装に必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-104">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="ecc7b-105">探索プロキシは、サービスのリポジトリを格納するスタンドアロンのサービスです。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-105">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="ecc7b-106">クライアントは探索プロキシに対し、そのプロキシで認識される探索可能なサービスを問い合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-106">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="ecc7b-107">プロキシにサービスを登録する方法は、実装手段によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-107">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="ecc7b-108">たとえば、探索プロキシが既存のサービス リポジトリに接続でき、その情報を探索可能にできる場合、管理者は管理 API を使用して探索可能なサービスをプロキシに追加することができます。または、探索プロキシにアナウンス機能を使用し、内部キャッシュを更新できます。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-108">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="ecc7b-109">WCF 実装は、プロキシを簡単にビルドできる基本クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-109">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="ecc7b-110">これらの API を利用して、既存のリポジトリの上に探索プロキシをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-110">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="ecc7b-111">ここで実装される探索プロキシは、探索可能にしてクライアントからエンドポイントを検索できるという点で、他の WCF サービスと似ています。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-111">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ecc7b-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ecc7b-112">In This Section</span></span>  

 [<span data-ttu-id="ecc7b-113">方法: 探索プロキシを実装する</span><span class="sxs-lookup"><span data-stu-id="ecc7b-113">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="ecc7b-114">探索プロキシを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-114">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="ecc7b-115">方法: 探索プロキシで登録される探索可能なサービスの実装する</span><span class="sxs-lookup"><span data-stu-id="ecc7b-115">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="ecc7b-116">探索プロキシに登録する探索可能な WCF サービスを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-116">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="ecc7b-117">方法: 探索プロキシを使用してサービスを検索するクライアント アプリケーションを実装する</span><span class="sxs-lookup"><span data-stu-id="ecc7b-117">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="ecc7b-118">探索プロキシを使用してサービスを検索する WCF クライアントアプリケーションを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-118">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="ecc7b-119">方法: 探索プロキシをテストする</span><span class="sxs-lookup"><span data-stu-id="ecc7b-119">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="ecc7b-120">前の 3 つのトピックに記述されたコードのテスト方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ecc7b-120">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc7b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecc7b-121">See also</span></span>

- [<span data-ttu-id="ecc7b-122">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="ecc7b-122">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="ecc7b-123">方法: プログラムを使用して探索可能性に WCF サービスとクライアントを追加する</span><span class="sxs-lookup"><span data-stu-id="ecc7b-123">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
