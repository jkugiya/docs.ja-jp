---
description: 詳細については、「ICorProfilerFunctionControl インターフェイス」を参照してください。
title: ICorProfilerFunctionControl インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
ms.openlocfilehash: 7b4ac58d2b8754108b4e10493596776987a93a49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753316"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="d5487-103">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5487-103">ICorProfilerFunctionControl Interface</span></span>

<span data-ttu-id="d5487-104">特定のメソッドを再コンパイルする時に JIT コンパイラーがコードをどのように生成するかを制御するために、コード プロファイラーが共通言語ランタイム (CLR) と通信できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d5487-104">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5487-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d5487-105">Methods</span></span>  
  
|<span data-ttu-id="d5487-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d5487-106">Method</span></span>|<span data-ttu-id="d5487-107">説明</span><span class="sxs-lookup"><span data-stu-id="d5487-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5487-108">SetCodegenFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="d5487-108">SetCodegenFlags Method</span></span>](icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="d5487-109">[COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md)列挙型の1つ以上のフラグを設定して、JUST-IN-TIME (JIT) 再コンパイル関数のコード生成を制御します。</span><span class="sxs-lookup"><span data-stu-id="d5487-109">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="d5487-110">SetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="d5487-110">SetILFunctionBody Method</span></span>](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="d5487-111">メソッドの中間共通言語 (CIL) 本体を置換します。</span><span class="sxs-lookup"><span data-stu-id="d5487-111">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="d5487-112">SetILInstrumentedCodeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="d5487-112">SetILInstrumentedCodeMap Method</span></span>](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="d5487-113">指定した共通中間言語 (CIL) マップ エントリを使用して、指定される関数のコード マップを設定します。</span><span class="sxs-lookup"><span data-stu-id="d5487-113">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5487-114">解説</span><span class="sxs-lookup"><span data-stu-id="d5487-114">Remarks</span></span>  

 <span data-ttu-id="d5487-115">`ICorProfilerFunctionControl` インターフェイスは、単一の再コンパイルされた関数に対してコード生成を制御するためにメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d5487-115">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="d5487-116">プロファイラーは、 [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) コールバックを使用して、このインターフェイスのインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5487-116">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="d5487-117">`ICorProfilerFunctionControl` の各インスタンスは一つの関数の全てのインスタンスを制御します。</span><span class="sxs-lookup"><span data-stu-id="d5487-117">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5487-118">要件</span><span class="sxs-lookup"><span data-stu-id="d5487-118">Requirements</span></span>  

 <span data-ttu-id="d5487-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5487-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5487-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5487-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5487-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5487-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5487-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5487-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5487-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5487-123">See also</span></span>

- [<span data-ttu-id="d5487-124">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5487-124">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="d5487-125">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5487-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d5487-126">EnumJITedFunctions2 メソッド</span><span class="sxs-lookup"><span data-stu-id="d5487-126">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)
