---
description: '詳細情報: FunctionEnter 関数'
title: FunctionEnter 関数
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
ms.openlocfilehash: 07b91a81480e453be16e840b89fa822cb91002ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788957"
---
# <a name="functionenter-function"></a><span data-ttu-id="8a281-103">FunctionEnter 関数</span><span class="sxs-lookup"><span data-stu-id="8a281-103">FunctionEnter Function</span></span>

<span data-ttu-id="8a281-104">コントロールが関数に渡されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8a281-104">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a281-105">`FunctionEnter`関数は .NET Framework バージョン2.0 では非推奨とされており、その使用によってパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="8a281-105">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="8a281-106">代わりに、 [FunctionEnter2](functionenter2-function.md) 関数を使用してください。</span><span class="sxs-lookup"><span data-stu-id="8a281-106">Use the [FunctionEnter2](functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a281-107">構文</span><span class="sxs-lookup"><span data-stu-id="8a281-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a281-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a281-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="8a281-109">\[in] コントロールが渡される関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="8a281-109">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a281-110">解説</span><span class="sxs-lookup"><span data-stu-id="8a281-110">Remarks</span></span>  

 <span data-ttu-id="8a281-111">`FunctionEnter`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a281-111">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="8a281-112">実装では、 `__declspec` ( `naked` ) ストレージクラス属性を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a281-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="8a281-113">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="8a281-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="8a281-114">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a281-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="8a281-115">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a281-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="8a281-116">の実装は、 `FunctionEnter` ガベージコレクションを遅延させるため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="8a281-116">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="8a281-117">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="8a281-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="8a281-118">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionEnter` ます。</span><span class="sxs-lookup"><span data-stu-id="8a281-118">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="8a281-119">また、 `FunctionEnter` 関数はマネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="8a281-119">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a281-120">要件</span><span class="sxs-lookup"><span data-stu-id="8a281-120">Requirements</span></span>  

 <span data-ttu-id="8a281-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a281-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a281-122">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="8a281-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8a281-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a281-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a281-124">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="8a281-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a281-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a281-125">See also</span></span>

- [<span data-ttu-id="8a281-126">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="8a281-126">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="8a281-127">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="8a281-127">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="8a281-128">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="8a281-128">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="8a281-129">SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="8a281-129">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="8a281-130">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="8a281-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
