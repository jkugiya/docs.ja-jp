---
description: '詳細について: ICorProfilerInfo:: SetILInstrumentedCodeMap メソッド'
title: ICorProfilerInfo::SetILInstrumentedCodeMap メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: 0cf3b4ccf31076c2d1ea2df581003e3a07f0e795
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737351"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="81d4b-103">ICorProfilerInfo::SetILInstrumentedCodeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="81d4b-103">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="81d4b-104">指定された MSIL (Microsoft 中間言語) マップエントリを使用して、指定された関数のコードマップを設定します。</span><span class="sxs-lookup"><span data-stu-id="81d4b-104">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>

> [!NOTE]
> <span data-ttu-id="81d4b-105">.NET Framework バージョン2.0 では、 `SetILInstrumentedCodeMap` `FunctionID` 特定のアプリケーションドメインのジェネリック関数を表すでを呼び出すと、アプリケーションドメイン内のその関数のすべてのインスタンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="81d4b-105">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>

## <a name="syntax"></a><span data-ttu-id="81d4b-106">構文</span><span class="sxs-lookup"><span data-stu-id="81d4b-106">Syntax</span></span>

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a><span data-ttu-id="81d4b-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81d4b-107">Parameters</span></span>

`functionId`\
<span data-ttu-id="81d4b-108">からコードマップを設定する関数の ID。</span><span class="sxs-lookup"><span data-stu-id="81d4b-108">[in] The ID of the function for which to set the code map.</span></span>

`fStartJit`\
<span data-ttu-id="81d4b-109">からメソッドの呼び出し `SetILInstrumentedCodeMap` が、特定のの最初のメソッドであるかどうかを示すブール値 `FunctionID` 。</span><span class="sxs-lookup"><span data-stu-id="81d4b-109">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="81d4b-110">`fStartJit`指定されたの最初の呼び出しでをに設定し、それ以降の場合はに設定し `true` `SetILInstrumentedCodeMap` `FunctionID` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="81d4b-110">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>

`cILMapEntries`\
<span data-ttu-id="81d4b-111">から配列内の要素の数 `cILMapEntries` 。</span><span class="sxs-lookup"><span data-stu-id="81d4b-111">[in] The number of elements in the `cILMapEntries` array.</span></span>

`rgILMapEntries`\
<span data-ttu-id="81d4b-112">からCOR_IL_MAP 構造体の配列。それぞれが MSIL オフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="81d4b-112">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>

## <a name="remarks"></a><span data-ttu-id="81d4b-113">解説</span><span class="sxs-lookup"><span data-stu-id="81d4b-113">Remarks</span></span>

<span data-ttu-id="81d4b-114">多くの場合、プロファイラーは、メソッドのソースコード内にステートメントを挿入して、そのメソッドをインストルメント化します (たとえば、特定のソース行に到達したときに通知します)。</span><span class="sxs-lookup"><span data-stu-id="81d4b-114">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="81d4b-115">`SetILInstrumentedCodeMap` プロファイラーが元の MSIL 命令を新しい場所にマップできるようにします。</span><span class="sxs-lookup"><span data-stu-id="81d4b-115">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="81d4b-116">プロファイラーは、 [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) メソッドを使用して、指定されたネイティブオフセットの元の MSIL オフセットを取得できます。</span><span class="sxs-lookup"><span data-stu-id="81d4b-116">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>

<span data-ttu-id="81d4b-117">デバッガーは、古い各オフセットが元の変更されていない MSIL コード内の MSIL オフセットを参照し、新しい各オフセットが新しいインストルメント化されたコード内の MSIL オフセットを参照することを想定します。</span><span class="sxs-lookup"><span data-stu-id="81d4b-117">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="81d4b-118">マップは昇順に並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="81d4b-118">The map should be sorted in increasing order.</span></span> <span data-ttu-id="81d4b-119">ステップ実行を正常に行うには、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="81d4b-119">For stepping to work properly, follow these guidelines:</span></span>

