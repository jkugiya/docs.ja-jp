---
description: '詳細情報: IMetaDataImport:: EnumMethods メソッド'
title: IMetaDataImport::EnumMethods メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
ms.openlocfilehash: 4fce3593d088a8d401335869eb49e598ac4c3fd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670678"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="8b508-103">IMetaDataImport::EnumMethods メソッド</span><span class="sxs-lookup"><span data-stu-id="8b508-103">IMetaDataImport::EnumMethods Method</span></span>

<span data-ttu-id="8b508-104">指定した型のメソッドを表す MethodDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="8b508-104">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b508-105">構文</span><span class="sxs-lookup"><span data-stu-id="8b508-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b508-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8b508-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="8b508-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8b508-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8b508-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b508-108">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="8b508-109">から列挙するメソッドを持つ型を表す TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="8b508-109">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="8b508-110">入出力MethodDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="8b508-110">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8b508-111">からMethodDef 配列の最大サイズ `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="8b508-111">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8b508-112">入出力で返される MethodDef トークンの数 `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="8b508-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b508-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="8b508-113">Return Value</span></span>  
  
|<span data-ttu-id="8b508-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b508-114">HRESULT</span></span>|<span data-ttu-id="8b508-115">説明</span><span class="sxs-lookup"><span data-stu-id="8b508-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8b508-116">`EnumMethods` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="8b508-116">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8b508-117">列挙する MethodDef トークンがありません。</span><span class="sxs-lookup"><span data-stu-id="8b508-117">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="8b508-118">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="8b508-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b508-119">要件</span><span class="sxs-lookup"><span data-stu-id="8b508-119">Requirements</span></span>  

 <span data-ttu-id="8b508-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b508-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b508-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8b508-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b508-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8b508-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b508-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b508-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b508-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b508-124">See also</span></span>

- [<span data-ttu-id="8b508-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b508-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8b508-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b508-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
