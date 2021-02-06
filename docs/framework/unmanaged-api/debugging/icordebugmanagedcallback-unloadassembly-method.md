---
description: '詳細については、次を参照してください: UnloadAssembly メソッド'
title: ICorDebugManagedCallback::UnloadAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: b1860e90ba2bab1428a0f8559d18801136bbbb39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660337"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="2f4db-103">ICorDebugManagedCallback::UnloadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="2f4db-103">ICorDebugManagedCallback::UnloadAssembly Method</span></span>

<span data-ttu-id="2f4db-104">共通言語ランタイムアセンブリがアンロードされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2f4db-104">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f4db-105">構文</span><span class="sxs-lookup"><span data-stu-id="2f4db-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f4db-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f4db-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="2f4db-107">からアセンブリが格納されているアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2f4db-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="2f4db-108">からアセンブリを表す、オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2f4db-108">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f4db-109">解説</span><span class="sxs-lookup"><span data-stu-id="2f4db-109">Remarks</span></span>  

 <span data-ttu-id="2f4db-110">このコールバックの後にアセンブリを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="2f4db-110">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f4db-111">要件</span><span class="sxs-lookup"><span data-stu-id="2f4db-111">Requirements</span></span>  

 <span data-ttu-id="2f4db-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f4db-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f4db-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f4db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f4db-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f4db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f4db-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f4db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4db-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f4db-116">See also</span></span>

- [<span data-ttu-id="2f4db-117">LoadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="2f4db-117">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="2f4db-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f4db-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
