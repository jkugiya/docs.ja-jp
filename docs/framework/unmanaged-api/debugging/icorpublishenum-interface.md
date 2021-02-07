---
description: 詳細については、「ICorPublishEnum インターフェイス」を参照してください。
title: ICorPublishEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: c0d50f67bd61eecbade0b226f2f569ac26712faf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721603"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="77665-103">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77665-103">ICorPublishEnum Interface</span></span>

<span data-ttu-id="77665-104">プロセスおよびアプリケーションドメインに関する情報の公開に使用される列挙子の抽象基本インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="77665-104">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77665-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="77665-105">Methods</span></span>  
  
|<span data-ttu-id="77665-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="77665-106">Method</span></span>|<span data-ttu-id="77665-107">説明</span><span class="sxs-lookup"><span data-stu-id="77665-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77665-108">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="77665-108">Clone Method</span></span>](icorpublishenum-clone-method.md)|<span data-ttu-id="77665-109">この `ICorPublishEnum` オブジェクトのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="77665-109">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="77665-110">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="77665-110">GetCount Method</span></span>](icorpublishenum-getcount-method.md)|<span data-ttu-id="77665-111">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="77665-111">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="77665-112">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="77665-112">Reset Method</span></span>](icorpublishenum-reset-method.md)|<span data-ttu-id="77665-113">のカーソルを列挙体の先頭に移動します。</span><span class="sxs-lookup"><span data-stu-id="77665-113">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="77665-114">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="77665-114">Skip Method</span></span>](icorpublishenum-skip-method.md)|<span data-ttu-id="77665-115">指定した数の項目だけ、列挙内でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="77665-115">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77665-116">解説</span><span class="sxs-lookup"><span data-stu-id="77665-116">Remarks</span></span>  

 <span data-ttu-id="77665-117">次の列挙子は、から派生し `ICorPublishEnum` ます。</span><span class="sxs-lookup"><span data-stu-id="77665-117">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="77665-118">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="77665-118">ICorPublishAppDomainEnum</span></span>](icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="77665-119">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="77665-119">ICorPublishProcessEnum</span></span>](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="77665-120">要件</span><span class="sxs-lookup"><span data-stu-id="77665-120">Requirements</span></span>  

 <span data-ttu-id="77665-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77665-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77665-122">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="77665-122">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="77665-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77665-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77665-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77665-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77665-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="77665-125">See also</span></span>

- [<span data-ttu-id="77665-126">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="77665-126">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
- [<span data-ttu-id="77665-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="77665-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
