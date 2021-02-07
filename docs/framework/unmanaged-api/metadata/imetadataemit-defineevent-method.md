---
description: '詳細について: IMetaDataEmit::D efineEvent メソッド'
title: IMetaDataEmit::DefineEvent メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: f96f3a5b2ed16ba83223312af82cac7688cebfa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753472"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="0be20-103">IMetaDataEmit::DefineEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="0be20-103">IMetaDataEmit::DefineEvent Method</span></span>

<span data-ttu-id="0be20-104">指定したメタデータシグネチャを持つイベントの定義を作成し、そのイベント定義へのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0be20-104">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0be20-105">構文</span><span class="sxs-lookup"><span data-stu-id="0be20-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineEvent (
    [in]  mdTypeDef    td,
    [in]  LPCWSTR      szEvent,
    [in]  DWORD        dwEventFlags,
    [in]  mdToken      tkEventType,
    [in]  mdMethodDef  mdAddOn,
    [in]  mdMethodDef  mdRemoveOn,
    [in]  mdMethodDef  mdFire,
    [in]  mdMethodDef  rmdOtherMethods[],
    [out] mdEvent      *pmdEvent
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0be20-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0be20-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="0be20-107">からターゲットクラスまたはインターフェイスのトークン。</span><span class="sxs-lookup"><span data-stu-id="0be20-107">[in] The token for the target class or interface.</span></span> <span data-ttu-id="0be20-108">これは、 `mdTypeDef` またはトークンのいずれか `mdTypeDefNil` です。</span><span class="sxs-lookup"><span data-stu-id="0be20-108">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="0be20-109">からイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="0be20-109">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="0be20-110">からイベントフラグ。</span><span class="sxs-lookup"><span data-stu-id="0be20-110">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="0be20-111">からイベントクラスのトークン。</span><span class="sxs-lookup"><span data-stu-id="0be20-111">[in] The token for the event class.</span></span> <span data-ttu-id="0be20-112">これは `mdTypeDef` 、、、 `mdTypeRef` または `mdTokenNil` トークンです。</span><span class="sxs-lookup"><span data-stu-id="0be20-112">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="0be20-113">からイベントの定期受信に使用するメソッド、または null。</span><span class="sxs-lookup"><span data-stu-id="0be20-113">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="0be20-114">からイベントのサブスクリプションを解除するために使用するメソッド、または null。</span><span class="sxs-lookup"><span data-stu-id="0be20-114">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="0be20-115">からイベントを発生させるために (派生クラスによって) 使用されるメソッド。</span><span class="sxs-lookup"><span data-stu-id="0be20-115">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="0be20-116">からイベントに関連付けられている他のメソッドのトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="0be20-116">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="0be20-117">配列がトークンで終了してい `mdMethodDefNil` ます。</span><span class="sxs-lookup"><span data-stu-id="0be20-117">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="0be20-118">入出力イベントに割り当てられたメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="0be20-118">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0be20-119">要件</span><span class="sxs-lookup"><span data-stu-id="0be20-119">Requirements</span></span>  

 <span data-ttu-id="0be20-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0be20-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0be20-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0be20-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0be20-122">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0be20-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0be20-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0be20-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0be20-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="0be20-124">See also</span></span>

- [<span data-ttu-id="0be20-125">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0be20-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0be20-126">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0be20-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
