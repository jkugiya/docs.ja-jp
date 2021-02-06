---
description: '詳細について: IMetaDataEmit:: SetMethodImplFlags メソッド'
title: IMetaDataEmit::SetMethodImplFlags メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: ea7f3122a21c8651014e60de3629db87eeaf6260
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657836"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="6a70e-103">IMetaDataEmit::SetMethodImplFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="6a70e-103">IMetaDataEmit::SetMethodImplFlags Method</span></span>

<span data-ttu-id="6a70e-104">指定したトークンによって参照される、継承されたメソッドの実装のメタデータシグネチャを設定または更新します。</span><span class="sxs-lookup"><span data-stu-id="6a70e-104">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a70e-105">構文</span><span class="sxs-lookup"><span data-stu-id="6a70e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a70e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a70e-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="6a70e-107">から変更するメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="6a70e-107">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="6a70e-108">からメソッド実装機能を指定する [Cormethodimpl](cormethodimpl-enumeration.md) 列挙値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="6a70e-108">[in] A combination of the values of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a70e-109">要件</span><span class="sxs-lookup"><span data-stu-id="6a70e-109">Requirements</span></span>  

 <span data-ttu-id="6a70e-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a70e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a70e-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="6a70e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a70e-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="6a70e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a70e-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a70e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a70e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a70e-114">See also</span></span>

- [<span data-ttu-id="6a70e-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a70e-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6a70e-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a70e-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
