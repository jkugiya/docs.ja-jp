---
description: 詳細については、「ICorPublishProcessEnum インターフェイス」を参照してください。
title: ICorPublishProcessEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 87d80d066995dbeca67f461e01652dd3deb3bf1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790491"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="014dd-103">ICorPublishProcessEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="014dd-103">ICorPublishProcessEnum Interface</span></span>

<span data-ttu-id="014dd-104">[ICorPublishProcess](icorpublishprocess-interface.md)オブジェクトのコレクションを走査するメソッドを提供する[ICorPublishEnum](icorpublishenum-interface.md)インターフェイスのサブクラス。</span><span class="sxs-lookup"><span data-stu-id="014dd-104">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="014dd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="014dd-105">Methods</span></span>  
  
|<span data-ttu-id="014dd-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="014dd-106">Method</span></span>|<span data-ttu-id="014dd-107">説明</span><span class="sxs-lookup"><span data-stu-id="014dd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="014dd-108">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="014dd-108">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="014dd-109">現在の位置から開始して、指定した数の `ICorPublishProcess` インスタンスをコレクションから取得します。</span><span class="sxs-lookup"><span data-stu-id="014dd-109">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="014dd-110">解説</span><span class="sxs-lookup"><span data-stu-id="014dd-110">Remarks</span></span>  

 <span data-ttu-id="014dd-111">インターフェイスは、 `ICorPublishProcessEnum` 抽象インターフェイス [ICorPublishEnum](icorpublishenum-interface.md)のメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="014dd-111">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="014dd-112">`ICorPublishProcessEnum`インスタンスは、 [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md)メソッドによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="014dd-112">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="014dd-113">オブジェクトのコレクションの走査 `ICorPublishProcess` は、インスタンスの作成時に指定されたフィルター条件に基づいてい `ICorPublishProcessEnum` ます。</span><span class="sxs-lookup"><span data-stu-id="014dd-113">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="014dd-114">要件</span><span class="sxs-lookup"><span data-stu-id="014dd-114">Requirements</span></span>  

 <span data-ttu-id="014dd-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="014dd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="014dd-116">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="014dd-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="014dd-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="014dd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="014dd-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="014dd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014dd-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="014dd-119">See also</span></span>

- [<span data-ttu-id="014dd-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="014dd-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="014dd-121">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="014dd-121">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
