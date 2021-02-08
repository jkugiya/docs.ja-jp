---
description: '詳細: NetTcpBinding アプリケーションからピアチャネルアプリケーションへの変換'
title: NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 828ffce38fb05acff851c9fe5a6fbb38fffad6aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780415"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="be7e2-103">NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換</span><span class="sxs-lookup"><span data-stu-id="be7e2-103">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>

<span data-ttu-id="be7e2-104">接続のパラメーターを記述するバインディングを使用して、WinFX を使用するクライアント間の接続を作成できます。</span><span class="sxs-lookup"><span data-stu-id="be7e2-104">You can create connections between clients using the WinFX by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="be7e2-105">ピアツーピア接続を使用するように .NET Framework アプリケーションを変換するには、クライアント接続を行うときに、このテクノロジをサポートするバインディングが必要です。</span><span class="sxs-lookup"><span data-stu-id="be7e2-105">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="be7e2-106">ピア チャネルには、<xref:System.ServiceModel.NetPeerTcpBinding> と呼ばれるバインディングが用意されています。このバインディングは、<xref:System.ServiceModel.NetTcpBinding> と同じような方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="be7e2-106">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="be7e2-107">主な違いは、リゾルバー サービスの仕様とセキュリティ設定の定義です。</span><span class="sxs-lookup"><span data-stu-id="be7e2-107">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="be7e2-108">アプリケーションでリゾルバーとセキュリティの既定の設定を使用する場合、通常のクライアント/サーバー ベースのアプリケーションは、アプリケーションの構成ファイルでバインディング名を "NetTcpBinding" から "NetPeerTcpBinding" に変更するだけで、ピア チャネルを使用するように変換できます。アプリケーションのコード ベースを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="be7e2-108">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7e2-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="be7e2-109">See also</span></span>

- [<span data-ttu-id="be7e2-110">ピア チャネル アプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="be7e2-110">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
- [<span data-ttu-id="be7e2-111">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="be7e2-111">System-Provided Bindings</span></span>](../system-provided-bindings.md)
