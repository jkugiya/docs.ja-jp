---
description: '詳細については、次を参照してください: IMetaDataTables 許容:: GetBlob メソッド'
title: IMetaDataTables::GetBlob メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
ms.openlocfilehash: 733f94c280283e00b644fe7811d450efbc7e1e7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688391"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="8b1fe-103">IMetaDataTables::GetBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="8b1fe-103">IMetaDataTables::GetBlob Method</span></span>

<span data-ttu-id="8b1fe-104">指定した列インデックスにあるバイナリラージオブジェクト (BLOB) へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8b1fe-104">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b1fe-105">構文</span><span class="sxs-lookup"><span data-stu-id="8b1fe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b1fe-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8b1fe-106">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="8b1fe-107">から取得するメモリアドレス `ppData` 。</span><span class="sxs-lookup"><span data-stu-id="8b1fe-107">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="8b1fe-108">入出力のサイズ (バイト単位) へのポインター `ppData` 。</span><span class="sxs-lookup"><span data-stu-id="8b1fe-108">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="8b1fe-109">入出力取得したバイナリデータへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8b1fe-109">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b1fe-110">要件</span><span class="sxs-lookup"><span data-stu-id="8b1fe-110">Requirements</span></span>  

 <span data-ttu-id="8b1fe-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b1fe-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b1fe-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8b1fe-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b1fe-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8b1fe-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b1fe-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b1fe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b1fe-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b1fe-115">See also</span></span>

- [<span data-ttu-id="8b1fe-116">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b1fe-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="8b1fe-117">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b1fe-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
