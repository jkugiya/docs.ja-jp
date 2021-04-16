---
description: '詳細情報: _EFN_GetManagedObjectFieldInfo 関数'
title: _EFN_GetManagedObjectFieldInfo 関数
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
ms.openlocfilehash: 749ab286a86db07c1b66ff2b61ff073d15334800
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637888"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="12b82-103">\_EFN\_GetManagedObjectFieldInfo 関数</span><span class="sxs-lookup"><span data-stu-id="12b82-103">\_EFN\_GetManagedObjectFieldInfo Function</span></span>

<span data-ttu-id="12b82-104">指定したオブジェクト ポインターとフィールド名を使用して、オブジェクトの先頭からフィールドまでのオフセットとフィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="12b82-104">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b82-105">構文</span><span class="sxs-lookup"><span data-stu-id="12b82-105">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12b82-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12b82-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="12b82-107">[in] デバッグ クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="12b82-107">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="12b82-108">[in] マネージド オブジェクト ポインター。</span><span class="sxs-lookup"><span data-stu-id="12b82-108">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="12b82-109">szFieldName</span><span class="sxs-lookup"><span data-stu-id="12b82-109">szFieldName</span></span>  
 <span data-ttu-id="12b82-110">[in] フィールド名へのマネージド オブジェクト ポインター。</span><span class="sxs-lookup"><span data-stu-id="12b82-110">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="12b82-111">[out] フィールド値。</span><span class="sxs-lookup"><span data-stu-id="12b82-111">[out] The field value.</span></span> <span data-ttu-id="12b82-112">このパラメーターには、null を指定できます。</span><span class="sxs-lookup"><span data-stu-id="12b82-112">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="12b82-113">[out] `objAddr` からフィールドまでのオフセット。</span><span class="sxs-lookup"><span data-stu-id="12b82-113">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="12b82-114">このパラメーターには、null を指定できます。</span><span class="sxs-lookup"><span data-stu-id="12b82-114">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12b82-115">解説</span><span class="sxs-lookup"><span data-stu-id="12b82-115">Remarks</span></span>  

 <span data-ttu-id="12b82-116">オフセットが 0 の場合、オフセットは書き込まれません。</span><span class="sxs-lookup"><span data-stu-id="12b82-116">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="12b82-117">現在コンテキスト内にあるスレッドにマネージド コードがない場合、この関数では、ファシリティ値が 0xa0 でエラー コードが 0x1000 の HRESULT SOS_E_NOMANAGEDCODE が返されます。</span><span class="sxs-lookup"><span data-stu-id="12b82-117">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12b82-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="12b82-118">Requirements</span></span>  

 <span data-ttu-id="12b82-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12b82-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12b82-120">**ヘッダー:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="12b82-120">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="12b82-121">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12b82-121">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b82-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="12b82-122">See also</span></span>

- [<span data-ttu-id="12b82-123">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="12b82-123">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
