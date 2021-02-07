---
description: 詳細については、「チャネルレイヤーの拡張」を参照してください。
title: チャネル レイヤーの拡張
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: 4588a2749127e454801615cc8916d83fc15592bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685583"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="37944-103">チャネル レイヤーの拡張</span><span class="sxs-lookup"><span data-stu-id="37944-103">Extending the Channel Layer</span></span>

<span data-ttu-id="37944-104">チャネル レイヤーはクライアントとサービス間のメッセージの交換を担います。</span><span class="sxs-lookup"><span data-stu-id="37944-104">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="37944-105">チャネル拡張では、新しいプロトコル機能 (セキュリティなど)、またはトランスポート機能 (SOAP メッセージを送信する新しいネットワーク トランスポートの実装など) を実装できます。</span><span class="sxs-lookup"><span data-stu-id="37944-105">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37944-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="37944-106">In This Section</span></span>  

 [<span data-ttu-id="37944-107">チャネル モデルの概要</span><span class="sxs-lookup"><span data-stu-id="37944-107">Channel Model Overview</span></span>](channel-model-overview.md)  
 <span data-ttu-id="37944-108">チャネルとその機能、サービス アプリケーションおよびクライアント アプリケーションとの連携について概要を示します。</span><span class="sxs-lookup"><span data-stu-id="37944-108">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="37944-109">チャネルの開発</span><span class="sxs-lookup"><span data-stu-id="37944-109">Developing Channels</span></span>](developing-channels.md)  
 <span data-ttu-id="37944-110">各種のチャネル インフラストラクチャが果たす役割、ステート エンジンとステート ライフサイクルのしくみ、例外とエラーの処理方法、メタデータ サポートの実装方法、チャネルとメッセージ エンコーダーの連携について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="37944-110">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="37944-111">カスタム エンコーダー</span><span class="sxs-lookup"><span data-stu-id="37944-111">Custom Encoders</span></span>](custom-encoders.md)  
 <span data-ttu-id="37944-112">メッセージ エンコーダーがチャネルで果たす役割、およびメッセージ エンコーダーの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37944-112">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="37944-113">カスタム ストリームのアップグレード</span><span class="sxs-lookup"><span data-stu-id="37944-113">Custom Stream Upgrades</span></span>](custom-stream-upgrades.md)  
 <span data-ttu-id="37944-114">ストリーム指向のトランスポートによって提供されるストリームのアップグレード プロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="37944-114">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>
