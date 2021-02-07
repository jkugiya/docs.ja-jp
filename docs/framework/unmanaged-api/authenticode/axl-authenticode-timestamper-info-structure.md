---
description: '詳細情報: AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造'
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造体
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: 35e30241c3c3b5747e247c57183e28e726c0cae3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747414"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="4605d-103">AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="4605d-103">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>

<span data-ttu-id="4605d-104">Authenticode のタイム スタンパー情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="4605d-104">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4605d-105">構文</span><span class="sxs-lookup"><span data-stu-id="4605d-105">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="4605d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4605d-106">Members</span></span>  
  
|<span data-ttu-id="4605d-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="4605d-107">Member</span></span>|<span data-ttu-id="4605d-108">説明</span><span class="sxs-lookup"><span data-stu-id="4605d-108">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="4605d-109">この構造のサイズ。</span><span class="sxs-lookup"><span data-stu-id="4605d-109">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="4605d-110">エラー コード。</span><span class="sxs-lookup"><span data-stu-id="4605d-110">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="4605d-111">ハッシュアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="4605d-111">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="4605d-112">タイム スタンプの時刻。</span><span class="sxs-lookup"><span data-stu-id="4605d-112">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="4605d-113">タイム スタンパーのチェーン コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="4605d-113">The time stamper’s chain context.</span></span>  <span data-ttu-id="4605d-114">[CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4605d-114">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4605d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="4605d-115">See also</span></span>

- [<span data-ttu-id="4605d-116">Authenticode</span><span class="sxs-lookup"><span data-stu-id="4605d-116">Authenticode</span></span>](index.md)
