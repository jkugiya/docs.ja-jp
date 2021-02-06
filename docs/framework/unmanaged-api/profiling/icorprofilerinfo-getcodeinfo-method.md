---
description: '詳細について: ICorProfilerInfo:: GetCodeInfo メソッド'
title: ICorProfilerInfo::GetCodeInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: e965e9c21b7add0367b08f152bf509ad6b6ed4cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647662"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="9f926-103">ICorProfilerInfo::GetCodeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="9f926-103">ICorProfilerInfo::GetCodeInfo Method</span></span>

<span data-ttu-id="9f926-104">指定した関数 ID に関連付けられているネイティブ コードの範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="9f926-104">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="9f926-105">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="9f926-105">This method is obsolete.</span></span> <span data-ttu-id="9f926-106">代わりに [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="9f926-106">Use the [ICorProfilerInfo2::GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f926-107">構文</span><span class="sxs-lookup"><span data-stu-id="9f926-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f926-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f926-108">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="9f926-109">[in] ネイティブ コードが関連付けられている関数の ID。</span><span class="sxs-lookup"><span data-stu-id="9f926-109">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="9f926-110">[out] 関数のネイティブ コードを構成するバイトの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9f926-110">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="9f926-111">[out] ネイティブ コードのバイト単位のサイズを指定する整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9f926-111">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f926-112">解説</span><span class="sxs-lookup"><span data-stu-id="9f926-112">Remarks</span></span>  

 <span data-ttu-id="9f926-113">パフォーマンスを最適化するために、.NET Framework Version 2.0 のランタイムは、関数のプリコンパイルされたネイティブ コードを複数の領域に分割します。</span><span class="sxs-lookup"><span data-stu-id="9f926-113">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="9f926-114">したがって、関数のネイティブ コードの範囲を処理できないため、.NET Framework 2.0 では `GetCodeInfo` メソッドは互換性のために残されているだけです。</span><span class="sxs-lookup"><span data-stu-id="9f926-114">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="9f926-115">プロファイラーは、より一般的な `ICorProfilerInfo2::GetCodeInfo2` メソッドを代わりに使用するように切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f926-115">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="9f926-116">この関数は、呼び出し元が割り当てたバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9f926-116">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f926-117">要件</span><span class="sxs-lookup"><span data-stu-id="9f926-117">Requirements</span></span>  

 <span data-ttu-id="9f926-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f926-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f926-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9f926-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9f926-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f926-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f926-121">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="9f926-121">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f926-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f926-122">See also</span></span>

- [<span data-ttu-id="9f926-123">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f926-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="9f926-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f926-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9f926-125">プロファイル</span><span class="sxs-lookup"><span data-stu-id="9f926-125">Profiling</span></span>](index.md)
