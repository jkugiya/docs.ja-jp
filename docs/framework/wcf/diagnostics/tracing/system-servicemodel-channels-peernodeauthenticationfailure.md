---
description: 詳細については、「System.servicemodel」を参照してください。
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 751202abd3e199a03fc4ee0bf1252d4a8027e0cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99634935"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="79bc7-103">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="79bc7-103">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>

<span data-ttu-id="79bc7-104">潜在的な近隣ノードとのセキュリティ ハンドシェイクに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="79bc7-104">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="79bc7-105">説明</span><span class="sxs-lookup"><span data-stu-id="79bc7-105">Description</span></span>  

 <span data-ttu-id="79bc7-106">このトレースは、セキュリティで保護された近隣との接続を確立するときに行われます。</span><span class="sxs-lookup"><span data-stu-id="79bc7-106">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="79bc7-107">これは、資格情報が十分でないか間違っている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="79bc7-107">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="79bc7-108">PeerChannel では、トークンの種類として、強力な識別手段である X.509 証明書だけを認識します。X.509 証明書は、実装可能な認証および承認の種類に基づいて強力な ID モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="79bc7-108">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="79bc7-109">PeerChannel では、パスワードを使用した簡単なアプリケーションもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="79bc7-109">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="79bc7-110">パスワードは、セッションへのエントリを許可する目的でのみ使用できます。パスワードを使用して、メッセージの認証を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="79bc7-110">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="79bc7-111">これは、ピア グループで共有する共通鍵トークンをソース認証に使用することは困難かつ不適切であるためです。</span><span class="sxs-lookup"><span data-stu-id="79bc7-111">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="79bc7-112">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="79bc7-112">Troubleshooting</span></span>  

 <span data-ttu-id="79bc7-113">すべての近隣ノードに適切なセキュリティ資格情報があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="79bc7-113">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79bc7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="79bc7-114">See also</span></span>

- [<span data-ttu-id="79bc7-115">ピア チャネルのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="79bc7-115">Peer Channel Security</span></span>](../../feature-details/peer-channel-security.md)
- [<span data-ttu-id="79bc7-116">トレース</span><span class="sxs-lookup"><span data-stu-id="79bc7-116">Tracing</span></span>](index.md)
- [<span data-ttu-id="79bc7-117">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="79bc7-117">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="79bc7-118">管理と診断</span><span class="sxs-lookup"><span data-stu-id="79bc7-118">Administration and Diagnostics</span></span>](../index.md)
