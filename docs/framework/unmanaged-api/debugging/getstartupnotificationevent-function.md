---
description: '詳細情報: GetStartupNotificationEvent 関数'
title: GetStartupNotificationEvent 関数
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
ms.openlocfilehash: 49b0e3f9b2acec87e419bae03086a7e437f45f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801385"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="f27e5-103">GetStartupNotificationEvent 関数</span><span class="sxs-lookup"><span data-stu-id="f27e5-103">GetStartupNotificationEvent Function</span></span>

<span data-ttu-id="f27e5-104">指定された対象プロセスに読み込まれている任意の共通言語ランタイム (CLR: Common Language Runtime) によって通知されるイベント ハンドルを作成または開きます。</span><span class="sxs-lookup"><span data-stu-id="f27e5-104">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f27e5-105">構文</span><span class="sxs-lookup"><span data-stu-id="f27e5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f27e5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f27e5-106">Parameters</span></span>  

 `debuggeePID`  
 <span data-ttu-id="f27e5-107">[in] 受信する CLR スタートアップ通知の送信元である対象プロセスのプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="f27e5-107">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="f27e5-108">[out] スタートアップ時に CLR によって通知されるハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f27e5-108">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f27e5-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f27e5-109">Return Value</span></span>  

 <span data-ttu-id="f27e5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f27e5-110">S_OK</span></span>  
 <span data-ttu-id="f27e5-111">スタートアップ通知イベントに対するハンドルを正常に取得しました。</span><span class="sxs-lookup"><span data-stu-id="f27e5-111">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="f27e5-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f27e5-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="f27e5-113">`phStartupEvent` が nullであるか、または `debuggeePID` が現在実行されているプロセスを参照していません。</span><span class="sxs-lookup"><span data-stu-id="f27e5-113">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="f27e5-114">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="f27e5-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="f27e5-115">スタートアップ通知イベントに対するハンドルを取得できません。</span><span class="sxs-lookup"><span data-stu-id="f27e5-115">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f27e5-116">解説</span><span class="sxs-lookup"><span data-stu-id="f27e5-116">Remarks</span></span>  

 <span data-ttu-id="f27e5-117">Windows オペレーティング システムでは、`debuggeePID` がプロセス識別子に対応づけられます。</span><span class="sxs-lookup"><span data-stu-id="f27e5-117">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="f27e5-118">イベントは、通知元の CLR によってマネージド コードが実行される前に通知されます。</span><span class="sxs-lookup"><span data-stu-id="f27e5-118">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f27e5-119">要件</span><span class="sxs-lookup"><span data-stu-id="f27e5-119">Requirements</span></span>  

 <span data-ttu-id="f27e5-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f27e5-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f27e5-121">**ヘッダー:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="f27e5-121">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="f27e5-122">**ライブラリ:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="f27e5-122">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="f27e5-123">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="f27e5-123">**.NET Framework Versions:** 3.5 SP1</span></span>
