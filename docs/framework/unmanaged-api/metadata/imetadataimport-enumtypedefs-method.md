---
description: '詳細について: IMetaDataImport:: EnumTypeDefs メソッド'
title: IMetaDataImport::EnumTypeDefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 28bd06b70573b780b687da9de0e13e17c29bb39a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670682"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="01886-103">IMetaDataImport::EnumTypeDefs メソッド</span><span class="sxs-lookup"><span data-stu-id="01886-103">IMetaDataImport::EnumTypeDefs Method</span></span>

<span data-ttu-id="01886-104">現在のスコープ内のすべての型を表す TypeDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="01886-104">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01886-105">構文</span><span class="sxs-lookup"><span data-stu-id="01886-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01886-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01886-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="01886-107">入出力新しい列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="01886-107">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="01886-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="01886-108">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="01886-109">からTypeDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="01886-109">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="01886-110">[in] `rTypeDefs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="01886-110">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="01886-111">入出力で返された TypeDef トークンの数 `rTypeDefs` 。</span><span class="sxs-lookup"><span data-stu-id="01886-111">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01886-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="01886-112">Return Value</span></span>  
  
|<span data-ttu-id="01886-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01886-113">HRESULT</span></span>|<span data-ttu-id="01886-114">説明</span><span class="sxs-lookup"><span data-stu-id="01886-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="01886-115">`EnumTypeDefs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="01886-115">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="01886-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="01886-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="01886-117">この場合、 `pcTypeDefs` は0になります。</span><span class="sxs-lookup"><span data-stu-id="01886-117">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01886-118">解説</span><span class="sxs-lookup"><span data-stu-id="01886-118">Remarks</span></span>  

 <span data-ttu-id="01886-119">TypeDef トークンは、クラスやインターフェイスなどの型、および拡張メカニズムを使用して追加された型を表します。</span><span class="sxs-lookup"><span data-stu-id="01886-119">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01886-120">要件</span><span class="sxs-lookup"><span data-stu-id="01886-120">Requirements</span></span>  

 <span data-ttu-id="01886-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01886-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01886-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="01886-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01886-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="01886-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01886-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01886-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01886-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="01886-125">See also</span></span>

- [<span data-ttu-id="01886-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01886-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="01886-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01886-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
