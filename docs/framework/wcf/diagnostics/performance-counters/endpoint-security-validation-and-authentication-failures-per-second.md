---
description: '詳細については、「エンドポイント: 1 秒あたりのセキュリティ検証と認証エラー」を参照してください。'
title: 'エンドポイント : 1 秒あたりのセキュリティ検証と認証エラー'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
ms.openlocfilehash: aa5ccc4049dc81a7c2d545cfc70e9078ac72d87a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655436"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="e8e61-103">エンドポイント : 1 秒あたりのセキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="e8e61-103">Endpoint: Security Validation and Authentication Failures Per Second</span></span>

<span data-ttu-id="e8e61-104">カウンター名 : 1 秒あたりのセキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="e8e61-104">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="e8e61-105">説明</span><span class="sxs-lookup"><span data-stu-id="e8e61-105">Description</span></span>  

 <span data-ttu-id="e8e61-106">このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="e8e61-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="e8e61-107">この問題には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="e8e61-107">Such problems include:</span></span>  
  
- <span data-ttu-id="e8e61-108">メッセージからクライアント トークンを読み取ることができない。</span><span class="sxs-lookup"><span data-stu-id="e8e61-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="e8e61-109">クライアント トークンが認証に失敗した (例 : 無効なパスワード)。</span><span class="sxs-lookup"><span data-stu-id="e8e61-109">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="e8e61-110">署名の検証に失敗した (例 : メッセージが改ざんされた)。</span><span class="sxs-lookup"><span data-stu-id="e8e61-110">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="e8e61-111">メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="e8e61-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="e8e61-112">復号化に失敗した。</span><span class="sxs-lookup"><span data-stu-id="e8e61-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="e8e61-113">一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。</span><span class="sxs-lookup"><span data-stu-id="e8e61-113">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="e8e61-114">TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="e8e61-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="e8e61-115">このカウンターの種類は [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))で、次の式を使用して値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="e8e61-115">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="e8e61-116">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="e8e61-116">(N1-N0)/((D1-D0)/F)</span></span>
