---
description: '詳細については、次のページを参照してください: いいね。'
title: ICorDebugController::Continue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
ms.openlocfilehash: e5858a8c287e8dd5a493a85c9f427ad8acd9ecc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710804"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="0fbdc-103">ICorDebugController::Continue メソッド</span><span class="sxs-lookup"><span data-stu-id="0fbdc-103">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="0fbdc-104">[Stop メソッド](icordebugcontroller-stop-method.md)の呼び出し後に、マネージスレッドの実行を再開します。</span><span class="sxs-lookup"><span data-stu-id="0fbdc-104">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="0fbdc-105">構文</span><span class="sxs-lookup"><span data-stu-id="0fbdc-105">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="0fbdc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0fbdc-106">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="0fbdc-107">から `true` 帯域外イベントから続行する場合はに設定し、それ以外の場合はに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="0fbdc-107">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0fbdc-108">解説</span><span class="sxs-lookup"><span data-stu-id="0fbdc-108">Remarks</span></span>

<span data-ttu-id="0fbdc-109">`Continue` メソッドの呼び出し後にプロセスを続行し `ICorDebugController::Stop` ます。</span><span class="sxs-lookup"><span data-stu-id="0fbdc-109">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="0fbdc-110">混合モードのデバッグを実行する場合は、 `Continue` 帯域外のイベントから継続している場合を除き、Win32 イベントスレッドでを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="0fbdc-110">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="0fbdc-111">*帯域内イベント* は、マネージイベント、またはデバッガーがプロセスのマネージ状態との対話をサポートする通常のアンマネージイベントのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="0fbdc-111">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="0fbdc-112">この場合、デバッガーは、パラメーターがに設定された状態で [ICorDebugUnmanagedCallback::D Eのイベント](icordebugunmanagedcallback-debugevent-method.md) コールバックを受け取り `fOutOfBand` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="0fbdc-112">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="0fbdc-113">*アウトオブバンドイベント* は、イベントによってプロセスが停止されている間に、プロセスのマネージ状態との相互作用が不可能なアンマネージイベントです。</span><span class="sxs-lookup"><span data-stu-id="0fbdc-113">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="0fbdc-114">この場合、デバッガーは `ICorDebugUnmanagedCallback::DebugEvent` `fOutOfBand` パラメーターをに設定してコールバックを受け取り `true` ます。</span><span class="sxs-lookup"><span data-stu-id="0fbdc-114">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="0fbdc-115">要件</span><span class="sxs-lookup"><span data-stu-id="0fbdc-115">Requirements</span></span>

<span data-ttu-id="0fbdc-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fbdc-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="0fbdc-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fbdc-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="0fbdc-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fbdc-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0fbdc-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fbdc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
