---
description: '詳細情報: COR_FIELD 構造'
title: COR_FIELD 構造体
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
ms.openlocfilehash: a3e9dcc2a5c3bb2abae42dab4292c1d285df5ad7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747111"
---
# <a name="cor_field-structure"></a><span data-ttu-id="3d551-103">COR_FIELD 構造体</span><span class="sxs-lookup"><span data-stu-id="3d551-103">COR_FIELD Structure</span></span>

<span data-ttu-id="3d551-104">オブジェクトのフィールドに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="3d551-104">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d551-105">構文</span><span class="sxs-lookup"><span data-stu-id="3d551-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="3d551-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3d551-106">Members</span></span>  
  
|<span data-ttu-id="3d551-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="3d551-107">Member</span></span>|<span data-ttu-id="3d551-108">説明</span><span class="sxs-lookup"><span data-stu-id="3d551-108">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="3d551-109">`mdFieldDef`フィールド情報を取得するために使用できるトークン。</span><span class="sxs-lookup"><span data-stu-id="3d551-109">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="3d551-110">オブジェクト内のフィールドデータへのオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="3d551-110">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="3d551-111">このフィールドの型を識別する [COR_TYPEID](cor-typeid-structure.md) 値。</span><span class="sxs-lookup"><span data-stu-id="3d551-111">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="3d551-112">フィールドの型を示す CorElementType 列挙値。</span><span class="sxs-lookup"><span data-stu-id="3d551-112">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d551-113">解説</span><span class="sxs-lookup"><span data-stu-id="3d551-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d551-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="3d551-114">Requirements</span></span>  

 <span data-ttu-id="3d551-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d551-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d551-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d551-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d551-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d551-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d551-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d551-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d551-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d551-119">See also</span></span>

- [<span data-ttu-id="3d551-120">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="3d551-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="3d551-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3d551-121">Debugging</span></span>](index.md)
