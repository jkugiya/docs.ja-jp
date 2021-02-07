---
description: '詳細について: ICorProfilerInfo6:: EnumNgenModuleMethodsInliningThisMethod メソッド'
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: bd43dcecabe9a75f7ce3a94996727b192574e321
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737169"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="7b7df-103">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="7b7df-103">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="7b7df-104">特定の NGen モジュールで定義され、指定されたメソッドにインライン化されているすべてのメソッドに対する列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="7b7df-104">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="7b7df-105">構文</span><span class="sxs-lookup"><span data-stu-id="7b7df-105">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="7b7df-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7b7df-106">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="7b7df-107">からNGen モジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="7b7df-107">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="7b7df-108">からを定義するモジュールの識別子 `inlineeMethodId` 。</span><span class="sxs-lookup"><span data-stu-id="7b7df-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="7b7df-109">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b7df-109">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="7b7df-110">からインラインメソッドの識別子。</span><span class="sxs-lookup"><span data-stu-id="7b7df-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="7b7df-111">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b7df-111">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="7b7df-112">入出力 `ppEnum` に、指定したメソッドをインライン展開するメソッドがすべて含まれているかどうかを示すフラグ。</span><span class="sxs-lookup"><span data-stu-id="7b7df-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="7b7df-113">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b7df-113">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="7b7df-114">入出力列挙子のアドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="7b7df-114">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="7b7df-115">解説</span><span class="sxs-lookup"><span data-stu-id="7b7df-115">Remarks</span></span>

<span data-ttu-id="7b7df-116">`inlineeModuleId` と `inlineeMethodId` は、インライン化される可能性のあるメソッドの完全な識別子を形成します。</span><span class="sxs-lookup"><span data-stu-id="7b7df-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="7b7df-117">たとえば、module `A` がメソッドを定義するとし `Simple.Add` ます。</span><span class="sxs-lookup"><span data-stu-id="7b7df-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="7b7df-118">モジュール B は次を定義し `Fancy.AddTwice` ます。</span><span class="sxs-lookup"><span data-stu-id="7b7df-118">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="7b7df-119">は、への呼び出しをインラインで使用することも想定 `Fancy.AddTwice` `SimpleAdd` しています。</span><span class="sxs-lookup"><span data-stu-id="7b7df-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="7b7df-120">プロファイラーは、この列挙子を使用して、モジュール B でインラインで定義されているすべてのメソッドを検索し、結果を列挙することができ `Simple.Add` `AddTwice` ます。</span><span class="sxs-lookup"><span data-stu-id="7b7df-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="7b7df-121">`inlineeModuleId` はモジュールの識別子で、 `A` `inlineeMethodId` はの識別子です `Simple.Add(int a, int b)` 。</span><span class="sxs-lookup"><span data-stu-id="7b7df-121">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="7b7df-122">`incompleteData`関数からが返された後にが true の場合、列挙子には、特定のメソッドをインライン展開するメソッドがすべて含まれているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="7b7df-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="7b7df-123">これは、inliners モジュールの1つ以上の直接または間接的な依存関係がまだ読み込まれていない場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7b7df-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="7b7df-124">プロファイラーが正確なデータを必要とする場合、より多くのモジュールが読み込まれると、後でモジュールの負荷に応じて、後で再試行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b7df-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="7b7df-125">`EnumNgenModuleMethodsInliningThisMethod`メソッドを使用すると、ReJIT のインライン展開に関する制限を回避できます。</span><span class="sxs-lookup"><span data-stu-id="7b7df-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="7b7df-126">ReJIT を使用すると、プロファイラーはメソッドの実装を変更し、その場で新しいコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7b7df-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="7b7df-127">たとえば、次のように変更でき `Simple.Add` ます。</span><span class="sxs-lookup"><span data-stu-id="7b7df-127">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="7b7df-128">ただし、は既にインライン化されているため `Fancy.AddTwice` `Simple.Add` 、以前と同じ動作を続けます。</span><span class="sxs-lookup"><span data-stu-id="7b7df-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="7b7df-129">この制限を回避するために、呼び出し元は、 `Simple.Add` `ICorProfilerInfo5::RequestRejit` これらの各メソッドでインラインで使用されるすべてのモジュール内のすべてのメソッドを検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b7df-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="7b7df-130">メソッドを再コンパイルすると、以前の動作ではなく、の新しい動作が行われ `Simple.Add` ます。</span><span class="sxs-lookup"><span data-stu-id="7b7df-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b7df-131">要件</span><span class="sxs-lookup"><span data-stu-id="7b7df-131">Requirements</span></span>

<span data-ttu-id="7b7df-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b7df-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7b7df-133">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b7df-133">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="7b7df-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b7df-134">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="7b7df-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b7df-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7b7df-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b7df-136">See also</span></span>

- [<span data-ttu-id="7b7df-137">ICorProfilerInfo6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b7df-137">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
