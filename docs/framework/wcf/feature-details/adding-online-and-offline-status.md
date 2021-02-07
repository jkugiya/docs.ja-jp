---
description: オンラインとオフラインの状態の追加に関する詳細情報
title: オンライン ステータスとオフライン ステータスの追加
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 33f7920954ed28ebc2c3d34cc54a2e294f5730c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705240"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="193a5-103">オンライン ステータスとオフライン ステータスの追加</span><span class="sxs-lookup"><span data-stu-id="193a5-103">Adding Online and Offline Status</span></span>

<span data-ttu-id="193a5-104">多くの場合、アプリケーションではピア チャネル接続のステータスについて明確な詳細情報を監視することが重要です。</span><span class="sxs-lookup"><span data-stu-id="193a5-104">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="193a5-105">この情報は、`GetProperty` インターフェイスの実装で <xref:System.ServiceModel.IOnlineStatus> メソッドを呼び出すことで取得できます。</span><span class="sxs-lookup"><span data-stu-id="193a5-105">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="193a5-106">このインターフェイスを実装するオブジェクトは、接続ステータスを監視したり、`OnOnline` や `OnOffline` などのイベント ハンドラーを登録したりできるため、オンライン ステータスに変化があると即座に反応できます。</span><span class="sxs-lookup"><span data-stu-id="193a5-106">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="193a5-107">ピア チャネル インフラストラクチャでは、クライアントが少なくとも 1 つのピアに接続されているとオンラインと見なされ、そうでない場合はオフラインと見なされます。</span><span class="sxs-lookup"><span data-stu-id="193a5-107">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="193a5-108">このことは、開発中のアプリケーションをデバッグする際や、エンド ユーザーに詳細情報を表示する際に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="193a5-108">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="193a5-109">オンライン イベント ハンドラーでは、メッセージを送信する前に、まず、ノードが開いていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="193a5-109">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="193a5-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="193a5-110">See also</span></span>

- [<span data-ttu-id="193a5-111">ピア チャネル アプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="193a5-111">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
