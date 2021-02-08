---
description: '詳細について: IMetaDataEmit:: SetRVA メソッド'
title: IMetaDataEmit::SetRVA メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
ms.openlocfilehash: 52294250df2b7a677bb4ecb09ea0a97baca595a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771783"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="fc8a4-103">IMetaDataEmit::SetRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="fc8a4-103">IMetaDataEmit::SetRVA Method</span></span>

<span data-ttu-id="fc8a4-104">指定したメソッドの相対仮想アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="fc8a4-104">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8a4-105">構文</span><span class="sxs-lookup"><span data-stu-id="fc8a4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc8a4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc8a4-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="fc8a4-107">から対象のメソッドまたはメソッドの実装のトークン。</span><span class="sxs-lookup"><span data-stu-id="fc8a4-107">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="fc8a4-108">からコードまたはデータ領域のアドレス。</span><span class="sxs-lookup"><span data-stu-id="fc8a4-108">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc8a4-109">要件</span><span class="sxs-lookup"><span data-stu-id="fc8a4-109">Requirements</span></span>  

 <span data-ttu-id="fc8a4-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc8a4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc8a4-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="fc8a4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc8a4-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="fc8a4-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc8a4-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc8a4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8a4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc8a4-114">See also</span></span>

- [<span data-ttu-id="fc8a4-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc8a4-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="fc8a4-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc8a4-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
