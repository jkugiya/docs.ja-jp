---
description: 詳細については、「WCF Discovery」を参照してください。
title: WCF Discovery
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 67fa5800209676b11e9e49171483bf514b6a190a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779635"
---
# <a name="wcf-discovery"></a><span data-ttu-id="2f0f3-103">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="2f0f3-103">WCF Discovery</span></span>

<span data-ttu-id="2f0f3-104">Windows Communication Foundation (WCF) は、WS-Discovery プロトコルを使用して、相互運用可能な方法で実行時にサービスを探索可能にするためのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-104">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="2f0f3-105">WCF サービスは、マルチキャストメッセージまたは探索プロキシサーバーを使用して、ネットワークへの可用性をアナウンスできます。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-105">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="2f0f3-106">クライアント アプリケーションは、ネットワークまたは探索プロキシ サーバーを検索して、一連の基準を満たすサービスを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-106">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="2f0f3-107">このセクションのトピックでは、この機能の概要を示し、そのプログラミング モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-107">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f0f3-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2f0f3-108">In This Section</span></span>  

 [<span data-ttu-id="2f0f3-109">WCF Discovery の概要</span><span class="sxs-lookup"><span data-stu-id="2f0f3-109">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)  
 <span data-ttu-id="2f0f3-110">WCF によって提供される WS-Discovery のサポートの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-110">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="2f0f3-111">WCF Discovery オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="2f0f3-111">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)  
 <span data-ttu-id="2f0f3-112">オブジェクト モデルのクラスと WS-Discovery サポートの拡張性について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-112">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="2f0f3-113">方法: プログラムを使用して探索可能性に WCF サービスとクライアントを追加する</span><span class="sxs-lookup"><span data-stu-id="2f0f3-113">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="2f0f3-114">Windows Communication Foundation (WCF) サービスを探索可能にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-114">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="2f0f3-115">探索プロキシの実装</span><span class="sxs-lookup"><span data-stu-id="2f0f3-115">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)  
 <span data-ttu-id="2f0f3-116">探索プロキシを実装するのに必要な手順、探索プロキシで登録される探索可能なサービス、および探索プロキシを使用して探索可能なサービスを検索するクライアントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-116">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="2f0f3-117">探索機能のバージョン指定</span><span class="sxs-lookup"><span data-stu-id="2f0f3-117">Discovery Versioning</span></span>](discovery-versioning.md)  
 <span data-ttu-id="2f0f3-118">いくつかの新しい探索機能のプロトタイプ実装の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-118">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="2f0f3-119">使用する探索バージョンを選択する方法の概要も示します。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-119">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="2f0f3-120">構成ファイルにおける探索の構成</span><span class="sxs-lookup"><span data-stu-id="2f0f3-120">Configuring Discovery in a Configuration File</span></span>](configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="2f0f3-121">構成ファイルで探索を構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-121">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="2f0f3-122">探索クライアント チャネルの使用</span><span class="sxs-lookup"><span data-stu-id="2f0f3-122">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)  
 <span data-ttu-id="2f0f3-123">WCF クライアントアプリケーションを記述するときに探索クライアントチャネルを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f0f3-123">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>
