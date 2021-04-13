---
title: GetErrorInfo 関数 (アンマネージド API リファレンス)
description: GetErrorInfo 関数では、前の関数呼び出しからのエラー情報が取得されます。
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5da4eaa459c515689b822e4cb537380245e800e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722766"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="d8405-103">GetErrorInfo 関数</span><span class="sxs-lookup"><span data-stu-id="d8405-103">GetErrorInfo function</span></span>

<span data-ttu-id="d8405-104">前の関数呼び出しからエラー情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="d8405-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d8405-105">構文</span><span class="sxs-lookup"><span data-stu-id="d8405-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="d8405-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="d8405-106">Return value</span></span>

<span data-ttu-id="d8405-107">関数呼び出しが成功した場合は、[IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) オブジェクトへのポインター。失敗した場合は `null`。</span><span class="sxs-lookup"><span data-stu-id="d8405-107">An pointer to an [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="d8405-108">解説</span><span class="sxs-lookup"><span data-stu-id="d8405-108">Remarks</span></span>

<span data-ttu-id="d8405-109">この関数では、[IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="d8405-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8405-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="d8405-110">Requirements</span></span>  

 <span data-ttu-id="d8405-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8405-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8405-112">**ヘッダー:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="d8405-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="d8405-113">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d8405-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8405-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8405-114">See also</span></span>

- [<span data-ttu-id="d8405-115">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d8405-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
