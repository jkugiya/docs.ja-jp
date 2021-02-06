---
description: '詳細については、次を参照してください: UnloadClass メソッド'
title: ICorDebugManagedCallback::UnloadClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: b76caf39611b0f59c74b4ae47d167e6f232a6dbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660220"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="2bb12-103">ICorDebugManagedCallback::UnloadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="2bb12-103">ICorDebugManagedCallback::UnloadClass Method</span></span>

<span data-ttu-id="2bb12-104">クラスがアンロードされていることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2bb12-104">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bb12-105">構文</span><span class="sxs-lookup"><span data-stu-id="2bb12-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bb12-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2bb12-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="2bb12-107">からクラスを含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2bb12-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="2bb12-108">からクラスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2bb12-108">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bb12-109">解説</span><span class="sxs-lookup"><span data-stu-id="2bb12-109">Remarks</span></span>  

 <span data-ttu-id="2bb12-110">この呼び出しの後にクラスを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="2bb12-110">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bb12-111">要件</span><span class="sxs-lookup"><span data-stu-id="2bb12-111">Requirements</span></span>  

 <span data-ttu-id="2bb12-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bb12-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bb12-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bb12-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bb12-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bb12-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bb12-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bb12-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb12-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bb12-116">See also</span></span>

- [<span data-ttu-id="2bb12-117">LoadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="2bb12-117">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="2bb12-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2bb12-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
