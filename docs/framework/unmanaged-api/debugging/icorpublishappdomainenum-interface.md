---
description: 詳細については、「ICorPublishAppDomainEnum インターフェイス」を参照してください。
title: ICorPublishAppDomainEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
ms.openlocfilehash: 4e84af576103a792308fd44f903f2ae4daa5d736
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721789"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="44628-103">ICorPublishAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44628-103">ICorPublishAppDomainEnum Interface</span></span>

<span data-ttu-id="44628-104">プロセス内に現在存在する[ICorPublishAppDomain](icorpublishappdomain-interface.md)オブジェクトのコレクションを走査するメソッドを提供する[ICorPublishEnum](icorpublishenum-interface.md)インターフェイスのサブクラス。</span><span class="sxs-lookup"><span data-stu-id="44628-104">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44628-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="44628-105">Methods</span></span>  
  
|<span data-ttu-id="44628-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="44628-106">Method</span></span>|<span data-ttu-id="44628-107">説明</span><span class="sxs-lookup"><span data-stu-id="44628-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44628-108">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="44628-108">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="44628-109">現在の位置から開始して、指定した数の `ICorPublishAppDomain` インスタンスをコレクションから取得します。</span><span class="sxs-lookup"><span data-stu-id="44628-109">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44628-110">解説</span><span class="sxs-lookup"><span data-stu-id="44628-110">Remarks</span></span>  

 <span data-ttu-id="44628-111">インターフェイスは、 `ICorPublishAppDomainEnum` 抽象インターフェイス [ICorPublishEnum](icorpublishenum-interface.md)のメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="44628-111">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44628-112">要件</span><span class="sxs-lookup"><span data-stu-id="44628-112">Requirements</span></span>  

 <span data-ttu-id="44628-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44628-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44628-114">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="44628-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="44628-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44628-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44628-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44628-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44628-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="44628-117">See also</span></span>

- [<span data-ttu-id="44628-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="44628-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="44628-119">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="44628-119">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
