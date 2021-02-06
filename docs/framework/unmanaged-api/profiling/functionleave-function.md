---
description: '詳細情報: FunctionLeave 関数'
title: FunctionLeave 関数
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: cc0db68df8976ce86197cc9b7570b00c6f662cb5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648481"
---
# <a name="functionleave-function"></a><span data-ttu-id="66527-103">FunctionLeave 関数</span><span class="sxs-lookup"><span data-stu-id="66527-103">FunctionLeave Function</span></span>

<span data-ttu-id="66527-104">関数が呼び出し元に戻りようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="66527-104">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66527-105">`FunctionLeave`関数は、.NET Framework 2.0 では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="66527-105">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="66527-106">これは引き続き機能しますが、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="66527-106">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="66527-107">代わりに、 [FunctionLeave2](functionleave2-function.md) 関数を使用してください。</span><span class="sxs-lookup"><span data-stu-id="66527-107">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66527-108">構文</span><span class="sxs-lookup"><span data-stu-id="66527-108">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66527-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66527-109">Parameters</span></span>

- `funcID`

  <span data-ttu-id="66527-110">\[in] を返す関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="66527-110">\[in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="66527-111">解説</span><span class="sxs-lookup"><span data-stu-id="66527-111">Remarks</span></span>  

 <span data-ttu-id="66527-112">`FunctionLeave`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66527-112">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="66527-113">実装では、 `__declspec` ( `naked` ) ストレージクラス属性を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66527-113">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="66527-114">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="66527-114">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="66527-115">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66527-115">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="66527-116">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66527-116">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="66527-117">の実装は、 `FunctionLeave` ガベージコレクションを遅延させるため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="66527-117">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="66527-118">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="66527-118">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="66527-119">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionLeave` ます。</span><span class="sxs-lookup"><span data-stu-id="66527-119">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="66527-120">また、 `FunctionLeave` 関数はマネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="66527-120">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66527-121">要件</span><span class="sxs-lookup"><span data-stu-id="66527-121">Requirements</span></span>  

 <span data-ttu-id="66527-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66527-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66527-123">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="66527-123">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="66527-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66527-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66527-125">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="66527-125">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66527-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="66527-126">See also</span></span>

- [<span data-ttu-id="66527-127">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="66527-127">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="66527-128">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="66527-128">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="66527-129">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="66527-129">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="66527-130">SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="66527-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="66527-131">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="66527-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
