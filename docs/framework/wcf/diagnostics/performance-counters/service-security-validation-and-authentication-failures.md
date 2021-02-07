---
description: '詳細については、「サービス: セキュリティ検証と認証エラー」を参照してください。'
title: 'サービス : セキュリティ検証と認証エラー'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 8938c74e706526a02bf2ea5885951d067d6ebae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759485"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="a231b-103">サービス : セキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="a231b-103">Service: Security Validation and Authentication Failures</span></span>

<span data-ttu-id="a231b-104">カウンター名 : セキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="a231b-104">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="a231b-105">説明</span><span class="sxs-lookup"><span data-stu-id="a231b-105">Description</span></span>  

 <span data-ttu-id="a231b-106">このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="a231b-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="a231b-107">この問題には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="a231b-107">Such problems include:</span></span>  
  
- <span data-ttu-id="a231b-108">メッセージからクライアント トークンを読み取ることができない。</span><span class="sxs-lookup"><span data-stu-id="a231b-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="a231b-109">クライアント トークンが認証に失敗した (例 : 無効なパスワード)。</span><span class="sxs-lookup"><span data-stu-id="a231b-109">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="a231b-110">署名の検証に失敗した (例 : メッセージが改ざんされた)。</span><span class="sxs-lookup"><span data-stu-id="a231b-110">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="a231b-111">メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="a231b-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="a231b-112">復号化に失敗した。</span><span class="sxs-lookup"><span data-stu-id="a231b-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="a231b-113">一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。</span><span class="sxs-lookup"><span data-stu-id="a231b-113">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="a231b-114">TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="a231b-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
