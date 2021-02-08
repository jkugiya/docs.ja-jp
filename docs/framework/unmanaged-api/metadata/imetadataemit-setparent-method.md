---
description: '詳細について: IMetaDataEmit:: SetParent メソッド'
title: IMetaDataEmit::SetParent メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: 9025d4a37de85a0e657059f63ef781dc4377c036
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772004"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="4e168-103">IMetaDataEmit::SetParent メソッド</span><span class="sxs-lookup"><span data-stu-id="4e168-103">IMetaDataEmit::SetParent Method</span></span>

<span data-ttu-id="4e168-104">前の[IMetaDataEmit::D efineTypeDef](imetadataemit-definetypedef-method.md)の呼び出しで定義されているように、 [IMetaDataEmit::D efinememberref](imetadataemit-definememberref-method.md)の前の呼び出しで定義されている指定されたメンバーが、指定された型のメンバーであることを確立します。</span><span class="sxs-lookup"><span data-stu-id="4e168-104">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e168-105">構文</span><span class="sxs-lookup"><span data-stu-id="4e168-105">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e168-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4e168-106">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="4e168-107">から `mdMemberRef` 新しい親を受け取るトークン。</span><span class="sxs-lookup"><span data-stu-id="4e168-107">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="4e168-108">から `mdToken` 新しい親の。</span><span class="sxs-lookup"><span data-stu-id="4e168-108">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e168-109">要件</span><span class="sxs-lookup"><span data-stu-id="4e168-109">Requirements</span></span>  

 <span data-ttu-id="4e168-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e168-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e168-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4e168-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e168-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="4e168-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e168-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e168-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e168-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e168-114">See also</span></span>

- [<span data-ttu-id="4e168-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4e168-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4e168-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4e168-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
