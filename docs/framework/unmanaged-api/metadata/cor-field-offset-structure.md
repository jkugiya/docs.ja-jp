---
description: '詳細情報: COR_FIELD_OFFSET 構造'
title: COR_FIELD_OFFSET 構造体
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 7976e79a5484fa467d7ac887a4e1a7fa324abf69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678628"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="82fd8-103">COR_FIELD_OFFSET 構造体</span><span class="sxs-lookup"><span data-stu-id="82fd8-103">COR_FIELD_OFFSET Structure</span></span>

<span data-ttu-id="82fd8-104">指定したフィールドのクラス内の相対位置を格納します。</span><span class="sxs-lookup"><span data-stu-id="82fd8-104">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82fd8-105">構文</span><span class="sxs-lookup"><span data-stu-id="82fd8-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="82fd8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="82fd8-106">Members</span></span>  
  
|<span data-ttu-id="82fd8-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="82fd8-107">Member</span></span>|<span data-ttu-id="82fd8-108">説明</span><span class="sxs-lookup"><span data-stu-id="82fd8-108">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="82fd8-109">`mdFieldDef`フィールドを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="82fd8-109">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="82fd8-110">クラス内のフィールドのオフセット。</span><span class="sxs-lookup"><span data-stu-id="82fd8-110">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82fd8-111">解説</span><span class="sxs-lookup"><span data-stu-id="82fd8-111">Remarks</span></span>  

 <span data-ttu-id="82fd8-112">[IMetaDataImport:: GetClassLayout](imetadataimport-getclasslayout-method.md) メソッドと [IMetaDataEmit:: SetClassLayout](imetadataemit-setclasslayout-method.md) メソッドは、型のパラメーターを受け取り `COR_FIELD_OFFSET` ます。</span><span class="sxs-lookup"><span data-stu-id="82fd8-112">[IMetaDataImport::GetClassLayout](imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82fd8-113">要件</span><span class="sxs-lookup"><span data-stu-id="82fd8-113">Requirements</span></span>  

 <span data-ttu-id="82fd8-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82fd8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82fd8-115">**ヘッダー:** CorHdr .h、Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="82fd8-115">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="82fd8-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82fd8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82fd8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="82fd8-117">See also</span></span>

- [<span data-ttu-id="82fd8-118">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="82fd8-118">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="82fd8-119">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82fd8-119">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="82fd8-120">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82fd8-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
