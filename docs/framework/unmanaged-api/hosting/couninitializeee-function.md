---
description: '詳細情報: CoUninitializeEE 関数'
title: CoUninitializeEE 関数
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: e356135ea027bd52520eff9084ad2f7f09e1fe0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746166"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="7166b-103">CoUninitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="7166b-103">CoUninitializeEE Function</span></span>

<span data-ttu-id="7166b-104">`CoUninitializeEE` は互換性のために残されており、機能を提供しません。</span><span class="sxs-lookup"><span data-stu-id="7166b-104">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7166b-105">構文</span><span class="sxs-lookup"><span data-stu-id="7166b-105">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="7166b-106">解説</span><span class="sxs-lookup"><span data-stu-id="7166b-106">Remarks</span></span>  

 <span data-ttu-id="7166b-107">共通言語ランタイムの実行エンジンをプロセスからアンロードできません。</span><span class="sxs-lookup"><span data-stu-id="7166b-107">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="7166b-108">実行エンジンをシャットダウンするには、 [CorExitProcess](corexitprocess-function.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7166b-108">To shut down the execution engine call [CorExitProcess](corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7166b-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="7166b-109">See also</span></span>

- [<span data-ttu-id="7166b-110">CoInitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="7166b-110">CoInitializeEE Function</span></span>](coinitializeee-function.md)
- [<span data-ttu-id="7166b-111">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="7166b-111">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
