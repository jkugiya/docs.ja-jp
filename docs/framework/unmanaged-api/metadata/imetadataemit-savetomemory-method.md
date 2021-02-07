---
description: '詳細情報: IMetaDataEmit:: SaveToMemory メソッド'
title: IMetaDataEmit::SaveToMemory メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: b5fbca2c3ce06398de72bf2690108077545fef9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745802"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="52740-103">IMetaDataEmit::SaveToMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="52740-103">IMetaDataEmit::SaveToMemory Method</span></span>

<span data-ttu-id="52740-104">現在のスコープ内のすべてのメタデータを、指定したメモリ領域に保存します。</span><span class="sxs-lookup"><span data-stu-id="52740-104">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52740-105">構文</span><span class="sxs-lookup"><span data-stu-id="52740-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52740-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52740-106">Parameters</span></span>  

 `pbData`  
 <span data-ttu-id="52740-107">入出力メタデータの書き込みを開始するアドレス。</span><span class="sxs-lookup"><span data-stu-id="52740-107">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="52740-108">から割り当てられたメモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="52740-108">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52740-109">要件</span><span class="sxs-lookup"><span data-stu-id="52740-109">Requirements</span></span>  

 <span data-ttu-id="52740-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52740-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52740-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="52740-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52740-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="52740-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52740-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52740-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52740-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="52740-114">See also</span></span>

- [<span data-ttu-id="52740-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52740-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="52740-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52740-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
