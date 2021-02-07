---
description: '詳細については、次のページを参照してください: を参照'
title: ICorDebugExceptionDebugEvent::GetFlags メソッド
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 54a6c9b0dff2346ca130f80e72fe06dbb3017f10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693474"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="52a8e-103">ICorDebugExceptionDebugEvent::GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="52a8e-103">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>

<span data-ttu-id="52a8e-104">例外をインターセプトできるかどうかを示すフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="52a8e-104">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a8e-105">構文</span><span class="sxs-lookup"><span data-stu-id="52a8e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52a8e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52a8e-106">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="52a8e-107">入出力例外をインターセプトできるかどうかを示す [Cordebugexceptionflags](cordebugexceptionflags-enumeration.md) 値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="52a8e-107">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52a8e-108">解説</span><span class="sxs-lookup"><span data-stu-id="52a8e-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52a8e-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="52a8e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52a8e-110">要件</span><span class="sxs-lookup"><span data-stu-id="52a8e-110">Requirements</span></span>  

 <span data-ttu-id="52a8e-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a8e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52a8e-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52a8e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52a8e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52a8e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52a8e-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52a8e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a8e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="52a8e-115">See also</span></span>

- [<span data-ttu-id="52a8e-116">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52a8e-116">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="52a8e-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="52a8e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
