---
description: '詳細について: IMetaDataImport:: Enumtyp Ecs メソッド'
title: IMetaDataImport::EnumTypeSpecs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 7446bbf3296ffb6cfa3a20f594b4a7da22acff5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799344"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="55a83-103">IMetaDataImport::EnumTypeSpecs メソッド</span><span class="sxs-lookup"><span data-stu-id="55a83-103">IMetaDataImport::EnumTypeSpecs Method</span></span>

<span data-ttu-id="55a83-104">現在のメタデータ スコープに定義されている TypeSpec トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="55a83-104">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a83-105">構文</span><span class="sxs-lookup"><span data-stu-id="55a83-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55a83-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55a83-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="55a83-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="55a83-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="55a83-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="55a83-108">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="55a83-109">入出力TypeSpec トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="55a83-109">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="55a83-110">[in] `rTypeSpecs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="55a83-110">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="55a83-111">入出力で返された TypeSpec トークンの数 `rTypeSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="55a83-111">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55a83-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="55a83-112">Return Value</span></span>  
  
|<span data-ttu-id="55a83-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55a83-113">HRESULT</span></span>|<span data-ttu-id="55a83-114">説明</span><span class="sxs-lookup"><span data-stu-id="55a83-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="55a83-115">`EnumTypeSpecs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="55a83-115">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="55a83-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="55a83-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="55a83-117">この場合、 `pcTypeSpecs` は0になります。</span><span class="sxs-lookup"><span data-stu-id="55a83-117">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55a83-118">解説</span><span class="sxs-lookup"><span data-stu-id="55a83-118">Remarks</span></span>  

 <span data-ttu-id="55a83-119">TypeSpec トークンは、 [IMetaDataEmit:: GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) メソッドによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="55a83-119">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55a83-120">要件</span><span class="sxs-lookup"><span data-stu-id="55a83-120">Requirements</span></span>  

 <span data-ttu-id="55a83-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55a83-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55a83-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="55a83-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55a83-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="55a83-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55a83-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55a83-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a83-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="55a83-125">See also</span></span>

- [<span data-ttu-id="55a83-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55a83-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="55a83-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55a83-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
