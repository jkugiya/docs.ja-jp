---
description: '詳細情報: IMetaDataImport:: EnumEvents メソッド'
title: IMetaDataImport::EnumEvents メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: e944c15a19314b315e01493836ce078fccc917eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799409"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="11a8a-103">IMetaDataImport::EnumEvents メソッド</span><span class="sxs-lookup"><span data-stu-id="11a8a-103">IMetaDataImport::EnumEvents Method</span></span>

<span data-ttu-id="11a8a-104">指定した TypeDef トークンのイベント定義トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="11a8a-104">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a8a-105">構文</span><span class="sxs-lookup"><span data-stu-id="11a8a-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11a8a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11a8a-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="11a8a-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="11a8a-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="11a8a-108">からイベント定義を列挙する TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="11a8a-108">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="11a8a-109">入出力返されたイベントの配列。</span><span class="sxs-lookup"><span data-stu-id="11a8a-109">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="11a8a-110">[in] `rEvents` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="11a8a-110">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="11a8a-111">入出力で返されるイベントの実際の数 `rEvents` 。</span><span class="sxs-lookup"><span data-stu-id="11a8a-111">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11a8a-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="11a8a-112">Return Value</span></span>  
  
|<span data-ttu-id="11a8a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11a8a-113">HRESULT</span></span>|<span data-ttu-id="11a8a-114">説明</span><span class="sxs-lookup"><span data-stu-id="11a8a-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="11a8a-115">`EnumEvents` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="11a8a-115">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="11a8a-116">列挙するイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="11a8a-116">There are no events to enumerate.</span></span> <span data-ttu-id="11a8a-117">この場合、 `pcEvents` は0になります。</span><span class="sxs-lookup"><span data-stu-id="11a8a-117">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11a8a-118">要件</span><span class="sxs-lookup"><span data-stu-id="11a8a-118">Requirements</span></span>  

 <span data-ttu-id="11a8a-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11a8a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11a8a-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="11a8a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11a8a-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="11a8a-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11a8a-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11a8a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a8a-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="11a8a-123">See also</span></span>

- [<span data-ttu-id="11a8a-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11a8a-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="11a8a-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11a8a-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
