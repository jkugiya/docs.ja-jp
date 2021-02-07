---
description: '詳細については、「IMetaDataTables:: メソッド」を参照してください。'
title: IMetaDataTables::GetStringHeapSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
ms.openlocfilehash: 0ec9f4e2768cc78163db67bc9099fc9cafae8c8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687780"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="499d3-103">IMetaDataTables::GetStringHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="499d3-103">IMetaDataTables::GetStringHeapSize Method</span></span>

<span data-ttu-id="499d3-104">文字列ヒープのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="499d3-104">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="499d3-105">構文</span><span class="sxs-lookup"><span data-stu-id="499d3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="499d3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="499d3-106">Parameters</span></span>  

 `pcbStrings`  
 <span data-ttu-id="499d3-107">入出力文字列ヒープのサイズ (バイト単位) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="499d3-107">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="499d3-108">要件</span><span class="sxs-lookup"><span data-stu-id="499d3-108">Requirements</span></span>  

 <span data-ttu-id="499d3-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="499d3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="499d3-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="499d3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="499d3-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="499d3-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="499d3-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="499d3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="499d3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="499d3-113">See also</span></span>

- [<span data-ttu-id="499d3-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="499d3-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="499d3-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="499d3-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
