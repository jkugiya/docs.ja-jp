---
description: '詳細について: ICorDebugHeapValue3:: GetMonitorEventWaitList メソッド'
title: ICorDebugHeapValue3::GetMonitorEventWaitList メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
ms.openlocfilehash: ffc849e83151719062133382989344a8f0057caf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791453"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="0b93d-103">ICorDebugHeapValue3::GetMonitorEventWaitList メソッド</span><span class="sxs-lookup"><span data-stu-id="0b93d-103">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>

<span data-ttu-id="0b93d-104">モニターロックに関連付けられているイベントでキューに登録されているスレッドの順序付きリストを提供します。</span><span class="sxs-lookup"><span data-stu-id="0b93d-104">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b93d-105">構文</span><span class="sxs-lookup"><span data-stu-id="0b93d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b93d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b93d-106">Parameters</span></span>  

 `ppThreadEnum`  
 <span data-ttu-id="0b93d-107">入出力順序付けされたスレッドのリストを提供する、の型の定数列挙子。</span><span class="sxs-lookup"><span data-stu-id="0b93d-107">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b93d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0b93d-108">Return Value</span></span>  

 <span data-ttu-id="0b93d-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="0b93d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0b93d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b93d-110">HRESULT</span></span>|<span data-ttu-id="0b93d-111">説明</span><span class="sxs-lookup"><span data-stu-id="0b93d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b93d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b93d-112">S_OK</span></span>|<span data-ttu-id="0b93d-113">The list is not empty.</span><span class="sxs-lookup"><span data-stu-id="0b93d-113">The list is not empty.</span></span>|  
|<span data-ttu-id="0b93d-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0b93d-114">S_FALSE</span></span>|<span data-ttu-id="0b93d-115">リストが空です。</span><span class="sxs-lookup"><span data-stu-id="0b93d-115">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0b93d-116">例外</span><span class="sxs-lookup"><span data-stu-id="0b93d-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b93d-117">解説</span><span class="sxs-lookup"><span data-stu-id="0b93d-117">Remarks</span></span>  

 <span data-ttu-id="0b93d-118">リスト内の最初のスレッドは、の次の呼び出しによって解放される最初のスレッドです <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0b93d-118">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0b93d-119">リスト内の次のスレッドは、次の呼び出しで解放されます。</span><span class="sxs-lookup"><span data-stu-id="0b93d-119">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="0b93d-120">リストが空でない場合、このメソッドは S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="0b93d-120">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="0b93d-121">リストが空の場合、メソッドは S_FALSE を返します。この場合、列挙体は空ですが、有効です。</span><span class="sxs-lookup"><span data-stu-id="0b93d-121">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="0b93d-122">どちらの場合も、列挙インターフェイスは、現在の同期された状態の間のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0b93d-122">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="0b93d-123">ただし、スレッドのインターフェイスディスペンサーは、スレッドが終了するまで有効です。</span><span class="sxs-lookup"><span data-stu-id="0b93d-123">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="0b93d-124">`ppThreadEnum`が有効なポインターでない場合、結果は未定義になります。</span><span class="sxs-lookup"><span data-stu-id="0b93d-124">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="0b93d-125">どのスレッドがモニターを待機しているかを特定できないようなエラーが発生した場合、メソッドはエラーを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="0b93d-125">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b93d-126">要件</span><span class="sxs-lookup"><span data-stu-id="0b93d-126">Requirements</span></span>  

 <span data-ttu-id="0b93d-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b93d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b93d-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b93d-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b93d-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b93d-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b93d-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b93d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b93d-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b93d-131">See also</span></span>

- [<span data-ttu-id="0b93d-132">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b93d-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0b93d-133">デバッグ</span><span class="sxs-lookup"><span data-stu-id="0b93d-133">Debugging</span></span>](index.md)
