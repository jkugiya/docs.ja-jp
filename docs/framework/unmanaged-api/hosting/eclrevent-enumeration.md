---
description: 詳細については、「EClrEvent 列挙型」を参照してください。
title: EClrEvent 列挙型
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: 7c2365d1a2fb0109bab9159c3af4e2da3a46de6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785602"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="9e9ef-103">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="9e9ef-103">EClrEvent Enumeration</span></span>

<span data-ttu-id="9e9ef-104">ホストがコールバックを登録できる共通言語ランタイム (CLR) イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-104">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e9ef-105">構文</span><span class="sxs-lookup"><span data-stu-id="9e9ef-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="9e9ef-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9e9ef-106">Members</span></span>  
  
|<span data-ttu-id="9e9ef-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="9e9ef-107">Member</span></span>|<span data-ttu-id="9e9ef-108">説明</span><span class="sxs-lookup"><span data-stu-id="9e9ef-108">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="9e9ef-109">致命的な CLR エラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-109">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="9e9ef-110">特定ののアンロードを指定し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-110">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="9e9ef-111">マネージデバッグアシスタント (MDA) メッセージが生成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-111">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="9e9ef-112">スタックオーバーフローエラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-112">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e9ef-113">解説</span><span class="sxs-lookup"><span data-stu-id="9e9ef-113">Remarks</span></span>  

 <span data-ttu-id="9e9ef-114">ホストは、 `EClrEvent` [ICLROnEventManager](iclroneventmanager-interface.md) インターフェイスのメソッドを呼び出すことによって、によって記述された任意のイベントの種類のコールバックを登録できます。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-114">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="9e9ef-115">ホストは、 [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) メソッドを呼び出すことによって、このインターフェイスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-115">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="9e9ef-116">`Event_CLRDisabled`イベントと `Event_DomainUnload` イベントが複数回発生する可能性があり、異なるスレッドから、アンロードまたは CLR の無効化を通知することができます。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-116">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="9e9ef-117">イベントは、 `Event_MDAFired` MDA メッセージの詳細を含む [MDAInfo](mdainfo-structure.md) インスタンスの作成を発生させます。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-117">The `Event_MDAFired` event raises the creation of an [MDAInfo](mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="9e9ef-118">Mda の詳細については、「 [マネージデバッグアシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-118">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e9ef-119">要件</span><span class="sxs-lookup"><span data-stu-id="9e9ef-119">Requirements</span></span>  

 <span data-ttu-id="9e9ef-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e9ef-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e9ef-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9e9ef-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e9ef-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e9ef-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e9ef-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e9ef-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e9ef-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e9ef-124">See also</span></span>

- [<span data-ttu-id="9e9ef-125">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e9ef-125">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="9e9ef-126">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e9ef-126">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="9e9ef-127">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="9e9ef-127">Hosting Enumerations</span></span>](hosting-enumerations.md)
