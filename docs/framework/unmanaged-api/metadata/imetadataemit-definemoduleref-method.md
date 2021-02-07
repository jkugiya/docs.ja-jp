---
description: '詳細について: IMetaDataEmit::D efineModuleRef メソッド'
title: IMetaDataEmit::DefineModuleRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
ms.openlocfilehash: b5af5e458f749d2315612bbe9419f037331f8c46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753394"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="d124a-103">IMetaDataEmit::DefineModuleRef メソッド</span><span class="sxs-lookup"><span data-stu-id="d124a-103">IMetaDataEmit::DefineModuleRef Method</span></span>

<span data-ttu-id="d124a-104">指定された名前を持つモジュールのメタデータシグネチャを作成します。</span><span class="sxs-lookup"><span data-stu-id="d124a-104">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d124a-105">構文</span><span class="sxs-lookup"><span data-stu-id="d124a-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d124a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d124a-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="d124a-107">から他のメタデータファイルの名前 (通常は DLL)。</span><span class="sxs-lookup"><span data-stu-id="d124a-107">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="d124a-108">これはファイル名のみです。</span><span class="sxs-lookup"><span data-stu-id="d124a-108">This is the file name only.</span></span> <span data-ttu-id="d124a-109">完全なパス名は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="d124a-109">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="d124a-110">入出力割り当てられた `mdModuleRef` トークン。</span><span class="sxs-lookup"><span data-stu-id="d124a-110">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d124a-111">要件</span><span class="sxs-lookup"><span data-stu-id="d124a-111">Requirements</span></span>  

 <span data-ttu-id="d124a-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d124a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d124a-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="d124a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d124a-114">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="d124a-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d124a-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d124a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d124a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d124a-116">See also</span></span>

- [<span data-ttu-id="d124a-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d124a-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d124a-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d124a-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
