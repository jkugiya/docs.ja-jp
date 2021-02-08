---
description: '詳細情報: AXL_AUTHENTICODE_SIGNER_INFO 構造'
title: AXL_AUTHENTICODE_SIGNER_INFO 構造体
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
ms.openlocfilehash: 940652cf184e26f141df806b060c391333d1bb95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781962"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="b7174-103">AXL_AUTHENTICODE_SIGNER_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="b7174-103">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>

<span data-ttu-id="b7174-104">Authenticode の署名者情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="b7174-104">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7174-105">構文</span><span class="sxs-lookup"><span data-stu-id="b7174-105">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b7174-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b7174-106">Members</span></span>  
  
|<span data-ttu-id="b7174-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b7174-107">Member</span></span>|<span data-ttu-id="b7174-108">説明</span><span class="sxs-lookup"><span data-stu-id="b7174-108">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="b7174-109">この構造のサイズ。</span><span class="sxs-lookup"><span data-stu-id="b7174-109">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="b7174-110">エラー コード。</span><span class="sxs-lookup"><span data-stu-id="b7174-110">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="b7174-111">ハッシュアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="b7174-111">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="b7174-112">ハッシュです。</span><span class="sxs-lookup"><span data-stu-id="b7174-112">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="b7174-113">説明です。</span><span class="sxs-lookup"><span data-stu-id="b7174-113">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="b7174-114">説明の URL。</span><span class="sxs-lookup"><span data-stu-id="b7174-114">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="b7174-115">署名者のチェーン コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="b7174-115">The chain context of the signer.</span></span> <span data-ttu-id="b7174-116">[CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7174-116">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7174-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7174-117">See also</span></span>

- [<span data-ttu-id="b7174-118">Authenticode</span><span class="sxs-lookup"><span data-stu-id="b7174-118">Authenticode</span></span>](index.md)
