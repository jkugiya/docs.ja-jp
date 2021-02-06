---
description: '詳細については、次を参照してください: LoadModule メソッド'
title: ICorDebugManagedCallback::LoadModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 9a547d384b3f450054ebc70072664c6dcfb5992f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660506"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="527f7-103">ICorDebugManagedCallback::LoadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="527f7-103">ICorDebugManagedCallback::LoadModule Method</span></span>

<span data-ttu-id="527f7-104">共通言語ランタイム (CLR) モジュールが正常に読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="527f7-104">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="527f7-105">構文</span><span class="sxs-lookup"><span data-stu-id="527f7-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="527f7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="527f7-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="527f7-107">からモジュールが読み込まれたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="527f7-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="527f7-108">からCLR モジュールを表す、のモジュールオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="527f7-108">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="527f7-109">解説</span><span class="sxs-lookup"><span data-stu-id="527f7-109">Remarks</span></span>  

 <span data-ttu-id="527f7-110">`LoadModule`コールバックは、モジュールのメタデータを確認したり、just-in-time (JIT) コンパイラフラグを設定したり、モジュールのクラス読み込みコールバックを有効または無効にしたりするための適切な時間を提供します。</span><span class="sxs-lookup"><span data-stu-id="527f7-110">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="527f7-111">要件</span><span class="sxs-lookup"><span data-stu-id="527f7-111">Requirements</span></span>  

 <span data-ttu-id="527f7-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="527f7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="527f7-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="527f7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="527f7-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="527f7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="527f7-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="527f7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="527f7-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="527f7-116">See also</span></span>

- [<span data-ttu-id="527f7-117">UnloadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="527f7-117">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="527f7-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="527f7-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
