---
description: '詳細情報: IMetaDataEmit:: Merge メソッド'
title: IMetaDataEmit::Merge メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 6b78dd20555acf1eaf610ed05d8a37ab6cdeee5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745945"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="ccc60-103">IMetaDataEmit::Merge メソッド</span><span class="sxs-lookup"><span data-stu-id="ccc60-103">IMetaDataEmit::Merge Method</span></span>

<span data-ttu-id="ccc60-104">マージするスコープの一覧に、指定したインポートされたスコープを追加します。</span><span class="sxs-lookup"><span data-stu-id="ccc60-104">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccc60-105">構文</span><span class="sxs-lookup"><span data-stu-id="ccc60-105">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccc60-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ccc60-106">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="ccc60-107">からマージするインポートされたスコープを識別する [IMetaDataImport](imetadataimport-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ccc60-107">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="ccc60-108">からトークンの再マップを指定する [IMapToken](imaptoken-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ccc60-108">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="ccc60-109">からエラーを指定する [IUnknown](/cpp/atl/iunknown) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ccc60-109">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccc60-110">解説</span><span class="sxs-lookup"><span data-stu-id="ccc60-110">Remarks</span></span>  

 <span data-ttu-id="ccc60-111">[IMetaDataEmit:: MergeEnd](imetadataemit-mergeend-method.md)を呼び出して、メタデータの1つのスコープへのマージをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="ccc60-111">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccc60-112">要件</span><span class="sxs-lookup"><span data-stu-id="ccc60-112">Requirements</span></span>  

 <span data-ttu-id="ccc60-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccc60-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccc60-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="ccc60-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccc60-115">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="ccc60-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ccc60-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccc60-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc60-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccc60-117">See also</span></span>

- [<span data-ttu-id="ccc60-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ccc60-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ccc60-119">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ccc60-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
