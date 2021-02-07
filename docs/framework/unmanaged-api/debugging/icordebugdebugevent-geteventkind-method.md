---
description: 詳細については、次を参照してください
title: ICorDebugDebugEvent::GetEventKind メソッド
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 9e15eb82195fae8aa3797ea47cb04d0bb407d2ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764321"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="9ce47-103">ICorDebugDebugEvent::GetEventKind メソッド</span><span class="sxs-lookup"><span data-stu-id="9ce47-103">ICorDebugDebugEvent::GetEventKind Method</span></span>

<span data-ttu-id="9ce47-104">この `ICorDebugDebugEvent` オブジェクトが表すイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="9ce47-104">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ce47-105">構文</span><span class="sxs-lookup"><span data-stu-id="9ce47-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ce47-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ce47-106">Parameters</span></span>  

 <span data-ttu-id="9ce47-107">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="9ce47-107">pDebugEventKind</span></span>  
 <span data-ttu-id="9ce47-108">イベントの種類を示す [Cordebugdebugeventkind](cordebugdebugeventkind-enumeration.md) 列挙体メンバーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ce47-108">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ce47-109">解説</span><span class="sxs-lookup"><span data-stu-id="9ce47-109">Remarks</span></span>  

 <span data-ttu-id="9ce47-110">`pDebugEventKind` の値に基づいて、`QueryInterface` を呼び出して、追加データを含むより正確なデバッグ イベント インターフェイスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="9ce47-110">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ce47-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ce47-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ce47-112">要件</span><span class="sxs-lookup"><span data-stu-id="9ce47-112">Requirements</span></span>  

 <span data-ttu-id="9ce47-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ce47-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ce47-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ce47-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ce47-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ce47-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ce47-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ce47-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce47-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ce47-117">See also</span></span>

- [<span data-ttu-id="9ce47-118">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ce47-118">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="9ce47-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ce47-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
