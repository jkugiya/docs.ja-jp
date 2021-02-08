---
description: '詳細については、次を参照してください: CorLinkerOptions 列挙型'
title: CorLinkerOptions 列挙型
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
ms.openlocfilehash: 40f8ba6382fc937a072e01f9b3f6f89056f628db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784432"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="50b0f-103">CorLinkerOptions 列挙型</span><span class="sxs-lookup"><span data-stu-id="50b0f-103">CorLinkerOptions Enumeration</span></span>

<span data-ttu-id="50b0f-104">メタデータ リンカーのオプションを選択するためのフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="50b0f-104">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50b0f-105">構文</span><span class="sxs-lookup"><span data-stu-id="50b0f-105">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="50b0f-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="50b0f-106">Members</span></span>  
  
|<span data-ttu-id="50b0f-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="50b0f-107">Member</span></span>|<span data-ttu-id="50b0f-108">説明</span><span class="sxs-lookup"><span data-stu-id="50b0f-108">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="50b0f-109">プライベート型とグローバル関数は保持されません。</span><span class="sxs-lookup"><span data-stu-id="50b0f-109">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="50b0f-110">プライベート型とグローバル関数が保持されます。</span><span class="sxs-lookup"><span data-stu-id="50b0f-110">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50b0f-111">要件</span><span class="sxs-lookup"><span data-stu-id="50b0f-111">Requirements</span></span>  

 <span data-ttu-id="50b0f-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50b0f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50b0f-113">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="50b0f-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="50b0f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50b0f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b0f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="50b0f-115">See also</span></span>

- [<span data-ttu-id="50b0f-116">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="50b0f-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
