---
description: '詳細について: ICoreClrDebugTarget:: EnumRuntimes メソッド'
title: ICoreClrDebugTarget::EnumRuntimes メソッド
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
ms.openlocfilehash: 675747106b2acec2e8be3fcdf15831958bea7c7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794625"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="b477e-103">ICoreClrDebugTarget::EnumRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="b477e-103">ICoreClrDebugTarget::EnumRuntimes Method</span></span>

<span data-ttu-id="b477e-104">リモート コンピューターで実行されている指定のプロセスの共通言語ランタイム (CLR: Common Language Runtime) を列挙します。</span><span class="sxs-lookup"><span data-stu-id="b477e-104">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b477e-105">構文</span><span class="sxs-lookup"><span data-stu-id="b477e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b477e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b477e-106">Parameters</span></span>  

 `dwInternalProcessID`  
 <span data-ttu-id="b477e-107">[in] ランタイムを列挙するプロセスの内部プロセス ID。</span><span class="sxs-lookup"><span data-stu-id="b477e-107">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="b477e-108">これは `m_dwInternalID` 、対応する [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)からのものになります。</span><span class="sxs-lookup"><span data-stu-id="b477e-108">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="b477e-109">[out] `ppRuntimes` に返されるランタイム数。</span><span class="sxs-lookup"><span data-stu-id="b477e-109">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="b477e-110">この値は 0 (ゼロ) になる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="b477e-110">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="b477e-111">入出力リモートターゲットプロセスに読み込まれたランタイムを表す [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) 構造体の配列。</span><span class="sxs-lookup"><span data-stu-id="b477e-111">[out] An array of [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b477e-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="b477e-112">Return Value</span></span>  

 <span data-ttu-id="b477e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b477e-113">S_OK</span></span>  
 <span data-ttu-id="b477e-114">正常終了しました。</span><span class="sxs-lookup"><span data-stu-id="b477e-114">Success.</span></span>  
  
 <span data-ttu-id="b477e-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b477e-115">S_FALSE</span></span>  
 <span data-ttu-id="b477e-116">`dwInternalProcessID` が、コンピューターで実行されているどのプロセスにも一致しません。多くの場合、プロセスが既に終了していることが原因です。</span><span class="sxs-lookup"><span data-stu-id="b477e-116">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="b477e-117">`pcRuntimes` と `ppRuntimes` は null になります。</span><span class="sxs-lookup"><span data-stu-id="b477e-117">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="b477e-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b477e-118">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b477e-119">`ppRuntimes`  用に十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="b477e-119">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="b477e-120">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="b477e-120">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b477e-121">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b477e-121">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b477e-122">解説</span><span class="sxs-lookup"><span data-stu-id="b477e-122">Remarks</span></span>  

 <span data-ttu-id="b477e-123">このメソッドによって割り当てられたメモリを解放するには、 [ICoreClrDebugTarget:: FreeMemory](icoreclrdebugtarget-freememory-method.md) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b477e-123">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b477e-124">要件</span><span class="sxs-lookup"><span data-stu-id="b477e-124">Requirements</span></span>  

 <span data-ttu-id="b477e-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b477e-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b477e-126">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="b477e-126">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b477e-127">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b477e-127">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b477e-128">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b477e-128">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b477e-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="b477e-129">See also</span></span>

- [<span data-ttu-id="b477e-130">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b477e-130">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
