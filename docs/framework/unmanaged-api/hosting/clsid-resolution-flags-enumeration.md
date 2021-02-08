---
description: '詳細情報: CLSID_RESOLUTION_FLAGS 列挙型'
title: CLSID_RESOLUTION_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- CLSID_RESOLUTION_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLSID_RESOLUTION_FLAGS
helpviewer_keywords:
- CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type:
- apiref
ms.openlocfilehash: 54d334147e13217f8ce20dae1b139cdc6d11a3b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799877"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="608ee-103">CLSID_RESOLUTION_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="608ee-103">CLSID_RESOLUTION_FLAGS Enumeration</span></span>

<span data-ttu-id="608ee-104">共通言語ランタイム (CLR: common language runtime) でを解決する方法を示す値を格納し `CLSID` ます。</span><span class="sxs-lookup"><span data-stu-id="608ee-104">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="608ee-105">構文</span><span class="sxs-lookup"><span data-stu-id="608ee-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="608ee-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="608ee-106">Members</span></span>  
  
|<span data-ttu-id="608ee-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="608ee-107">Member</span></span>|<span data-ttu-id="608ee-108">説明</span><span class="sxs-lookup"><span data-stu-id="608ee-108">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="608ee-109">既定の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="608ee-109">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="608ee-110">は、ランタイムがレジストリを検索して shim ポリシーを適用することを示します。</span><span class="sxs-lookup"><span data-stu-id="608ee-110">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="608ee-111">要件</span><span class="sxs-lookup"><span data-stu-id="608ee-111">Requirements</span></span>  

 <span data-ttu-id="608ee-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="608ee-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="608ee-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="608ee-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="608ee-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="608ee-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608ee-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="608ee-115">See also</span></span>

- [<span data-ttu-id="608ee-116">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="608ee-116">Hosting Enumerations</span></span>](hosting-enumerations.md)
