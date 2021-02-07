---
description: '詳細について: ICoreClrDebugTarget:: EnumProcesses メソッド'
title: ICoreClrDebugTarget::EnumProcesses メソッド
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 73dc8a2b00f7a57879855158e6b871117d015f3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738040"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="7163f-103">ICoreClrDebugTarget::EnumProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="7163f-103">ICoreClrDebugTarget::EnumProcesses Method</span></span>

<span data-ttu-id="7163f-104">リモート コンピューターで実行されているプロセスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="7163f-104">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7163f-105">構文</span><span class="sxs-lookup"><span data-stu-id="7163f-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7163f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7163f-106">Parameters</span></span>  

 `pcProcs`  
 <span data-ttu-id="7163f-107">[out] `ppProcs` に返されるプロセス数。</span><span class="sxs-lookup"><span data-stu-id="7163f-107">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="7163f-108">この値は 0 (ゼロ) になる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="7163f-108">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="7163f-109">入出力リモートコンピューター上で実行されているプロセスを表す [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) 構造体の配列。</span><span class="sxs-lookup"><span data-stu-id="7163f-109">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7163f-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="7163f-110">Return Value</span></span>  

 <span data-ttu-id="7163f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7163f-111">S_OK</span></span>  
 <span data-ttu-id="7163f-112">正常終了しました。</span><span class="sxs-lookup"><span data-stu-id="7163f-112">Success.</span></span>  
  
 <span data-ttu-id="7163f-113">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7163f-113">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="7163f-114">`ppProcs`  用に十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="7163f-114">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="7163f-115">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="7163f-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7163f-116">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7163f-116">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7163f-117">解説</span><span class="sxs-lookup"><span data-stu-id="7163f-117">Remarks</span></span>  

 <span data-ttu-id="7163f-118">このメソッドによって割り当てられたメモリを解放するには、 [ICoreClrDebugTarget:: FreeMemory](icoreclrdebugtarget-freememory-method.md) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7163f-118">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7163f-119">要件</span><span class="sxs-lookup"><span data-stu-id="7163f-119">Requirements</span></span>  

 <span data-ttu-id="7163f-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7163f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7163f-121">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="7163f-121">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="7163f-122">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="7163f-122">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="7163f-123">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="7163f-123">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7163f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="7163f-124">See also</span></span>

- [<span data-ttu-id="7163f-125">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7163f-125">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
