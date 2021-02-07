---
description: WCF と Websocket の詳細情報
title: WCF と WebSocket
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: 6b0d8c33000a65bf3bbf834f66119d65768b3cb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755981"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="c9acb-103">WCF と WebSocket</span><span class="sxs-lookup"><span data-stu-id="c9acb-103">WCF and WebSockets</span></span>

<span data-ttu-id="c9acb-104">.NET Framework 4.5 では、Windows Communication Foundation の WebSocket のサポートが導入されています。</span><span class="sxs-lookup"><span data-stu-id="c9acb-104">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="c9acb-105">Websocket は、標準的な HTTP ポート 80 と 443 を介した双方向通信を有効にする効率的な標準ベース テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="c9acb-105">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="c9acb-106">標準 HTTP ポートを使用することで、Websocket は中継局を通じて Web 全体で通信できます。</span><span class="sxs-lookup"><span data-stu-id="c9acb-106">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="c9acb-107">2 つの新しい標準バインディングが WebSocket トランスポート経由の通信をサポートするために追加されました。</span><span class="sxs-lookup"><span data-stu-id="c9acb-107">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="c9acb-108"><xref:System.ServiceModel.NetHttpBinding> および <xref:System.ServiceModel.NetHttpsBinding>。</span><span class="sxs-lookup"><span data-stu-id="c9acb-108"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="c9acb-109">Websocket 固有の設定は、プロパティにアクセスすることによってで構成でき <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="c9acb-109">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="c9acb-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c9acb-110">In This Section</span></span>  

 [<span data-ttu-id="c9acb-111">NetHttpBinding の使用</span><span class="sxs-lookup"><span data-stu-id="c9acb-111">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)  
 <span data-ttu-id="c9acb-112"><xref:System.ServiceModel.NetHttpBinding> とその構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9acb-112">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="c9acb-113">方法: WebSockets 上で通信する WCF サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="c9acb-113">How to: Create a WCF Service that Communicates over WebSockets</span></span>](how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="c9acb-114">Websocket 経由で通信する WCF サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9acb-114">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c9acb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9acb-115">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c9acb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9acb-116">Related Sections</span></span>
