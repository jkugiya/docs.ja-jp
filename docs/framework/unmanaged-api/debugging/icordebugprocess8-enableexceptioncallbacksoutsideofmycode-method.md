---
description: '詳細については、次を参照してください: ICorDebugProcess8:: Enableexception Soutsideofmycode メソッド'
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: a85c9d62e5fb62fe620f0901509afa5a03504d4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691277"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="41500-103">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド</span><span class="sxs-lookup"><span data-stu-id="41500-103">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>

<span data-ttu-id="41500-104">[.NET Framework 4.6 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="41500-104">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="41500-105">特定の種類の [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外コールバックを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="41500-105">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41500-106">構文</span><span class="sxs-lookup"><span data-stu-id="41500-106">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41500-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41500-107">Parameters</span></span>  

 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="41500-108">[入力]</span><span class="sxs-lookup"><span data-stu-id="41500-108">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41500-109">解説</span><span class="sxs-lookup"><span data-stu-id="41500-109">Remarks</span></span>  

 <span data-ttu-id="41500-110">`enableExceptionsOutsideOfJMC` の値が `false` の場合:</span><span class="sxs-lookup"><span data-stu-id="41500-110">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="41500-111">デバッガーへのコールバックでは DEBUG_EXCEPTION_FIRST_CHANCE 例外は発生しません。</span><span class="sxs-lookup"><span data-stu-id="41500-111">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="41500-112">例外がユーザー コードにエスケープされることがない場合 (つまり、例外の発生から例外ハンドラーへのパスで、JustMyCode または JMC とマークされているメソッドがない場合)、DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外は発生しません。</span><span class="sxs-lookup"><span data-stu-id="41500-112">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="41500-113">`enableExceptionsOutsideOfJMC` の既定値は `true`です。</span><span class="sxs-lookup"><span data-stu-id="41500-113">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41500-114">要件</span><span class="sxs-lookup"><span data-stu-id="41500-114">Requirements</span></span>  

 <span data-ttu-id="41500-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41500-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41500-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41500-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41500-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41500-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41500-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41500-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41500-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="41500-119">See also</span></span>

- [<span data-ttu-id="41500-120">ICorDebugProcess8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41500-120">ICorDebugProcess8 Interface</span></span>](icordebugprocess8-interface.md)
- [<span data-ttu-id="41500-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="41500-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
