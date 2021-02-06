---
description: '詳細情報: CorExitProcess 関数'
title: CorExitProcess 関数
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: 68d33dec76387e103a34e99c529a4e7aff7535b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649586"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="db872-103">CorExitProcess 関数</span><span class="sxs-lookup"><span data-stu-id="db872-103">CorExitProcess Function</span></span>

<span data-ttu-id="db872-104">現在のアンマネージ プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="db872-104">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="db872-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="db872-105">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="db872-106">代わりに [ICLRMetaHost:: ExitProcess](iclrmetahost-exitprocess-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="db872-106">Use the [ICLRMetaHost::ExitProcess](iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db872-107">構文</span><span class="sxs-lookup"><span data-stu-id="db872-107">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db872-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="db872-108">Parameters</span></span>  

 `exitCode`  
 <span data-ttu-id="db872-109">プロセス終了コードを指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="db872-109">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db872-110">解説</span><span class="sxs-lookup"><span data-stu-id="db872-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db872-111">.NET Framework 4 以降では、 `CorExitProcess` レガシ api がバインドされているランタイムだけでなく、プロセスで開始されたすべてのランタイムを終了します。</span><span class="sxs-lookup"><span data-stu-id="db872-111">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db872-112">要件</span><span class="sxs-lookup"><span data-stu-id="db872-112">Requirements</span></span>  

 <span data-ttu-id="db872-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db872-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db872-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="db872-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db872-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db872-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db872-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db872-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db872-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="db872-117">See also</span></span>

- [<span data-ttu-id="db872-118">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="db872-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
