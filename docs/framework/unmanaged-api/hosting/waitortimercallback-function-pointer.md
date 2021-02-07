---
description: '詳細情報: WAITORTIMERCALLBACK 関数ポインター'
title: WAITORTIMERCALLBACK 関数ポインター
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
ms.openlocfilehash: 6fd9e7eab56e48086eefcb26fc48cbf5f45d4a0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679057"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="615f5-103">WAITORTIMERCALLBACK 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="615f5-103">WAITORTIMERCALLBACK Function Pointer</span></span>

<span data-ttu-id="615f5-104">待機ハンドル () がシグナル状態になったか、タイムアウトしたことをホストに通知する関数を指し <xref:System.Threading.WaitHandle> ます。</span><span class="sxs-lookup"><span data-stu-id="615f5-104">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="615f5-105">この関数ポインターは .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="615f5-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="615f5-106">構文</span><span class="sxs-lookup"><span data-stu-id="615f5-106">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="615f5-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="615f5-107">Parameters</span></span>  

 `lpParameter`  
 <span data-ttu-id="615f5-108">からホストによって定義された情報を格納しているオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="615f5-108">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="615f5-109">[入力] `true` 待機ハンドルがタイムアウトした場合は `false` 。それがシグナル状態だった場合は。</span><span class="sxs-lookup"><span data-stu-id="615f5-109">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="615f5-110">解説</span><span class="sxs-lookup"><span data-stu-id="615f5-110">Remarks</span></span>  

 <span data-ttu-id="615f5-111">`WAITORTIMERCALLBACK`ポイントがコールバック関数であり、ホストアプリケーションのライターによって実装されている必要がある関数。</span><span class="sxs-lookup"><span data-stu-id="615f5-111">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="615f5-112">要件</span><span class="sxs-lookup"><span data-stu-id="615f5-112">Requirements</span></span>  

 <span data-ttu-id="615f5-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="615f5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="615f5-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="615f5-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="615f5-115">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="615f5-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="615f5-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="615f5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="615f5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="615f5-117">See also</span></span>

- [<span data-ttu-id="615f5-118">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="615f5-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
