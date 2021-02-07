---
description: '詳細については、「IMetaDataTables:: メソッド」を参照してください。'
title: IMetaDataTables::GetUserStringHeapSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
ms.openlocfilehash: 7e6f3eed7803f52e6bde888852c4971900f0868c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687624"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="94d2b-103">IMetaDataTables::GetUserStringHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="94d2b-103">IMetaDataTables::GetUserStringHeapSize Method</span></span>

<span data-ttu-id="94d2b-104">ユーザー文字列ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="94d2b-104">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d2b-105">構文</span><span class="sxs-lookup"><span data-stu-id="94d2b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94d2b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94d2b-106">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="94d2b-107">入出力ユーザー文字列ヒープのサイズ (バイト単位) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="94d2b-107">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94d2b-108">要件</span><span class="sxs-lookup"><span data-stu-id="94d2b-108">Requirements</span></span>  

 <span data-ttu-id="94d2b-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94d2b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94d2b-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="94d2b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94d2b-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="94d2b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="94d2b-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94d2b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d2b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="94d2b-113">See also</span></span>

- [<span data-ttu-id="94d2b-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94d2b-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="94d2b-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94d2b-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
