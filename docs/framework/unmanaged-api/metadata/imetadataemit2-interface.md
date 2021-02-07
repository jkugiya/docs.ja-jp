---
description: 詳細については、「IMetaDataEmit2 インターフェイス」を参照してください。
title: IMetaDataEmit2 インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: db1880d64bf3b1e9084d6745251c174788a4afe7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745685"
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="85218-103">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85218-103">IMetaDataEmit2 Interface</span></span>

<span data-ttu-id="85218-104">[IMetaDataEmit](imetadataemit-interface.md)インターフェイスを拡張して、主にジェネリック型を操作できるようにします。</span><span class="sxs-lookup"><span data-stu-id="85218-104">Extends the [IMetaDataEmit](imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85218-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="85218-105">Methods</span></span>  
  
|<span data-ttu-id="85218-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="85218-106">Method</span></span>|<span data-ttu-id="85218-107">説明</span><span class="sxs-lookup"><span data-stu-id="85218-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85218-108">DefineGenericParam メソッド</span><span class="sxs-lookup"><span data-stu-id="85218-108">DefineGenericParam Method</span></span>](imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="85218-109">ジェネリック型パラメーターの定義を作成し、そのジェネリック型パラメーターへのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="85218-109">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="85218-110">DefineMethodSpec メソッド</span><span class="sxs-lookup"><span data-stu-id="85218-110">DefineMethodSpec Method</span></span>](imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="85218-111">メソッドのジェネリックインスタンスを作成し、その定義へのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="85218-111">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="85218-112">GetDeltaSaveSize メソッド</span><span class="sxs-lookup"><span data-stu-id="85218-112">GetDeltaSaveSize Method</span></span>](imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="85218-113">現在のエディットコンティニュセッションの変更を表すために必要なデータのサイズの差を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="85218-113">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="85218-114">ResetENCLog メソッド</span><span class="sxs-lookup"><span data-stu-id="85218-114">ResetENCLog Method</span></span>](imetadataemit2-resetenclog-method.md)|<span data-ttu-id="85218-115">エディットコンティニュログをリセットし、新しいセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="85218-115">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="85218-116">SaveDelta メソッド</span><span class="sxs-lookup"><span data-stu-id="85218-116">SaveDelta Method</span></span>](imetadataemit2-savedelta-method.md)|<span data-ttu-id="85218-117">現在のエディットコンティニュセッションから、指定したファイルへの変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="85218-117">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="85218-118">SaveDeltaToMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="85218-118">SaveDeltaToMemory Method</span></span>](imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="85218-119">現在のエディットコンティニュセッションの変更をメモリに保存します。</span><span class="sxs-lookup"><span data-stu-id="85218-119">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="85218-120">SaveDeltaToStream メソッド</span><span class="sxs-lookup"><span data-stu-id="85218-120">SaveDeltaToStream Method</span></span>](imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="85218-121">現在のエディットコンティニュセッションから、指定されたストリームに変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="85218-121">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="85218-122">SetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="85218-122">SetGenericParamProps Method</span></span>](imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="85218-123">指定したトークンによって参照されるジェネリックパラメーター定義のプロパティ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="85218-123">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85218-124">要件</span><span class="sxs-lookup"><span data-stu-id="85218-124">Requirements</span></span>  

 <span data-ttu-id="85218-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85218-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85218-126">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="85218-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85218-127">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="85218-127">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85218-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85218-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85218-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="85218-129">See also</span></span>

- [<span data-ttu-id="85218-130">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85218-130">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="85218-131">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85218-131">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
