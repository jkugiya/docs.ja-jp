---
description: '詳細については、「IMetaDataTables:: メソッド」を参照してください。'
title: IMetaDataTables::GetGuidHeapSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
ms.openlocfilehash: bbf2fd7e083c5a0a42ad69ab685b3e1aa8321d68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688144"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="1e243-103">IMetaDataTables::GetGuidHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="1e243-103">IMetaDataTables::GetGuidHeapSize Method</span></span>

<span data-ttu-id="1e243-104">GUID ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e243-104">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e243-105">構文</span><span class="sxs-lookup"><span data-stu-id="1e243-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e243-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e243-106">Parameters</span></span>  

 `pcbGuids`  
 <span data-ttu-id="1e243-107">入出力GUID ヒープのサイズ (バイト単位) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e243-107">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e243-108">要件</span><span class="sxs-lookup"><span data-stu-id="1e243-108">Requirements</span></span>  

 <span data-ttu-id="1e243-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e243-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e243-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1e243-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e243-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e243-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e243-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e243-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e243-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e243-113">See also</span></span>

- [<span data-ttu-id="1e243-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e243-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="1e243-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e243-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
