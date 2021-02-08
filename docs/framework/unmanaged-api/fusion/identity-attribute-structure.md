---
description: '詳細情報: IDENTITY_ATTRIBUTE 構造'
title: IDENTITY_ATTRIBUTE 構造体
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
ms.openlocfilehash: 52610961ab202fc79351073eac1846a1a63889e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800176"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="9589a-103">IDENTITY_ATTRIBUTE 構造体</span><span class="sxs-lookup"><span data-stu-id="9589a-103">IDENTITY_ATTRIBUTE Structure</span></span>

<span data-ttu-id="9589a-104">[IDefinitionIdentity](idefinitionidentity-interface.md)インスタンスに関するメタデータ属性情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="9589a-104">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9589a-105">構文</span><span class="sxs-lookup"><span data-stu-id="9589a-105">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="9589a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9589a-106">Members</span></span>  
  
|<span data-ttu-id="9589a-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="9589a-107">Member</span></span>|<span data-ttu-id="9589a-108">説明</span><span class="sxs-lookup"><span data-stu-id="9589a-108">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="9589a-109">属性が含まれている名前空間を含む null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9589a-109">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="9589a-110">属性の名前を含む null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9589a-110">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="9589a-111">属性の値を格納している null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9589a-111">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9589a-112">解説</span><span class="sxs-lookup"><span data-stu-id="9589a-112">Remarks</span></span>  

 <span data-ttu-id="9589a-113">構造体には、 `IDENTITY_ATTRIBUTE` null で終わる文字列への3つのポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9589a-113">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="9589a-114">これら3つの文字列は、1つの属性を表します。</span><span class="sxs-lookup"><span data-stu-id="9589a-114">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="9589a-115">構造体のインスタンス `IDENTITY_ATTRIBUTE` は、 [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) 構造体のインスタンスに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="9589a-115">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="9589a-116">`IDENTITY_ATTRIBUTE`構造体には実際の文字列が含まれ、対応する構造体には、 `IDENTITY_ATTRIBUTE_BLOB` 構造体に示されている3つの文字列へのオフセットが一覧表示され `IDENTITY_ATTRIBUTE` ます。</span><span class="sxs-lookup"><span data-stu-id="9589a-116">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9589a-117">要件</span><span class="sxs-lookup"><span data-stu-id="9589a-117">Requirements</span></span>  

 <span data-ttu-id="9589a-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9589a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9589a-119">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="9589a-119">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="9589a-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9589a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9589a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9589a-121">See also</span></span>

- [<span data-ttu-id="9589a-122">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9589a-122">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="9589a-123">IDENTITY_ATTRIBUTE_BLOB 構造体</span><span class="sxs-lookup"><span data-stu-id="9589a-123">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="9589a-124">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="9589a-124">Fusion Structures</span></span>](fusion-structures.md)
