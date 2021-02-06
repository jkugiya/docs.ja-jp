---
description: '詳細について: IMetaDataEmit:: SetEventProps メソッド'
title: IMetaDataEmit::SetEventProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: 888999bc0f80e82e0d139eecac7152a94104ed7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658127"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="44124-103">IMetaDataEmit::SetEventProps メソッド</span><span class="sxs-lookup"><span data-stu-id="44124-103">IMetaDataEmit::SetEventProps Method</span></span>

<span data-ttu-id="44124-104">[IMetaDataEmit::D efineEvent](imetadataemit-defineevent-method.md)の前の呼び出しで定義されたイベントの指定された機能を設定または更新します。</span><span class="sxs-lookup"><span data-stu-id="44124-104">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44124-105">構文</span><span class="sxs-lookup"><span data-stu-id="44124-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,
    [in]  DWORD       dwEventFlags,
    [in]  mdToken     tkEventType,
    [in]  mdMethodDef mdAddOn,
    [in]  mdMethodDef mdRemoveOn,
    [in]  mdMethodDef mdFire,
    [in]  mdMethodDef rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44124-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="44124-106">Parameters</span></span>  

 `ev`  
 <span data-ttu-id="44124-107">からイベントトークン。</span><span class="sxs-lookup"><span data-stu-id="44124-107">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="44124-108">からイベントフラグ。</span><span class="sxs-lookup"><span data-stu-id="44124-108">[in] Event flags.</span></span> <span data-ttu-id="44124-109">これは、値のビットマスクです `CorEventAttr` 。</span><span class="sxs-lookup"><span data-stu-id="44124-109">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="44124-110">からイベントクラスのトークン。</span><span class="sxs-lookup"><span data-stu-id="44124-110">[in] The token for the event class.</span></span> <span data-ttu-id="44124-111">これは、 `mdTypeDef` またはトークンのいずれか `mdTypeRef` です。</span><span class="sxs-lookup"><span data-stu-id="44124-111">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="44124-112">からイベントの定期受信に使用するメソッド、または null。</span><span class="sxs-lookup"><span data-stu-id="44124-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="44124-113">からイベントのサブスクリプションを解除するために使用するメソッド、または null。</span><span class="sxs-lookup"><span data-stu-id="44124-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="44124-114">からイベントを発生させるために (派生クラスによって) 使用されるメソッド。</span><span class="sxs-lookup"><span data-stu-id="44124-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="44124-115">からイベントに関連付けられている他のメソッドのトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="44124-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="44124-116">配列の最後の要素は、である必要があり `mdMethodDefNil` ます。</span><span class="sxs-lookup"><span data-stu-id="44124-116">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44124-117">要件</span><span class="sxs-lookup"><span data-stu-id="44124-117">Requirements</span></span>  

 <span data-ttu-id="44124-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44124-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44124-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="44124-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44124-120">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="44124-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44124-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44124-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44124-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="44124-122">See also</span></span>

- [<span data-ttu-id="44124-123">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44124-123">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="44124-124">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44124-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
