---
description: '詳細については、次を参照してください: Eclrassemblyidentity Flags 列挙型'
title: ECLRAssemblyIdentityFlags 列挙型
ms.date: 03/30/2017
api_name:
- ECLRAssemblyIdentityFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECLRAssemblyIdentityFlags
helpviewer_keywords:
- ECLRAssemblyIdentityFlags enumeration [.NET Framework hosting]
ms.assetid: d1e0b654-ccaf-4fa2-9aa3-8e007813c84d
topic_type:
- apiref
ms.openlocfilehash: d0211c6116b566964aeca29a52aede7e232f5556
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785580"
---
# <a name="eclrassemblyidentityflags-enumeration"></a><span data-ttu-id="5682c-103">ECLRAssemblyIdentityFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="5682c-103">ECLRAssemblyIdentityFlags Enumeration</span></span>

<span data-ttu-id="5682c-104">アセンブリの id の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="5682c-104">Indicates the type of an assembly's identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5682c-105">構文</span><span class="sxs-lookup"><span data-stu-id="5682c-105">Syntax</span></span>  
  
```cpp  
typedef enum _CLRAssemblyIdentityFlags {  
    CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT = 0  
} ECLRAssemblyIdentityFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5682c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="5682c-106">Members</span></span>  
  
|<span data-ttu-id="5682c-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="5682c-107">Member</span></span>|<span data-ttu-id="5682c-108">説明</span><span class="sxs-lookup"><span data-stu-id="5682c-108">Description</span></span>|  
|------------|-----------------|  
|`CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT`|<span data-ttu-id="5682c-109">Id は正規化されます。</span><span class="sxs-lookup"><span data-stu-id="5682c-109">The identity is canonicalized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5682c-110">要件</span><span class="sxs-lookup"><span data-stu-id="5682c-110">Requirements</span></span>  

 <span data-ttu-id="5682c-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5682c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5682c-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5682c-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5682c-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5682c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5682c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5682c-114">See also</span></span>

- [<span data-ttu-id="5682c-115">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="5682c-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
