---
description: '詳細について: ICorThreadpool:: CorCreateTimer メソッド'
title: ICorThreadpool::CorCreateTimer メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCreateTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type:
- apiref
ms.openlocfilehash: dc4258493181430a7e803f3b995e6b32ed2cd8b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737779"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="dccbe-103">ICorThreadpool::CorCreateTimer メソッド</span><span class="sxs-lookup"><span data-stu-id="dccbe-103">ICorThreadpool::CorCreateTimer Method</span></span>

<span data-ttu-id="dccbe-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="dccbe-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dccbe-105">構文</span><span class="sxs-lookup"><span data-stu-id="dccbe-105">Syntax</span></span>  
  
```cpp  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="dccbe-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="dccbe-106">Requirements</span></span>  

 <span data-ttu-id="dccbe-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dccbe-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dccbe-108">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="dccbe-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dccbe-109">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="dccbe-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dccbe-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dccbe-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dccbe-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="dccbe-111">See also</span></span>

- [<span data-ttu-id="dccbe-112">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dccbe-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
