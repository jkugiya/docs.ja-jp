---
title: ResetSecurity 関数 (アンマネージド API リファレンス)
description: ResetSecurity 関数では、現在のスレッドに偽装トークンが割り当てられます。
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 259bef74356f16221f1453dd4086e2fbb26faa83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721115"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="1a0f3-103">ResetSecurity 関数</span><span class="sxs-lookup"><span data-stu-id="1a0f3-103">ResetSecurity function</span></span>

<span data-ttu-id="1a0f3-104">指定した偽装トークンが現在のスレッドに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1a0f3-104">Assigns the supplied impersonation token to the current thread.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1a0f3-105">構文</span><span class="sxs-lookup"><span data-stu-id="1a0f3-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a><span data-ttu-id="1a0f3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1a0f3-106">Parameters</span></span>

`token`  
<span data-ttu-id="1a0f3-107">[in] 現在のスレッドに関連付ける偽装トークン。</span><span class="sxs-lookup"><span data-stu-id="1a0f3-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="1a0f3-108">この値は `null` の場合もあります。</span><span class="sxs-lookup"><span data-stu-id="1a0f3-108">Its value can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="1a0f3-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="1a0f3-109">Return value</span></span>

<span data-ttu-id="1a0f3-110">関数が成功した場合の戻り値は `S_OK` (0) です。</span><span class="sxs-lookup"><span data-stu-id="1a0f3-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="1a0f3-111">関数が失敗した場合の戻り値はゼロ以外のエラー コードです。</span><span class="sxs-lookup"><span data-stu-id="1a0f3-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="1a0f3-112">拡張されたエラー情報を取得するには、[GetErrorInfo](geterrorinfo.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1a0f3-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="1a0f3-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="1a0f3-113">Requirements</span></span>  

 <span data-ttu-id="1a0f3-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a0f3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a0f3-115">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1a0f3-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1a0f3-116">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1a0f3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a0f3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a0f3-117">See also</span></span>

- [<span data-ttu-id="1a0f3-118">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1a0f3-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
