---
description: 詳細については、「ICorProfilerInfo4 インターフェイス」を参照してください。
title: ICorProfilerInfo4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
ms.openlocfilehash: 94e33be74ccffea3fa9a0e51e317a6888596606d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794508"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="28b0f-103">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28b0f-103">ICorProfilerInfo4 Interface</span></span>

<span data-ttu-id="28b0f-104">コードプロファイラーが共通言語ランタイム (CLR) と通信してイベント監視と要求情報を制御するために使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-104">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="28b0f-105">.</span><span class="sxs-lookup"><span data-stu-id="28b0f-105">.</span></span> <span data-ttu-id="28b0f-106">インターフェイスは、 `ICorProfilerInfo4` 他のインターフェイスの拡張です `ICorProfilerInfo` 。</span><span class="sxs-lookup"><span data-stu-id="28b0f-106">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="28b0f-107">これには、just-in-time (JIT) の再コンパイルをサポートする新しいメソッドが用意されており、.NET Framework 4.5 に追加されています。</span><span class="sxs-lookup"><span data-stu-id="28b0f-107">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28b0f-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-108">Methods</span></span>  
  
|<span data-ttu-id="28b0f-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-109">Method</span></span>|<span data-ttu-id="28b0f-110">説明</span><span class="sxs-lookup"><span data-stu-id="28b0f-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28b0f-111">EnumJITedFunctions2 メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-111">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="28b0f-112">以前に JIT コンパイルおよび JIT 再コンパイルされたすべての関数の列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-112">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="28b0f-113">EnumThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-113">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="28b0f-114">プロファイリングされたプロセス内のすべてのマネージスレッドのコレクションを順番に反復処理するメソッドを提供する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-114">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="28b0f-115">GetCodeInfo3 メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-115">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="28b0f-116">指定した関数の JIT 再コンパイル バージョンに関連付けられているネイティブ コードの範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-116">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="28b0f-117">GetFunctionFromIP2 メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-117">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="28b0f-118">マネージコード命令ポインターを、指定された関数の JIT 再コンパイルバージョンにマップします。</span><span class="sxs-lookup"><span data-stu-id="28b0f-118">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="28b0f-119">GetILToNativeMapping2 メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-119">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="28b0f-120">Microsoft 中間言語 (MSIL) オフセットから、指定した関数の JIT 再コンパイルバージョンに含まれるコードのネイティブオフセットへのマップを取得します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-120">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="28b0f-121">GetObjectSize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-121">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="28b0f-122">指定したオブジェクトのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-122">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="28b0f-123">GetReJITIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-123">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="28b0f-124">割り当てられている指定された関数のすべての JIT 再コンパイルバージョンを識別する Id の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-124">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="28b0f-125">InitializeCurrentThread メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-125">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="28b0f-126">デッドロックを回避できるように、同じスレッドで、後続のプロファイラー API 呼び出しの前に現在のスレッドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-126">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="28b0f-127">RequestReJIT メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-127">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="28b0f-128">指定された関数のすべてのインスタンスの JIT 再コンパイルを要求します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-128">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="28b0f-129">RequestRevert メソッド</span><span class="sxs-lookup"><span data-stu-id="28b0f-129">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="28b0f-130">指定された関数のすべてのインスタンスを元のバージョンに戻します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-130">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28b0f-131">解説</span><span class="sxs-lookup"><span data-stu-id="28b0f-131">Remarks</span></span>  

 <span data-ttu-id="28b0f-132">CLR は、`ICorProfilerInfo4` インターフェイスのメソッドを、フリー スレッド モデルを使用して実装します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-132">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="28b0f-133">各メソッドが、成功または失敗を示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="28b0f-133">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="28b0f-134">返される可能性があるリターン コードの一覧については、CorError.h ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="28b0f-134">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28b0f-135">要件</span><span class="sxs-lookup"><span data-stu-id="28b0f-135">Requirements</span></span>  

 <span data-ttu-id="28b0f-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28b0f-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28b0f-137">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28b0f-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28b0f-138">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28b0f-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28b0f-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28b0f-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b0f-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="28b0f-140">See also</span></span>

- [<span data-ttu-id="28b0f-141">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="28b0f-141">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="28b0f-142">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28b0f-142">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
