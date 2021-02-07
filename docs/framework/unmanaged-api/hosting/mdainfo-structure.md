---
description: '詳細については、次を参照してください: MDAInfo 構造体'
title: MDAInfo 構造体
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
ms.openlocfilehash: 5c42537a68d38e6cff3d70dcb796cd733ce64a1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679759"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="8d8a3-103">MDAInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="8d8a3-103">MDAInfo Structure</span></span>

<span data-ttu-id="8d8a3-104">`Event_MDAFired`マネージデバッグアシスタント (MDA) の作成をトリガーするイベントについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-104">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d8a3-105">構文</span><span class="sxs-lookup"><span data-stu-id="8d8a3-105">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="8d8a3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8d8a3-106">Members</span></span>  
  
|<span data-ttu-id="8d8a3-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="8d8a3-107">Member</span></span>|<span data-ttu-id="8d8a3-108">説明</span><span class="sxs-lookup"><span data-stu-id="8d8a3-108">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="8d8a3-109">現在の MDA のタイトル。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-109">The title of the current MDA.</span></span> <span data-ttu-id="8d8a3-110">タイトルには、イベントを発生させたエラーの種類が示され `Event_MDAFired` ます。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-110">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="8d8a3-111">現在の MDA によって提供される出力メッセージ。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-111">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d8a3-112">解説</span><span class="sxs-lookup"><span data-stu-id="8d8a3-112">Remarks</span></span>  

 <span data-ttu-id="8d8a3-113">マネージデバッグアシスタント (Mda) は、共通言語ランタイム (CLR) と連携して動作し、ランタイム実行エンジンで無効な条件を特定したり、エンジンの状態に関する追加情報をダンプするなどのタスクを実行したりするためのデバッグ補助機能です。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-113">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="8d8a3-114">Mda は、トラップが困難なイベントに関する XML メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-114">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="8d8a3-115">これらは、マネージコードとアンマネージコードの間の遷移をデバッグする場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-115">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="8d8a3-116">MDA の作成をトリガーするイベントが発生した場合、ランタイムは次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-116">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="8d8a3-117">[ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)を呼び出してイベントを通知することで、ホストが[Iactiononclrevent](iactiononclrevent-interface.md)インスタンスを登録していない場合 `Event_MDAFired` 、ランタイムは既定のホストされていない動作に進みます。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-117">If the host has not registered an [IActionOnCLREvent](iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="8d8a3-118">ホストがこのイベントのハンドラーを登録している場合、ランタイムはデバッガーがプロセスにアタッチされているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-118">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="8d8a3-119">存在する場合、ランタイムはデバッガーに中断します。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-119">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="8d8a3-120">デバッガーが続行されると、ホストが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-120">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="8d8a3-121">デバッガーがアタッチされていない場合、ランタイムはを呼び出し、 `IActionOnCLREvent::OnEvent` `MDAInfo` パラメーターとしてインスタンスへのポインターを渡し `data` ます。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-121">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="8d8a3-122">ホストは mda をアクティブ化し、MDA がアクティブになったときに通知を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-122">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="8d8a3-123">これにより、ホストは、既定の動作をオーバーライドし、イベントを発生させたマネージスレッドを中止して、プロセスの状態が破損するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-123">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="8d8a3-124">Mda の使用方法の詳細については、「 [マネージデバッグアシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-124">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d8a3-125">要件</span><span class="sxs-lookup"><span data-stu-id="8d8a3-125">Requirements</span></span>  

 <span data-ttu-id="8d8a3-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d8a3-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d8a3-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8d8a3-127">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="8d8a3-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8d8a3-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d8a3-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d8a3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8a3-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d8a3-130">See also</span></span>

- [<span data-ttu-id="8d8a3-131">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="8d8a3-131">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="8d8a3-132">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="8d8a3-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
