---
description: '詳細については、「IMetaDataTables:: メソッド」を参照してください。'
title: IMetaDataTables::GetBlobHeapSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
ms.openlocfilehash: f6d5c7aeb5e1cc1f307d53d8f3e3cc99daa72311
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688313"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="625a4-103">IMetaDataTables::GetBlobHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="625a4-103">IMetaDataTables::GetBlobHeapSize Method</span></span>

<span data-ttu-id="625a4-104">バイナリラージオブジェクト (BLOB) ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="625a4-104">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="625a4-105">構文</span><span class="sxs-lookup"><span data-stu-id="625a4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="625a4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="625a4-106">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="625a4-107">入出力BLOB ヒープのサイズ (バイト単位) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="625a4-107">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="625a4-108">要件</span><span class="sxs-lookup"><span data-stu-id="625a4-108">Requirements</span></span>  

 <span data-ttu-id="625a4-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="625a4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="625a4-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="625a4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="625a4-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="625a4-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="625a4-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="625a4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="625a4-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="625a4-113">See also</span></span>

- [<span data-ttu-id="625a4-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="625a4-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="625a4-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="625a4-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
