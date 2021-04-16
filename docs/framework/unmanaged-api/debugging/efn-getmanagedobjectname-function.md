---
description: '詳細情報: _EFN_GetManagedObjectName 関数'
title: _EFN_GetManagedObjectName 関数
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
ms.openlocfilehash: 4fa47848ace973f43acbcf8ab0322db4b974b205
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637899"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="58763-103">\_EFN\_GetManagedObjectName 関数</span><span class="sxs-lookup"><span data-stu-id="58763-103">\_EFN\_GetManagedObjectName Function</span></span>

<span data-ttu-id="58763-104">指定したマネージド オブジェクトのポインターを使用して、型の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="58763-104">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58763-105">構文</span><span class="sxs-lookup"><span data-stu-id="58763-105">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58763-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="58763-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="58763-107">[in] デバッグ クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58763-107">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="58763-108">[in] マネージド オブジェクト ポインター。</span><span class="sxs-lookup"><span data-stu-id="58763-108">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="58763-109">szName</span><span class="sxs-lookup"><span data-stu-id="58763-109">szName</span></span>  
 <span data-ttu-id="58763-110">[out] 型の名前。</span><span class="sxs-lookup"><span data-stu-id="58763-110">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="58763-111">[out] 文字列バッファーで使用できる文字数。</span><span class="sxs-lookup"><span data-stu-id="58763-111">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58763-112">解説</span><span class="sxs-lookup"><span data-stu-id="58763-112">Remarks</span></span>  

 <span data-ttu-id="58763-113">現在コンテキスト内にあるスレッドにマネージド コードがない場合、この関数では、ファシリティ値が 0xa0 でエラー コードが 0x1000 の HRESULT SOS_E_NOMANAGEDCODE が返されます。</span><span class="sxs-lookup"><span data-stu-id="58763-113">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58763-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="58763-114">Requirements</span></span>  

 <span data-ttu-id="58763-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58763-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58763-116">**ヘッダー:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="58763-116">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="58763-117">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58763-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58763-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="58763-118">See also</span></span>

- [<span data-ttu-id="58763-119">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="58763-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
