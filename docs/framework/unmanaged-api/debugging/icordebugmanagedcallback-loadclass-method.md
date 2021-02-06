---
description: 詳細については、次を参照
title: ICorDebugManagedCallback::LoadClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 6f670a2f0798c7edfdc4292334cf9534e59a3007
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660610"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="8b398-103">ICorDebugManagedCallback::LoadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="8b398-103">ICorDebugManagedCallback::LoadClass Method</span></span>

<span data-ttu-id="8b398-104">クラスが読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8b398-104">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b398-105">構文</span><span class="sxs-lookup"><span data-stu-id="8b398-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b398-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8b398-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="8b398-107">からクラスが読み込まれたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8b398-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="8b398-108">からクラスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8b398-108">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b398-109">解説</span><span class="sxs-lookup"><span data-stu-id="8b398-109">Remarks</span></span>  

 <span data-ttu-id="8b398-110">このコールバックは、クラスを含むモジュールに対してクラスの読み込みが有効になっている場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="8b398-110">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="8b398-111">動的モジュールでは、クラスの読み込みが常に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="8b398-111">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="8b398-112">`LoadClass`コールバックは、動的モジュールで新しく生成されたクラスにブレークポイントをバインドするための適切な時間を提供します。</span><span class="sxs-lookup"><span data-stu-id="8b398-112">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b398-113">要件</span><span class="sxs-lookup"><span data-stu-id="8b398-113">Requirements</span></span>  

 <span data-ttu-id="8b398-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b398-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b398-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b398-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b398-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b398-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b398-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b398-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b398-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b398-118">See also</span></span>

- [<span data-ttu-id="8b398-119">UnloadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="8b398-119">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="8b398-120">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b398-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
