---
description: '詳細について: IMetaDataEmit::D efineMethodImpl メソッド'
title: IMetaDataEmit::DefineMethodImpl メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
ms.openlocfilehash: 9c79d713e61bfcc7b3191e570ed727b128422bf1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753407"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="57818-103">IMetaDataEmit::DefineMethodImpl メソッド</span><span class="sxs-lookup"><span data-stu-id="57818-103">IMetaDataEmit::DefineMethodImpl Method</span></span>

<span data-ttu-id="57818-104">インターフェイスから継承されたメソッドの実装の定義を作成し、そのメソッド実装定義にトークンを返します。</span><span class="sxs-lookup"><span data-stu-id="57818-104">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57818-105">構文</span><span class="sxs-lookup"><span data-stu-id="57818-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57818-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="57818-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="57818-107">から `mdTypedef` 実装するクラスのトークン。</span><span class="sxs-lookup"><span data-stu-id="57818-107">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="57818-108">から `mdMethodDef` `mdMemberRef` コード本体のまたはトークン。</span><span class="sxs-lookup"><span data-stu-id="57818-108">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="57818-109">から `mdMethodDef` `mdMemberRef` 実装されているインターフェイスメソッドのまたはトークン。</span><span class="sxs-lookup"><span data-stu-id="57818-109">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57818-110">要件</span><span class="sxs-lookup"><span data-stu-id="57818-110">Requirements</span></span>  

 <span data-ttu-id="57818-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57818-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57818-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="57818-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57818-113">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="57818-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57818-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57818-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57818-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="57818-115">See also</span></span>

- [<span data-ttu-id="57818-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57818-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="57818-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57818-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
