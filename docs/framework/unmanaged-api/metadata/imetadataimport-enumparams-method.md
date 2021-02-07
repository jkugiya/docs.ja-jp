---
description: '詳細について: IMetaDataImport:: EnumParams メソッド'
title: IMetaDataImport::EnumParams メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: 3402e0277631cb54232269ad96194583cc466c4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688794"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="f6cee-103">IMetaDataImport::EnumParams メソッド</span><span class="sxs-lookup"><span data-stu-id="f6cee-103">IMetaDataImport::EnumParams Method</span></span>

<span data-ttu-id="f6cee-104">指定した MethodDef トークンによって参照されるメソッドのパラメーターを表す ParamDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="f6cee-104">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6cee-105">構文</span><span class="sxs-lookup"><span data-stu-id="f6cee-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6cee-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f6cee-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="f6cee-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f6cee-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f6cee-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6cee-108">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="f6cee-109">から列挙するパラメーターを使用してメソッドを表す MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="f6cee-109">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="f6cee-110">入出力ParamDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="f6cee-110">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f6cee-111">[in] `rParams` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="f6cee-111">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f6cee-112">入出力で返された ParamDef トークンの数 `rParams` 。</span><span class="sxs-lookup"><span data-stu-id="f6cee-112">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6cee-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="f6cee-113">Return Value</span></span>  
  
|<span data-ttu-id="f6cee-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6cee-114">HRESULT</span></span>|<span data-ttu-id="f6cee-115">説明</span><span class="sxs-lookup"><span data-stu-id="f6cee-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f6cee-116">`EnumParams` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f6cee-116">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f6cee-117">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="f6cee-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="f6cee-118">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="f6cee-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6cee-119">要件</span><span class="sxs-lookup"><span data-stu-id="f6cee-119">Requirements</span></span>  

 <span data-ttu-id="f6cee-120">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cee-120">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6cee-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f6cee-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6cee-122">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f6cee-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6cee-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6cee-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6cee-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6cee-124">See also</span></span>

- [<span data-ttu-id="f6cee-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6cee-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f6cee-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6cee-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
