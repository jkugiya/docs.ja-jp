---
description: 詳細については、次のページを参照してください
title: ICorDebugManagedCallback::Break メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: 2ef273a693291685c4c3a0ce2b20ed45613e3376
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801216"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="e0191-103">ICorDebugManagedCallback::Break メソッド</span><span class="sxs-lookup"><span data-stu-id="e0191-103">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="e0191-104"><xref:System.Reflection.Emit.OpCodes.Break>コードストリーム内の命令が実行されたときに、デバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e0191-104">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0191-105">構文</span><span class="sxs-lookup"><span data-stu-id="e0191-105">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="e0191-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e0191-106">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="e0191-107">からBreak 命令を含むアプリケーションドメインを表す、コードの Appdomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e0191-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="e0191-108">からBreak 命令を含むスレッドを表す、コードスレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e0191-108">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0191-109">要件</span><span class="sxs-lookup"><span data-stu-id="e0191-109">Requirements</span></span>

<span data-ttu-id="e0191-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0191-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e0191-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0191-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="e0191-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0191-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e0191-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0191-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e0191-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0191-114">See also</span></span>

- [<span data-ttu-id="e0191-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e0191-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
