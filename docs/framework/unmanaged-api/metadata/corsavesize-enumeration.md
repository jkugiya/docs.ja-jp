---
description: '詳細については、次を参照してください: CorSaveSize 列挙型'
title: CorSaveSize 列挙型
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
ms.openlocfilehash: 47e2d4d77f58f8f1c2135da5867dfa47cedfd83d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784224"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="edac9-103">CorSaveSize 列挙型</span><span class="sxs-lookup"><span data-stu-id="edac9-103">CorSaveSize Enumeration</span></span>

<span data-ttu-id="edac9-104">保存操作のサイズの照会で要求される精度のレベルを示す値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="edac9-104">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edac9-105">構文</span><span class="sxs-lookup"><span data-stu-id="edac9-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="edac9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="edac9-106">Members</span></span>  
  
|<span data-ttu-id="edac9-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="edac9-107">Member</span></span>|<span data-ttu-id="edac9-108">説明</span><span class="sxs-lookup"><span data-stu-id="edac9-108">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="edac9-109">戻り値が正確であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="edac9-109">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="edac9-110">戻り値を推定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="edac9-110">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="edac9-111">破棄可能な型を削除する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="edac9-111">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="edac9-112">要件</span><span class="sxs-lookup"><span data-stu-id="edac9-112">Requirements</span></span>  

 <span data-ttu-id="edac9-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="edac9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edac9-114">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="edac9-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="edac9-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="edac9-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="edac9-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edac9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edac9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="edac9-117">See also</span></span>

- [<span data-ttu-id="edac9-118">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="edac9-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
