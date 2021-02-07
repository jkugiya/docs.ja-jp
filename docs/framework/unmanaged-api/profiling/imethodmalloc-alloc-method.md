---
description: '詳細情報: IMethodMalloc:: Alloc メソッド'
title: IMethodMalloc::Alloc メソッド
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: f8a41530e0e1a126fafa1816e6fed58d10df6587
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736952"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="43fe3-103">IMethodMalloc::Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="43fe3-103">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="43fe3-104">新しい Microsoft 中間言語 (MSIL) 関数本体に対して、指定された量のメモリを割り当てようとします。</span><span class="sxs-lookup"><span data-stu-id="43fe3-104">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="43fe3-105">構文</span><span class="sxs-lookup"><span data-stu-id="43fe3-105">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="43fe3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="43fe3-106">Parameters</span></span>

`cb`\
<span data-ttu-id="43fe3-107">からメソッド本体に割り当てるバイト数。</span><span class="sxs-lookup"><span data-stu-id="43fe3-107">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="43fe3-108">解説</span><span class="sxs-lookup"><span data-stu-id="43fe3-108">Remarks</span></span>

 <span data-ttu-id="43fe3-109">割り当てられたメモリは、このアロケーターに関連付けられているモジュールのベースアドレスよりも大きいアドレスから開始されます。</span><span class="sxs-lookup"><span data-stu-id="43fe3-109">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="43fe3-110">つまり、各アロケーターは特定のモジュールに対して作成され、そのベースアドレスからの正のオフセットでメモリの割り当てが試行されます。</span><span class="sxs-lookup"><span data-stu-id="43fe3-110">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="43fe3-111">が、 `Alloc` モジュールのベースアドレスよりも大きいアドレスで要求されたバイト数を割り当てられなかった場合は、使用可能な実際のメモリ容量に関係なく E_OUTOFMEMORY を返します。</span><span class="sxs-lookup"><span data-stu-id="43fe3-111">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="43fe3-112">メソッドは、 `Alloc` [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) メソッドと組み合わせて使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43fe3-112">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="43fe3-113">要件</span><span class="sxs-lookup"><span data-stu-id="43fe3-113">Requirements</span></span>

 <span data-ttu-id="43fe3-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43fe3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="43fe3-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="43fe3-115">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="43fe3-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43fe3-116">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="43fe3-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43fe3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="43fe3-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="43fe3-118">See also</span></span>

- [<span data-ttu-id="43fe3-119">IMethodMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="43fe3-119">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
