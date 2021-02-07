---
description: '詳細情報: CoUninitializeCor 関数'
title: CoUninitializeCor 関数
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
ms.openlocfilehash: 1aa3482b6891779b4c85c29079ccd26d7170934e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746205"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="8891a-103">CoUninitializeCor 関数</span><span class="sxs-lookup"><span data-stu-id="8891a-103">CoUninitializeCor Function</span></span>

<span data-ttu-id="8891a-104">`CoUninitializeCor` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="8891a-104">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8891a-105">構文</span><span class="sxs-lookup"><span data-stu-id="8891a-105">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="8891a-106">解説</span><span class="sxs-lookup"><span data-stu-id="8891a-106">Remarks</span></span>  

 <span data-ttu-id="8891a-107">共通言語ランタイムをプロセスからアンロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8891a-107">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="8891a-108">実行中のプロセスからランタイムを完全に削除するには、そのプロセスをシャットダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8891a-108">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8891a-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="8891a-109">See also</span></span>

- [<span data-ttu-id="8891a-110">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="8891a-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
