---
description: '詳細情報: ICorPublishProcessEnum:: Next メソッド'
title: ICorPublishProcessEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
ms.openlocfilehash: 14b4f815aff986b23a22ed3d5736c37128d3d7e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790478"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="85997-103">ICorPublishProcessEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="85997-103">ICorPublishProcessEnum::Next Method</span></span>

<span data-ttu-id="85997-104">現在のカーソル位置から開始して、指定した数のプロセスをコレクションから取得します。</span><span class="sxs-lookup"><span data-stu-id="85997-104">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85997-105">構文</span><span class="sxs-lookup"><span data-stu-id="85997-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85997-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="85997-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="85997-107">から取得するプロセスの数。</span><span class="sxs-lookup"><span data-stu-id="85997-107">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="85997-108">入出力取得された [ICorPublishProcess](icorpublishprocess-interface.md) オブジェクトの配列へのポインター。それぞれがプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="85997-108">[out] A pointer to the array of retrieved [ICorPublishProcess](icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="85997-109">入出力実際に返されたプロセスの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="85997-109">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="85997-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="85997-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85997-111">要件</span><span class="sxs-lookup"><span data-stu-id="85997-111">Requirements</span></span>  

 <span data-ttu-id="85997-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85997-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85997-113">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="85997-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="85997-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85997-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85997-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85997-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85997-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="85997-116">See also</span></span>

- [<span data-ttu-id="85997-117">ICorPublishProcessEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85997-117">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)
