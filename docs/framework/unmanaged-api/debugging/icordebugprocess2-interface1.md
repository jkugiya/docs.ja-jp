---
description: 詳細については、「ICorDebugProcess2 インターフェイス」を参照してください。
title: ICorDebugProcess2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
ms.openlocfilehash: 47e94ee8ee4f45e365fa9efe888cb706f8bb1dfd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746595"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="5ed16-103">ICorDebugProcess2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ed16-103">ICorDebugProcess2 Interface</span></span>

<span data-ttu-id="5ed16-104">は、マネージコードを実行しているプロセスを表す、のような、の論理拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="5ed16-104">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ed16-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed16-105">Methods</span></span>  
  
|<span data-ttu-id="5ed16-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed16-106">Method</span></span>|<span data-ttu-id="5ed16-107">説明</span><span class="sxs-lookup"><span data-stu-id="5ed16-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ed16-108">ClearUnmanagedBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed16-108">ClearUnmanagedBreakpoint Method</span></span>](icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="5ed16-109">の以前の呼び出しで設定された、指定したオフセット位置にあるブレークポイントを削除 `ICorDebugProcess2::SetUnmanagedBreakpoint` します。</span><span class="sxs-lookup"><span data-stu-id="5ed16-109">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="5ed16-110">GetDesiredNGENCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed16-110">GetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="5ed16-111">このによって参照されるプロセスにイメージを読み込むために共通言語ランタイム (CLR) に対して設定する必要があるフラグを取得し `ICorDebugProcess2` ます。</span><span class="sxs-lookup"><span data-stu-id="5ed16-111">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="5ed16-112">GetReferenceValueFromGCHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed16-112">GetReferenceValueFromGCHandle Method</span></span>](icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="5ed16-113">ガベージコレクションハンドルを持つ指定したマネージオブジェクトへの参照ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ed16-113">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="5ed16-114">GetThreadForTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed16-114">GetThreadForTaskID Method</span></span>](icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="5ed16-115">指定した id を持つタスクが実行されているスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ed16-115">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="5ed16-116">GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed16-116">GetVersion Method</span></span>](icordebugprocess2-getversion-method.md)|<span data-ttu-id="5ed16-117">デバッグ中のプロセスが実行されている CLR のバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ed16-117">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="5ed16-118">SetDesiredNGENCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed16-118">SetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="5ed16-119">Just-in-time (JIT) コンパイラがデバッグ中のプロセスにイメージを読み込むために必要なフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="5ed16-119">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="5ed16-120">SetUnmanagedBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed16-120">SetUnmanagedBreakpoint Method</span></span>](icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="5ed16-121">指定したネイティブイメージオフセットにアンマネージブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="5ed16-121">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ed16-122">解説</span><span class="sxs-lookup"><span data-stu-id="5ed16-122">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ed16-123">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5ed16-123">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed16-124">要件</span><span class="sxs-lookup"><span data-stu-id="5ed16-124">Requirements</span></span>  

 <span data-ttu-id="5ed16-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed16-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed16-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ed16-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ed16-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ed16-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ed16-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed16-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed16-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ed16-129">See also</span></span>

- [<span data-ttu-id="5ed16-130">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ed16-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
