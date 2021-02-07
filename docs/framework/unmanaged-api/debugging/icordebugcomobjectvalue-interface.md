---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugComObjectValue のインターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
ms.openlocfilehash: 3c071c371ae6e330431630cfb1934b538d62efe6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710817"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="7306a-103">ICorDebugComObjectValue のインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7306a-103">ICorDebugComObjectValue Interface</span></span>

<span data-ttu-id="7306a-104">ランタイム呼び出し可能ラッパー (RCW) に関連付けられている情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7306a-104">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7306a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7306a-105">Methods</span></span>  
  
|<span data-ttu-id="7306a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7306a-106">Method</span></span>|<span data-ttu-id="7306a-107">説明</span><span class="sxs-lookup"><span data-stu-id="7306a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7306a-108">GetCachedInterfacePointers メソッド</span><span class="sxs-lookup"><span data-stu-id="7306a-108">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="7306a-109">現在の RCW でキャッシュされている生のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7306a-109">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="7306a-110">GetCachedInterfaceTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="7306a-110">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="7306a-111">現在のオブジェクトで使用または使用されているインターフェイス型の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="7306a-111">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7306a-112">解説</span><span class="sxs-lookup"><span data-stu-id="7306a-112">Remarks</span></span>  

 <span data-ttu-id="7306a-113">"ICorDebugValue" インターフェイスのインスタンスが RCW を表すかどうかを確認するために、デバッガーは `QueryInterface` を使用して "icordebugvalue" でを呼び出し `IID_ICorDebugComObjectValue` ます。</span><span class="sxs-lookup"><span data-stu-id="7306a-113">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7306a-114">要件</span><span class="sxs-lookup"><span data-stu-id="7306a-114">Requirements</span></span>  

 <span data-ttu-id="7306a-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7306a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7306a-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7306a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7306a-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7306a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7306a-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7306a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7306a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7306a-119">See also</span></span>

- [<span data-ttu-id="7306a-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7306a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7306a-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="7306a-121">Debugging</span></span>](index.md)
