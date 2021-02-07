---
description: '詳細について: IMetaDataEmit:: SaveToStream メソッド'
title: IMetaDataEmit::SaveToStream メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 104aa0b0dfcd0f4f9e8b87b4633880f6423f92d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706657"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="3de1f-103">IMetaDataEmit::SaveToStream メソッド</span><span class="sxs-lookup"><span data-stu-id="3de1f-103">IMetaDataEmit::SaveToStream Method</span></span>

<span data-ttu-id="3de1f-104">現在のスコープ内のすべてのメタデータを、指定したに保存し `IStream` ます。</span><span class="sxs-lookup"><span data-stu-id="3de1f-104">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de1f-105">構文</span><span class="sxs-lookup"><span data-stu-id="3de1f-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3de1f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3de1f-106">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="3de1f-107">から保存先の書き込み可能なストリーム。</span><span class="sxs-lookup"><span data-stu-id="3de1f-107">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="3de1f-108">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="3de1f-108">[in] Reserved.</span></span> <span data-ttu-id="3de1f-109">ゼロを指定してください。</span><span class="sxs-lookup"><span data-stu-id="3de1f-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3de1f-110">要件</span><span class="sxs-lookup"><span data-stu-id="3de1f-110">Requirements</span></span>  

 <span data-ttu-id="3de1f-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3de1f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3de1f-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="3de1f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3de1f-113">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="3de1f-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3de1f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3de1f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de1f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3de1f-115">See also</span></span>

- [<span data-ttu-id="3de1f-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3de1f-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3de1f-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3de1f-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
