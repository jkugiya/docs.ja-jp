---
description: '詳細について: IMetaDataEmit:: GetTokenFromSig メソッド'
title: IMetaDataEmit::GetTokenFromSig メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
ms.openlocfilehash: 3b9b38389a2bf78a65baa2cf96e3a422c54d0bcb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783925"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="5a6e2-103">IMetaDataEmit::GetTokenFromSig メソッド</span><span class="sxs-lookup"><span data-stu-id="5a6e2-103">IMetaDataEmit::GetTokenFromSig Method</span></span>

<span data-ttu-id="5a6e2-104">指定したメタデータシグネチャのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="5a6e2-104">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a6e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="5a6e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a6e2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5a6e2-106">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="5a6e2-107">から永続化および格納される署名。</span><span class="sxs-lookup"><span data-stu-id="5a6e2-107">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="5a6e2-108">からのバイト数 `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="5a6e2-108">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="5a6e2-109">入出力 `mdSignature` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="5a6e2-109">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a6e2-110">要件</span><span class="sxs-lookup"><span data-stu-id="5a6e2-110">Requirements</span></span>  

 <span data-ttu-id="5a6e2-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a6e2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a6e2-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="5a6e2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a6e2-113">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="5a6e2-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a6e2-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a6e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a6e2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a6e2-115">See also</span></span>

- [<span data-ttu-id="5a6e2-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a6e2-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5a6e2-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a6e2-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
