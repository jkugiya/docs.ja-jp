---
description: '詳細情報: COR_PRF_CODEGEN_FLAGS 列挙型'
title: COR_PRF_CODEGEN_FLAGS 列挙体
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: 40ddaa77047e0b1daa743b512f21ba7643127230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649176"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="15bdc-103">COR_PRF_CODEGEN_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="15bdc-103">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>

<span data-ttu-id="15bdc-104">[ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md)メソッドで設定できるコード生成フラグを定義します。</span><span class="sxs-lookup"><span data-stu-id="15bdc-104">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15bdc-105">構文</span><span class="sxs-lookup"><span data-stu-id="15bdc-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="15bdc-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="15bdc-106">Members</span></span>  
  
|<span data-ttu-id="15bdc-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="15bdc-107">Member</span></span>|<span data-ttu-id="15bdc-108">説明</span><span class="sxs-lookup"><span data-stu-id="15bdc-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="15bdc-109">関数は、この関数の本体にインライン展開されません。</span><span class="sxs-lookup"><span data-stu-id="15bdc-109">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="15bdc-110">ただし、関数自体は、その呼び出し元にインライン展開される場合があります。</span><span class="sxs-lookup"><span data-stu-id="15bdc-110">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="15bdc-111">この関数の本体では、すべての最適化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="15bdc-111">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="15bdc-112">ただし、関数自体を呼び出し元にインライン化することはできます。</span><span class="sxs-lookup"><span data-stu-id="15bdc-112">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15bdc-113">解説</span><span class="sxs-lookup"><span data-stu-id="15bdc-113">Remarks</span></span>  

 <span data-ttu-id="15bdc-114">`COR_PRF_CODEGEN_FLAGS`列挙体は、 [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md)メソッドによって使用され、プロファイラーが JIT 再コンパイル関数のコード生成を制御できるようにします。</span><span class="sxs-lookup"><span data-stu-id="15bdc-114">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15bdc-115">要件</span><span class="sxs-lookup"><span data-stu-id="15bdc-115">Requirements</span></span>  

 <span data-ttu-id="15bdc-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15bdc-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15bdc-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15bdc-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15bdc-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15bdc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15bdc-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15bdc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15bdc-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="15bdc-120">See also</span></span>

- [<span data-ttu-id="15bdc-121">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="15bdc-121">Profiling Enumerations</span></span>](profiling-enumerations.md)
