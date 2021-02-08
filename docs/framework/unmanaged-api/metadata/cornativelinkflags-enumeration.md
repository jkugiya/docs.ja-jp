---
description: '詳細については、次を参照してください: CorNativeLinkFlags 列挙型'
title: CorNativeLinkFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: 9025d192ca92c1160c1b072b0dcfe045fa3ceab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784354"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="e2e61-103">CorNativeLinkFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="e2e61-103">CorNativeLinkFlags Enumeration</span></span>

<span data-ttu-id="e2e61-104">ネイティブ コードをリンクするときに、リンカーが使用するフラグ値を提供します。</span><span class="sxs-lookup"><span data-stu-id="e2e61-104">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e61-105">構文</span><span class="sxs-lookup"><span data-stu-id="e2e61-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e2e61-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e2e61-106">Members</span></span>  
  
|<span data-ttu-id="e2e61-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="e2e61-107">Member</span></span>|<span data-ttu-id="e2e61-108">説明</span><span class="sxs-lookup"><span data-stu-id="e2e61-108">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="e2e61-109">フラグがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="e2e61-109">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="e2e61-110">キーワードを示し `setLastError` ます。</span><span class="sxs-lookup"><span data-stu-id="e2e61-110">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="e2e61-111">キーワードを示し `nomangle` ます。</span><span class="sxs-lookup"><span data-stu-id="e2e61-111">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="e2e61-112">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="e2e61-112">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2e61-113">要件</span><span class="sxs-lookup"><span data-stu-id="e2e61-113">Requirements</span></span>  

 <span data-ttu-id="e2e61-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2e61-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2e61-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e2e61-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2e61-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e2e61-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2e61-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2e61-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e61-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2e61-118">See also</span></span>

- [<span data-ttu-id="e2e61-119">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="e2e61-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
