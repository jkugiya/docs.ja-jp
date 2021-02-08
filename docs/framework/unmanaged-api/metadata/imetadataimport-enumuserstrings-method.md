---
description: '詳細情報: IMetaDataImport:: EnumUserStrings メソッド'
title: IMetaDataImport::EnumUserStrings メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
ms.openlocfilehash: a4ead696f3d924fef9ebfed5c4f1eb97eb13e14e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799318"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="96082-103">IMetaDataImport::EnumUserStrings メソッド</span><span class="sxs-lookup"><span data-stu-id="96082-103">IMetaDataImport::EnumUserStrings Method</span></span>

<span data-ttu-id="96082-104">現在のメタデータ スコープ内にあるハードコーディングされた文字列を表す String トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="96082-104">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96082-105">構文</span><span class="sxs-lookup"><span data-stu-id="96082-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96082-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96082-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="96082-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="96082-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="96082-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="96082-108">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="96082-109">入出力文字列トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="96082-109">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="96082-110">[in] `rStrings` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="96082-110">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="96082-111">入出力で返された文字列トークンの数 `rStrings` 。</span><span class="sxs-lookup"><span data-stu-id="96082-111">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96082-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="96082-112">Return Value</span></span>  
  
|<span data-ttu-id="96082-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96082-113">HRESULT</span></span>|<span data-ttu-id="96082-114">説明</span><span class="sxs-lookup"><span data-stu-id="96082-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="96082-115">`EnumUserStrings` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="96082-115">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="96082-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="96082-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="96082-117">この場合、 `pcStrings` は0になります。</span><span class="sxs-lookup"><span data-stu-id="96082-117">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96082-118">解説</span><span class="sxs-lookup"><span data-stu-id="96082-118">Remarks</span></span>  

 <span data-ttu-id="96082-119">文字列トークンは、 [IMetaDataEmit::D efineUserString](imetadataemit-defineuserstring-method.md) メソッドによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="96082-119">The String tokens are created by the [IMetaDataEmit::DefineUserString](imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="96082-120">このメソッドは、コンパイラではなく、メタデータブラウザーによって使用されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="96082-120">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96082-121">要件</span><span class="sxs-lookup"><span data-stu-id="96082-121">Requirements</span></span>  

 <span data-ttu-id="96082-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96082-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96082-123">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="96082-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96082-124">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="96082-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96082-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96082-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96082-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="96082-126">See also</span></span>

- [<span data-ttu-id="96082-127">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96082-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="96082-128">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96082-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
