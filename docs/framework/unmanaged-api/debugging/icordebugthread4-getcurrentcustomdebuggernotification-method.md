---
description: '詳細について: ICorDebugThread4:: Getcurrentcustomデバッガ通知メソッド'
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
ms.openlocfilehash: 20d9449e98b9ab91dbdec84ba026e91514d5b3cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800943"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="a57b5-103">ICorDebugThread4::GetCurrentCustomDebuggerNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="a57b5-103">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="a57b5-104">現在のスレッドの現在の [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="a57b5-104">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="a57b5-105">構文</span><span class="sxs-lookup"><span data-stu-id="a57b5-105">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="a57b5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a57b5-106">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="a57b5-107">入出力現在のスレッド上の現在のオブジェクトへのポインター `ICorDebugManagedCallback3::CustomNotification` 。</span><span class="sxs-lookup"><span data-stu-id="a57b5-107">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="a57b5-108">解説</span><span class="sxs-lookup"><span data-stu-id="a57b5-108">Remarks</span></span>

<span data-ttu-id="a57b5-109">`ppNotificationObject`コールバック内からメソッドが呼び出されていない場合 `ICorDebugManagedCallback3::CustomNotification` 、または現在の通知オブジェクトが存在しない場合は、の値が null になります。</span><span class="sxs-lookup"><span data-stu-id="a57b5-109">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="a57b5-110">要件</span><span class="sxs-lookup"><span data-stu-id="a57b5-110">Requirements</span></span>

<span data-ttu-id="a57b5-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a57b5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a57b5-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a57b5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="a57b5-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a57b5-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a57b5-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a57b5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a57b5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a57b5-115">See also</span></span>

- [<span data-ttu-id="a57b5-116">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a57b5-116">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="a57b5-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a57b5-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a57b5-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a57b5-118">Debugging</span></span>](index.md)
