---
description: '詳細については、次を参照してください: を参照してください。表示インターフェイス'
title: ICorDebugExceptionObjectCallStackEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: c72f4299bf3ebc5de2d2ed196801d93ff5fe4356
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693357"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="983ae-103">ICorDebugExceptionObjectCallStackEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="983ae-103">ICorDebugExceptionObjectCallStackEnum Interface</span></span>

<span data-ttu-id="983ae-104">例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="983ae-104">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="983ae-105">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="983ae-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="983ae-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="983ae-106">Methods</span></span>  
  
|<span data-ttu-id="983ae-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="983ae-107">Method</span></span>|<span data-ttu-id="983ae-108">説明</span><span class="sxs-lookup"><span data-stu-id="983ae-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="983ae-109">いい Exceptionobjectcallstackenum:: Next</span><span class="sxs-lookup"><span data-stu-id="983ae-109">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="983ae-110">例外オブジェクトの呼び出し履歴に関する情報を格納している、指定した数の [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="983ae-110">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="983ae-111">解説</span><span class="sxs-lookup"><span data-stu-id="983ae-111">Remarks</span></span>  

 <span data-ttu-id="983ae-112">`ICorDebugExceptionObjectCallStackEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="983ae-112">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="983ae-113">`ICorDebugExceptionObjectCallStackEnum` [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md)オブジェクトを使用してインスタンスに値を設定するには、 [EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="983ae-113">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="983ae-114">コレクション内のコールスタック項目を列挙するには、 [次](icordebugexceptionobjectcallstackenum-next-method.md) のように指定します。</span><span class="sxs-lookup"><span data-stu-id="983ae-114">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="983ae-115">要件</span><span class="sxs-lookup"><span data-stu-id="983ae-115">Requirements</span></span>  

 <span data-ttu-id="983ae-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="983ae-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="983ae-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="983ae-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="983ae-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="983ae-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="983ae-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="983ae-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="983ae-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="983ae-120">See also</span></span>

- [<span data-ttu-id="983ae-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="983ae-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="983ae-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="983ae-122">Debugging</span></span>](index.md)