- <span data-ttu-id="81d4b-120">インストルメント化された MSIL コードの順序を変更しません。</span><span class="sxs-lookup"><span data-stu-id="81d4b-120">Do not reorder instrumented MSIL code.</span></span>

- <span data-ttu-id="81d4b-121">元の MSIL コードは削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="81d4b-121">Do not remove the original MSIL code.</span></span>

- <span data-ttu-id="81d4b-122">マップ内のプログラムデータベース (PDB) ファイルからのすべてのシーケンスポイントのエントリを含めます。</span><span class="sxs-lookup"><span data-stu-id="81d4b-122">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="81d4b-123">マップでは、不足しているエントリは補間されません。</span><span class="sxs-lookup"><span data-stu-id="81d4b-123">The map does not interpolate missing entries.</span></span> <span data-ttu-id="81d4b-124">そのため、次のマップを指定します。</span><span class="sxs-lookup"><span data-stu-id="81d4b-124">So, given the following map:</span></span>

  <span data-ttu-id="81d4b-125">(古い0、新規 0)</span><span class="sxs-lookup"><span data-stu-id="81d4b-125">(0 old, 0 new)</span></span>

  <span data-ttu-id="81d4b-126">(5 歳、10新規)</span><span class="sxs-lookup"><span data-stu-id="81d4b-126">(5 old, 10 new)</span></span>

  <span data-ttu-id="81d4b-127">(9 歳、20新規)</span><span class="sxs-lookup"><span data-stu-id="81d4b-127">(9 old, 20 new)</span></span>

  - <span data-ttu-id="81d4b-128">古いオフセット0、1、2、3、または4が新しいオフセット0にマップされます。</span><span class="sxs-lookup"><span data-stu-id="81d4b-128">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>

  - <span data-ttu-id="81d4b-129">古いオフセット5、6、7、または8は、新しいオフセット10にマップされます。</span><span class="sxs-lookup"><span data-stu-id="81d4b-129">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>

  - <span data-ttu-id="81d4b-130">9以上の古いオフセットは、新しいオフセット20にマップされます。</span><span class="sxs-lookup"><span data-stu-id="81d4b-130">An old offset of 9 or higher will be mapped to new offset 20.</span></span>

  - <span data-ttu-id="81d4b-131">新しいオフセット0、1、2、3、4、5、6、7、8、または9が古いオフセット0にマップされます。</span><span class="sxs-lookup"><span data-stu-id="81d4b-131">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>

  - <span data-ttu-id="81d4b-132">新しいオフセット10、11、12、13、14、15、16、17、18、19は、古いオフセット5にマップされます。</span><span class="sxs-lookup"><span data-stu-id="81d4b-132">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>

  - <span data-ttu-id="81d4b-133">20以上の新しいオフセットは、古いオフセット9にマップされます。</span><span class="sxs-lookup"><span data-stu-id="81d4b-133">A new offset of 20 or higher will be mapped to old offset 9.</span></span>

<span data-ttu-id="81d4b-134">.NET Framework 3.5 およびそれ以前のバージョンでは、 `rgILMapEntries` [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) メソッドを呼び出すことによって配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="81d4b-134">In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method.</span></span> <span data-ttu-id="81d4b-135">ランタイムはこのメモリの所有権を取得するため、プロファイラーは解放を試みることはできません。</span><span class="sxs-lookup"><span data-stu-id="81d4b-135">Because the runtime takes ownership of this memory, the profiler should not attempt to free it.</span></span>

## <a name="requirements"></a><span data-ttu-id="81d4b-136">要件</span><span class="sxs-lookup"><span data-stu-id="81d4b-136">Requirements</span></span>

<span data-ttu-id="81d4b-137">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81d4b-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="81d4b-138">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="81d4b-138">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="81d4b-139">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81d4b-139">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="81d4b-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d4b-140">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="81d4b-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="81d4b-141">See also</span></span>

- [<span data-ttu-id="81d4b-142">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81d4b-142">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
