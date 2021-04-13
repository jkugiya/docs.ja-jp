---
title: GetCurrentApartmentType 関数 (アンマネージド API リファレンス)
description: GetCurrentApartmentType 関数では、呼び出し元が実行されているアパートメントの種類が取得されます。
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0832867d86b7dda80e037846d9aa66c1d37f87be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726198"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="34104-103">GetCurrentApartmentType 関数</span><span class="sxs-lookup"><span data-stu-id="34104-103">GetCurrentApartmentType function</span></span>

<span data-ttu-id="34104-104">呼び出し元が実行されているアパートメントの種類が取得されます。</span><span class="sxs-lookup"><span data-stu-id="34104-104">Retrieves the type of apartment in which the caller is executing.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="34104-105">構文</span><span class="sxs-lookup"><span data-stu-id="34104-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a><span data-ttu-id="34104-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34104-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="34104-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="34104-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="34104-108">[in] [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="34104-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="34104-109">[out] 呼び出し元のアパートメントを示す [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="34104-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="34104-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="34104-110">Return value</span></span>

|<span data-ttu-id="34104-111">定数</span><span class="sxs-lookup"><span data-stu-id="34104-111">Constant</span></span>  |<span data-ttu-id="34104-112">[値]</span><span class="sxs-lookup"><span data-stu-id="34104-112">Value</span></span>  |<span data-ttu-id="34104-113">説明</span><span class="sxs-lookup"><span data-stu-id="34104-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="34104-114">0</span><span class="sxs-lookup"><span data-stu-id="34104-114">0</span></span> | <span data-ttu-id="34104-115">関数は正常に終了しました。</span><span class="sxs-lookup"><span data-stu-id="34104-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="34104-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="34104-116">0x80000008</span></span> | <span data-ttu-id="34104-117">呼び出し元がアパートメント内で実行されていません。</span><span class="sxs-lookup"><span data-stu-id="34104-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="34104-118">解説</span><span class="sxs-lookup"><span data-stu-id="34104-118">Remarks</span></span>

<span data-ttu-id="34104-119">この関数では、[IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="34104-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="34104-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="34104-120">Requirements</span></span>  

 <span data-ttu-id="34104-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34104-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34104-122">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="34104-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="34104-123">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="34104-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34104-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="34104-124">See also</span></span>

- [<span data-ttu-id="34104-125">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="34104-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
