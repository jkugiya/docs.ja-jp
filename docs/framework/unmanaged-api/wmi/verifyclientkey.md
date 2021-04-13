---
title: VerifyClientKey 関数 (アンマネージド API リファレンス)
description: VerifyClientKey 関数によって、クライアント キーのセキュリティが適切であることが確認されます。
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 26cffe9936f2e01078b6f54e8499b58519f1018e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729422"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="30322-103">VerifyClientKey 関数</span><span class="sxs-lookup"><span data-stu-id="30322-103">VerifyClientKey function</span></span>

<span data-ttu-id="30322-104">クライアント キーに適切なセキュリティが確実に含められます。</span><span class="sxs-lookup"><span data-stu-id="30322-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="30322-105">構文</span><span class="sxs-lookup"><span data-stu-id="30322-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a><span data-ttu-id="30322-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="30322-106">Return value</span></span>

<span data-ttu-id="30322-107">関数が成功した場合の戻り値は `ERROR_SUCCESS` (0) です。</span><span class="sxs-lookup"><span data-stu-id="30322-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="30322-108">関数が失敗した場合、戻り値は *WinError.h* で定義されている 0 以外のエラー コードです。</span><span class="sxs-lookup"><span data-stu-id="30322-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="30322-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="30322-109">Requirements</span></span>  

 <span data-ttu-id="30322-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30322-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30322-111">**ヘッダー:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="30322-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="30322-112">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="30322-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30322-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="30322-113">See also</span></span>

- [<span data-ttu-id="30322-114">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="30322-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
