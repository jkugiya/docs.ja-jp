---
description: '詳細情報: IMetaDataEmit:: Save メソッド'
title: IMetaDataEmit::Save メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: bf8675540ae2c851d2b6ed14883c9b75e9631903
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745867"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="b4d7f-103">IMetaDataEmit::Save メソッド</span><span class="sxs-lookup"><span data-stu-id="b4d7f-103">IMetaDataEmit::Save Method</span></span>

<span data-ttu-id="b4d7f-104">現在のスコープ内のすべてのメタデータを、指定したアドレスにあるファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="b4d7f-104">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d7f-105">構文</span><span class="sxs-lookup"><span data-stu-id="b4d7f-105">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4d7f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b4d7f-106">Parameters</span></span>  

 `wzFile`  
 <span data-ttu-id="b4d7f-107">から保存先のファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="b4d7f-107">[in] The name of the file to save to.</span></span> <span data-ttu-id="b4d7f-108">この値が null の場合、メモリ内のコピーは、使用された最後の場所に保存されます。</span><span class="sxs-lookup"><span data-stu-id="b4d7f-108">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="b4d7f-109">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="b4d7f-109">[in] Reserved.</span></span> <span data-ttu-id="b4d7f-110">ゼロを指定してください。</span><span class="sxs-lookup"><span data-stu-id="b4d7f-110">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d7f-111">要件</span><span class="sxs-lookup"><span data-stu-id="b4d7f-111">Requirements</span></span>  

 <span data-ttu-id="b4d7f-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4d7f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d7f-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b4d7f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b4d7f-114">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b4d7f-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4d7f-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d7f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d7f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4d7f-116">See also</span></span>

- [<span data-ttu-id="b4d7f-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4d7f-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b4d7f-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4d7f-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
