---
description: '詳細情報: Co初期化 Ecor 関数'
title: CoInitializeCor 関数
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: e1db9914cce8a92cecf78123a2e247d75ec74acf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799851"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="4959e-103">CoInitializeCor 関数</span><span class="sxs-lookup"><span data-stu-id="4959e-103">CoInitializeCor Function</span></span>

<span data-ttu-id="4959e-104">`CoInitializeCor` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="4959e-104">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4959e-105">構文</span><span class="sxs-lookup"><span data-stu-id="4959e-105">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="4959e-106">解説</span><span class="sxs-lookup"><span data-stu-id="4959e-106">Remarks</span></span>  

 <span data-ttu-id="4959e-107">共通言語ランタイムを初期化するには、 [Corbindtoruntimeex](corbindtoruntimeex-function.md) または [Corbindtoの entruntime](corbindtocurrentruntime-function.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="4959e-107">To initialize the common language runtime, use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4959e-108">要件</span><span class="sxs-lookup"><span data-stu-id="4959e-108">Requirements</span></span>  

 <span data-ttu-id="4959e-109">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4959e-109">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4959e-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4959e-110">See also</span></span>

- [<span data-ttu-id="4959e-111">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="4959e-111">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
