---
description: '詳細情報: ICorDebug:: Initialize メソッド'
title: ICorDebug::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
ms.openlocfilehash: 6b6ddd8c1c21470477420909bcf75906b5731ee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791596"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="89e4a-103">ICorDebug::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="89e4a-103">ICorDebug::Initialize Method</span></span>

<span data-ttu-id="89e4a-104">`ICorDebug` オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="89e4a-104">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e4a-105">構文</span><span class="sxs-lookup"><span data-stu-id="89e4a-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="89e4a-106">解説</span><span class="sxs-lookup"><span data-stu-id="89e4a-106">Remarks</span></span>  

 <span data-ttu-id="89e4a-107">デバッガーは、 `Initialize` 作成時にを呼び出して、デバッグサービスを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89e4a-107">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="89e4a-108">このメソッドは、の他のメソッドが呼び出される前に呼び出す必要があり `ICorDebug` ます。</span><span class="sxs-lookup"><span data-stu-id="89e4a-108">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89e4a-109">要件</span><span class="sxs-lookup"><span data-stu-id="89e4a-109">Requirements</span></span>  

 <span data-ttu-id="89e4a-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89e4a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89e4a-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89e4a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89e4a-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89e4a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89e4a-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89e4a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e4a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="89e4a-114">See also</span></span>

- [<span data-ttu-id="89e4a-115">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89e4a-115">ICorDebug Interface</span></span>](icordebug-interface.md)
