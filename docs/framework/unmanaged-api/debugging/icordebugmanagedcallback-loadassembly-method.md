---
description: '詳細については、次のページを参照してください: の説明:: の関数'
title: ICorDebugManagedCallback::LoadAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
ms.openlocfilehash: b90391f3c6286323db11dadae841db38f9b785a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722803"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="9a637-103">ICorDebugManagedCallback::LoadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="9a637-103">ICorDebugManagedCallback::LoadAssembly Method</span></span>

<span data-ttu-id="9a637-104">共通言語ランタイム (CLR) アセンブリが正常に読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9a637-104">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a637-105">構文</span><span class="sxs-lookup"><span data-stu-id="9a637-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a637-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a637-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="9a637-107">からアセンブリが読み込まれたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9a637-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="9a637-108">からアセンブリを表す、オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9a637-108">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a637-109">要件</span><span class="sxs-lookup"><span data-stu-id="9a637-109">Requirements</span></span>  

 <span data-ttu-id="9a637-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a637-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a637-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a637-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a637-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a637-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a637-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a637-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a637-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a637-114">See also</span></span>

- [<span data-ttu-id="9a637-115">UnloadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="9a637-115">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="9a637-116">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a637-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
