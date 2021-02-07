---
description: '詳細情報: _EFN_GetManagedExcepStack 関数'
title: _EFN_GetManagedExcepStack 関数
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: a3c7e30a377e10b9d4d0b1dd663a594a0e872f3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738313"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="27350-103">\_EFN \_ getmanagedexcepstack 関数</span><span class="sxs-lookup"><span data-stu-id="27350-103">\_EFN\_GetManagedExcepStack Function</span></span>

<span data-ttu-id="27350-104">指定したマネージド例外オブジェクトのアドレスに応じて、中に含まれているスタック トレースの文字列バージョンを返します。</span><span class="sxs-lookup"><span data-stu-id="27350-104">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27350-105">構文</span><span class="sxs-lookup"><span data-stu-id="27350-105">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27350-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="27350-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="27350-107">からデバッグ中のクライアント。</span><span class="sxs-lookup"><span data-stu-id="27350-107">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="27350-108">からから派生したマネージオブジェクトポインター <xref:System.Exception> 。</span><span class="sxs-lookup"><span data-stu-id="27350-108">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="27350-109">szStackString</span><span class="sxs-lookup"><span data-stu-id="27350-109">szStackString</span></span>  
 <span data-ttu-id="27350-110">入出力返された文字列。</span><span class="sxs-lookup"><span data-stu-id="27350-110">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="27350-111">入出力文字列バッファーで使用できる文字数。</span><span class="sxs-lookup"><span data-stu-id="27350-111">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27350-112">解説</span><span class="sxs-lookup"><span data-stu-id="27350-112">Remarks</span></span>  

 <span data-ttu-id="27350-113">現在コンテキスト内にあるスレッドにマネージコードがない場合、関数は、ファシリティ値が0xa0 でエラーコードが0x1000 の HRESULT SOS_E_NOMANAGEDCODE を返します。</span><span class="sxs-lookup"><span data-stu-id="27350-113">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27350-114">要件</span><span class="sxs-lookup"><span data-stu-id="27350-114">Requirements</span></span>  

 <span data-ttu-id="27350-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27350-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27350-116">**ヘッダー:** SOS_Stacktrace</span><span class="sxs-lookup"><span data-stu-id="27350-116">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="27350-117">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27350-117">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27350-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="27350-118">See also</span></span>

- [<span data-ttu-id="27350-119">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="27350-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
