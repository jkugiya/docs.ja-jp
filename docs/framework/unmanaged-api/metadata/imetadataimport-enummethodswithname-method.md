---
description: '詳細については、次を参照してください: IMetaDataImport:: Enummethod Withname メソッド'
title: IMetaDataImport::EnumMethodsWithName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: b77fc15bd7752b5b6b2b95d66a6bf04518616884
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745607"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="4707d-103">IMetaDataImport::EnumMethodsWithName メソッド</span><span class="sxs-lookup"><span data-stu-id="4707d-103">IMetaDataImport::EnumMethodsWithName Method</span></span>

<span data-ttu-id="4707d-104">指定された名前を持ち、指定された TypeDef トークンによって参照される型で定義されているメソッドを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4707d-104">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4707d-105">構文</span><span class="sxs-lookup"><span data-stu-id="4707d-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4707d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4707d-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="4707d-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4707d-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4707d-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4707d-108">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="4707d-109">から列挙するメソッドを持つ型を表す TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="4707d-109">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="4707d-110">から列挙型のスコープを制限する名前。</span><span class="sxs-lookup"><span data-stu-id="4707d-110">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="4707d-111">入出力MethodDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="4707d-111">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4707d-112">[in] `rMethods` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="4707d-112">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4707d-113">入出力で返される MethodDef トークンの数 `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="4707d-113">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4707d-114">解説</span><span class="sxs-lookup"><span data-stu-id="4707d-114">Remarks</span></span>  

 <span data-ttu-id="4707d-115">このメソッドは、フィールドとメソッドを列挙しますが、プロパティやイベントは列挙しません。</span><span class="sxs-lookup"><span data-stu-id="4707d-115">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="4707d-116">[IMetaDataImport:: enummethods](imetadataimport-enummethods-method.md)とは異なり、は、 `EnumMethodsWithName` 指定された名前を持たないすべてのメソッドトークンを破棄します。</span><span class="sxs-lookup"><span data-stu-id="4707d-116">Unlike [IMetaDataImport::EnumMethods](imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4707d-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="4707d-117">Return Value</span></span>  
  
|<span data-ttu-id="4707d-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4707d-118">HRESULT</span></span>|<span data-ttu-id="4707d-119">説明</span><span class="sxs-lookup"><span data-stu-id="4707d-119">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4707d-120">`EnumMethodsWithName` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="4707d-120">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4707d-121">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="4707d-121">There are no tokens to enumerate.</span></span> <span data-ttu-id="4707d-122">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="4707d-122">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4707d-123">要件</span><span class="sxs-lookup"><span data-stu-id="4707d-123">Requirements</span></span>  

 <span data-ttu-id="4707d-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4707d-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4707d-125">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4707d-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4707d-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4707d-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4707d-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4707d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4707d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="4707d-128">See also</span></span>

- [<span data-ttu-id="4707d-129">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4707d-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4707d-130">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4707d-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
