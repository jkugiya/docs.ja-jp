---
description: '詳細については、次を参照してください: CorMarkThreadInThreadPool 関数'
title: CorMarkThreadInThreadPool 関数
ms.date: 03/30/2017
api_name:
- CorMarkThreadInThreadPool
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorMarkThreadInThreadPool
helpviewer_keywords:
- CorMarkThreadInThreadPool function [.NET Framework hosting]
ms.assetid: 3f958d41-e82e-4ec3-ae6f-16c7b3b31e3e
topic_type:
- apiref
ms.openlocfilehash: 68d945870075f2f8c06fe76b7a71e2f806078694
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716940"
---
# <a name="cormarkthreadinthreadpool-function"></a><span data-ttu-id="b4072-103">CorMarkThreadInThreadPool 関数</span><span class="sxs-lookup"><span data-stu-id="b4072-103">CorMarkThreadInThreadPool Function</span></span>

<span data-ttu-id="b4072-104">現在実行されているスレッド プールのスレッドに、マネージド コードの実行のマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="b4072-104">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="b4072-105">.NET Framework Version 2.0 以降では、この関数に効力はありません。</span><span class="sxs-lookup"><span data-stu-id="b4072-105">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="b4072-106">必ずしも必要はありませんが、この関数はコードから削除できます。</span><span class="sxs-lookup"><span data-stu-id="b4072-106">It is not required, and can be removed from your code.</span></span> <span data-ttu-id="b4072-107">この関数は .NET Framework 4 では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="b4072-107">This function is deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4072-108">構文</span><span class="sxs-lookup"><span data-stu-id="b4072-108">Syntax</span></span>  
  
```cpp  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="b4072-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="b4072-109">Requirements</span></span>  

 <span data-ttu-id="b4072-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4072-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4072-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b4072-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4072-112">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4072-112">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4072-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4072-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4072-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4072-114">See also</span></span>

- [<span data-ttu-id="b4072-115">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="b4072-115">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
