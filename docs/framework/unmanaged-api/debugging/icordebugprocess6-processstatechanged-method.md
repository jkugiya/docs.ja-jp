---
description: '詳細について: ICorDebugProcess6::P rocessStateChanged メソッド'
title: ICorDebugProcess6::ProcessStateChanged メソッド
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 8060c29598adf5d4bbe7bffb4cd6611ee19a2669
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691368"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="21a5e-103">ICorDebugProcess6::ProcessStateChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="21a5e-103">ICorDebugProcess6::ProcessStateChanged Method</span></span>

<span data-ttu-id="21a5e-104">プロセスが実行されていることを [ICorDebug](icordebug-interface.md) に通知します。</span><span class="sxs-lookup"><span data-stu-id="21a5e-104">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21a5e-105">構文</span><span class="sxs-lookup"><span data-stu-id="21a5e-105">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21a5e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="21a5e-106">Parameters</span></span>  

 `change`  
 <span data-ttu-id="21a5e-107">から [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) 列挙型のメンバー</span><span class="sxs-lookup"><span data-stu-id="21a5e-107">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21a5e-108">解説</span><span class="sxs-lookup"><span data-stu-id="21a5e-108">Remarks</span></span>  

 <span data-ttu-id="21a5e-109">デバッガーはこのメソッドを呼び出して、プロセスが実行されていることを [ICorDebug](icordebug-interface.md) に通知します。</span><span class="sxs-lookup"><span data-stu-id="21a5e-109">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21a5e-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="21a5e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21a5e-111">要件</span><span class="sxs-lookup"><span data-stu-id="21a5e-111">Requirements</span></span>  

 <span data-ttu-id="21a5e-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21a5e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21a5e-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21a5e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21a5e-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21a5e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21a5e-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21a5e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a5e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="21a5e-116">See also</span></span>

- [<span data-ttu-id="21a5e-117">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21a5e-117">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="21a5e-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="21a5e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
