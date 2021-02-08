---
description: '詳細について: IMetaDataEmit2:: SaveDeltaToMemory メソッド'
title: IMetaDataEmit2::SaveDeltaToMemory メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
ms.openlocfilehash: 3ef01889df6dede85947508ca08635c95d655666
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771757"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="f7844-103">IMetaDataEmit2::SaveDeltaToMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="f7844-103">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>

<span data-ttu-id="f7844-104">現在のエディットコンティニュセッションの変更をメモリに保存します。</span><span class="sxs-lookup"><span data-stu-id="f7844-104">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7844-105">構文</span><span class="sxs-lookup"><span data-stu-id="f7844-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7844-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f7844-106">Parameters</span></span>  

 `pbData`  
 <span data-ttu-id="f7844-107">入出力メタデータデルタの書き込みを開始するアドレス。</span><span class="sxs-lookup"><span data-stu-id="f7844-107">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="f7844-108">から変更のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f7844-108">[in] The size of the changes.</span></span> <span data-ttu-id="f7844-109">サイズを確認するには、 [IMetaDataEmit2:: GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7844-109">Use [IMetaDataEmit2::GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7844-110">要件</span><span class="sxs-lookup"><span data-stu-id="f7844-110">Requirements</span></span>  

 <span data-ttu-id="f7844-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7844-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7844-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f7844-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7844-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f7844-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7844-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7844-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7844-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7844-115">See also</span></span>

- [<span data-ttu-id="f7844-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7844-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="f7844-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7844-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
