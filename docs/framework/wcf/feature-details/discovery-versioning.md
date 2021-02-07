---
description: 詳細については、「探索のバージョン管理」をご覧ください。
title: 探索機能のバージョン指定
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 075fefce0477810336c8b857343984070ed89b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743188"
---
# <a name="discovery-versioning"></a><span data-ttu-id="6e2c6-103">探索機能のバージョン指定</span><span class="sxs-lookup"><span data-stu-id="6e2c6-103">Discovery Versioning</span></span>

<span data-ttu-id="6e2c6-104">ここでは、新しい探索機能の実装の概要について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-104">This topic provides a brief overview of the implementation of some new discovery features.</span></span> <span data-ttu-id="6e2c6-105">使用する探索バージョンを選択する方法の概要も示します。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-105">It also gives an overview on how to select the discovery version to use.</span></span>

## <a name="discovery-versioning"></a><span data-ttu-id="6e2c6-106">探索機能のバージョン指定</span><span class="sxs-lookup"><span data-stu-id="6e2c6-106">Discovery Versioning</span></span>

<span data-ttu-id="6e2c6-107">探索機能は、WS_Discovery プロトコルの 3 つのバージョンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-107">The discovery feature includes support for three versions of the WS_Discovery protocol.</span></span> <span data-ttu-id="6e2c6-108">探索 API を使用すると、使用するプロトコルのバージョンを選択できます。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-108">The discovery APIs allow you to select which version of the protocol you want to use.</span></span> <span data-ttu-id="6e2c6-109">このドキュメントでは、バージョン指定に関連する設定について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-109">This document briefly describes the versioning-related settings.</span></span>

<span data-ttu-id="6e2c6-110">次の Discovery クラスには <xref:System.ServiceModel.Discovery.DiscoveryVersion> プロパティがあり、コンストラクターで <xref:System.ServiceModel.Discovery.DiscoveryVersion> 引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-110">The following Discovery classes now have a <xref:System.ServiceModel.Discovery.DiscoveryVersion> property and take a <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument in their constructors:</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>

### <a name="discoveryversionwsdiscoveryapril2005"></a><span data-ttu-id="6e2c6-111">DiscoveryVersion.WSDiscoveryApril2005</span><span class="sxs-lookup"><span data-stu-id="6e2c6-111">DiscoveryVersion.WSDiscoveryApril2005</span></span>

<span data-ttu-id="6e2c6-112">を <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> コンストラクターパラメーターとして指定すると、実装では WS-Discovery プロトコルの April2005 バージョンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-112">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> as a constructor parameter makes the implementation use the April2005 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="6e2c6-113">このバージョンは、WS-Discovery プロトコル仕様の発行済みバージョンに対応します。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-113">This version corresponds to the published version of the WS-Discovery protocol specification.</span></span> <span data-ttu-id="6e2c6-114">このバージョンは、WS-Discovery の April2005 バージョンを利用しているレガシ アプリケーションとの相互運用時に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-114">This version should be used to interoperate with legacy application utilizing the April2005 version of WS-Discovery.</span></span>

### <a name="discoveryversionwsdiscovery11"></a><span data-ttu-id="6e2c6-115">DiscoveryVersion.WSDiscovery11</span><span class="sxs-lookup"><span data-stu-id="6e2c6-115">DiscoveryVersion.WSDiscovery11</span></span>

<span data-ttu-id="6e2c6-116">Api で使用される既定の探索バージョンは <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11> です。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-116">The default discovery version used by the APIs is <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span></span> <span data-ttu-id="6e2c6-117">これは、現在標準化されている WS-Discovery プロトコルのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-117">This is the current standardized version of the WS-Discovery protocol.</span></span>

## <a name="discoveryversionwsdiscoverycd1"></a><span data-ttu-id="6e2c6-118">DiscoveryVersion.WSDiscoveryCD1</span><span class="sxs-lookup"><span data-stu-id="6e2c6-118">DiscoveryVersion.WSDiscoveryCD1</span></span>

<span data-ttu-id="6e2c6-119">コンストラクターのパラメーターとして <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> を使用することで、WS-Discovery プロトコルの Committee Draft 1 バージョンが実装で使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-119">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> as a constructor parameter makes the implementation use the committee draft 1 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="6e2c6-120">このバージョンのプロトコルは、WS-Discovery プロトコルの CD1 バージョンを利用している実装との相互運用時に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-120">This version of the protocol should be used to interoperate with implementations running the CD1 version of the WS-Discovery protocol.</span></span>

## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a><span data-ttu-id="6e2c6-121">単一のサービス ホスト上にある異なる探索バージョン用の複数の UDP 探索エンドポイントのサポート</span><span class="sxs-lookup"><span data-stu-id="6e2c6-121">Supporting Multiple UDP Discovery Endpoints for Different Discovery Versions on a Single Service Host</span></span>

<span data-ttu-id="6e2c6-122">単一のサービス ホスト上にある、異なる探索バージョン用の複数の UDP 探索エンドポイントを公開する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-122">You may want to expose multiple UDP Discovery Endpoints for different discovery versions on a single service host.</span></span> <span data-ttu-id="6e2c6-123">このような場合、UDP 探索エンドポイントごとに一意のアドレスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-123">To do this you must specify a unique address for each UDP discovery endpoint.</span></span> <span data-ttu-id="6e2c6-124">次の例は、その方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="6e2c6-124">The following example shows how to do this.</span></span>

```csharp
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);

newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionApril2005");

serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);
```
