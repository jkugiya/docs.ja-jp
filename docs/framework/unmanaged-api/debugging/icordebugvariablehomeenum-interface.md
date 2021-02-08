---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugVariableHomeEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: c56c68a6b5f9d329fe8af23f47b40fa629bfe3ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790621"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="f2e14-103">ICorDebugVariableHomeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2e14-103">ICorDebugVariableHomeEnum Interface</span></span>

<span data-ttu-id="f2e14-104">関数のローカル変数および引数に列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="f2e14-104">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2e14-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f2e14-105">Methods</span></span>  
  
|<span data-ttu-id="f2e14-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="f2e14-106">Method</span></span>|<span data-ttu-id="f2e14-107">説明</span><span class="sxs-lookup"><span data-stu-id="f2e14-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2e14-108">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="f2e14-108">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="f2e14-109">関数内のローカル変数および引数に関する情報を格納している指定された数の表示変数 [home](icordebugvariablehome-interface.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f2e14-109">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2e14-110">解説</span><span class="sxs-lookup"><span data-stu-id="f2e14-110">Remarks</span></span>  

 <span data-ttu-id="f2e14-111">`ICorDebugVariableHomeEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="f2e14-111">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="f2e14-112">`ICorDebugVariableHomeEnum`インスタンスには、 [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md)メソッドを呼び出すことによって、表示[変数 home](icordebugvariablehome-interface.md)インスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="f2e14-112">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="f2e14-113">コレクション内 [の各は](icordebugvariablehome-interface.md) 、関数のローカル変数または引数を表します。</span><span class="sxs-lookup"><span data-stu-id="f2e14-113">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="f2e14-114">コレクション内  [のオブジェクトを](icordebugvariablehome-interface.md) 列挙するには、 [次](icordebugvariablehomeenum-next-method.md) のように指定します。</span><span class="sxs-lookup"><span data-stu-id="f2e14-114">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2e14-115">要件</span><span class="sxs-lookup"><span data-stu-id="f2e14-115">Requirements</span></span>  

 <span data-ttu-id="f2e14-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2e14-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2e14-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2e14-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2e14-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2e14-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2e14-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2e14-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e14-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2e14-120">See also</span></span>

- [<span data-ttu-id="f2e14-121">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2e14-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="f2e14-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2e14-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
