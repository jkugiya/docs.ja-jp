---
description: 詳細については、次の説明
title: ICorDebugDebugEvent::GetThread メソッド
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 1d476603572f31882f481d414e483c6712f1b5fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710414"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="74815-103">ICorDebugDebugEvent::GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="74815-103">ICorDebugDebugEvent::GetThread Method</span></span>

<span data-ttu-id="74815-104">イベントが発生したスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="74815-104">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74815-105">構文</span><span class="sxs-lookup"><span data-stu-id="74815-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74815-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74815-106">Parameters</span></span>  

 <span data-ttu-id="74815-107">ppThread</span><span class="sxs-lookup"><span data-stu-id="74815-107">ppThread</span></span>  
 <span data-ttu-id="74815-108">[出力] イベントが発生したスレッドを表す ICorDebugThread オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="74815-108">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74815-109">解説</span><span class="sxs-lookup"><span data-stu-id="74815-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74815-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="74815-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74815-111">要件</span><span class="sxs-lookup"><span data-stu-id="74815-111">Requirements</span></span>  

 <span data-ttu-id="74815-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74815-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74815-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74815-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74815-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74815-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74815-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74815-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74815-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="74815-116">See also</span></span>

- [<span data-ttu-id="74815-117">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74815-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="74815-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="74815-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
