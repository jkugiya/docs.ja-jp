---
description: 詳細については、「関数ポインターの LPTHREAD_START_ROUTINE」を参照してください。
title: LPTHREAD_START_ROUTINE 関数ポインター
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
ms.openlocfilehash: 9f79cffb0b5290031915b453353dd47cb3959970
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679809"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="e6756-103">LPTHREAD_START_ROUTINE 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="e6756-103">LPTHREAD_START_ROUTINE Function Pointer</span></span>

<span data-ttu-id="e6756-104">スレッドの実行を開始したことをホストに通知する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="e6756-104">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="e6756-105">この関数ポインターは .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="e6756-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6756-106">構文</span><span class="sxs-lookup"><span data-stu-id="e6756-106">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6756-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e6756-107">Parameters</span></span>  

 `lpThreadParameter`  
 <span data-ttu-id="e6756-108">から実行を開始したコードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6756-108">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6756-109">解説</span><span class="sxs-lookup"><span data-stu-id="e6756-109">Remarks</span></span>  

 <span data-ttu-id="e6756-110">`LPTHREAD_START_ROUTINE`ポイントがコールバック関数であり、ホストアプリケーションのライターによって実装されている必要がある関数。</span><span class="sxs-lookup"><span data-stu-id="e6756-110">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6756-111">要件</span><span class="sxs-lookup"><span data-stu-id="e6756-111">Requirements</span></span>  

 <span data-ttu-id="e6756-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6756-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6756-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e6756-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6756-114">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="e6756-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="e6756-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6756-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6756-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6756-116">See also</span></span>

- [<span data-ttu-id="e6756-117">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="e6756-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
