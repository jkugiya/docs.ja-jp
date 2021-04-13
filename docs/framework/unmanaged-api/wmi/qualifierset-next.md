---
title: QualifierSet_Next 関数 (アンマネージド API リファレンス)
description: QualifierSet_Next 関数では、列挙型内の次の修飾子が取得されます。
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 54d79a3dc081e9cdcb42153b6f7aa457557e3399
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721128"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="24e02-103">QualifierSet_Next 関数</span><span class="sxs-lookup"><span data-stu-id="24e02-103">QualifierSet_Next function</span></span>

<span data-ttu-id="24e02-104">[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) 関数の呼び出しによって開始された列挙型内の次の修飾子が返されます。</span><span class="sxs-lookup"><span data-stu-id="24e02-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="24e02-105">構文</span><span class="sxs-lookup"><span data-stu-id="24e02-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a><span data-ttu-id="24e02-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="24e02-106">Parameters</span></span>

<span data-ttu-id="24e02-107">`vFunc` [in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="24e02-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="24e02-108">`ptr` [in] [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="24e02-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="24e02-109">`lFlags` [in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="24e02-109">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="24e02-110">このパラメーターは、0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="24e02-110">This parameter must be 0.</span></span>

<span data-ttu-id="24e02-111">`pstrName` [out] 修飾子の名前。</span><span class="sxs-lookup"><span data-stu-id="24e02-111">`pstrName` [out] The name of the qualifier.</span></span> <span data-ttu-id="24e02-112">`null` の場合、このパラメーターは無視されます。それ以外の場合、`pstrName` は有効な `BSTR` を指していないか、メモリ リークが発生しています。</span><span class="sxs-lookup"><span data-stu-id="24e02-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="24e02-113">null 値以外の場合、関数では、`WBEM_S_NO_ERROR` を返すときに常に新しい `BSTR` が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="24e02-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

<span data-ttu-id="24e02-114">`pVal` [out] 成功した場合は、修飾子の値。</span><span class="sxs-lookup"><span data-stu-id="24e02-114">`pVal` [out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="24e02-115">関数が失敗した場合、`pVal` が指す `VARIANT` を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="24e02-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="24e02-116">このパラメーターが `null` の場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="24e02-116">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="24e02-117">`plFlavor` [out] 修飾子の種類を受け取る LONG へのポインター。</span><span class="sxs-lookup"><span data-stu-id="24e02-117">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="24e02-118">種類の情報が必要でない場合は、このパラメーターを `null` にすることができます。</span><span class="sxs-lookup"><span data-stu-id="24e02-118">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="24e02-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="24e02-119">Return value</span></span>

<span data-ttu-id="24e02-120">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="24e02-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="24e02-121">定数</span><span class="sxs-lookup"><span data-stu-id="24e02-121">Constant</span></span>  |<span data-ttu-id="24e02-122">[値]</span><span class="sxs-lookup"><span data-stu-id="24e02-122">Value</span></span>  |<span data-ttu-id="24e02-123">説明</span><span class="sxs-lookup"><span data-stu-id="24e02-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="24e02-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="24e02-124">0x80041008</span></span> | <span data-ttu-id="24e02-125">パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="24e02-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="24e02-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="24e02-126">0x8004101d</span></span> | <span data-ttu-id="24e02-127">呼び出し元によって [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) が呼び出されませんでした。</span><span class="sxs-lookup"><span data-stu-id="24e02-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="24e02-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="24e02-128">0x80041006</span></span> | <span data-ttu-id="24e02-129">新しい列挙を開始するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="24e02-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="24e02-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="24e02-130">0x40005</span></span> | <span data-ttu-id="24e02-131">列挙内にはそれ以上修飾子が残されていません。</span><span class="sxs-lookup"><span data-stu-id="24e02-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="24e02-132">0</span><span class="sxs-lookup"><span data-stu-id="24e02-132">0</span></span> | <span data-ttu-id="24e02-133">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="24e02-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="24e02-134">解説</span><span class="sxs-lookup"><span data-stu-id="24e02-134">Remarks</span></span>

<span data-ttu-id="24e02-135">この関数では、[IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="24e02-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="24e02-136">`QualifierSet_Next` 関数を繰り返し呼び出して、関数から `WBEM_S_NO_MORE_DATA` が返されるまですべての修飾子を列挙します。</span><span class="sxs-lookup"><span data-stu-id="24e02-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="24e02-137">列挙を早期に終了するには、[QualifierSet_EndEnumeration](qualifierset-endenumeration.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="24e02-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="24e02-138">列挙中に返される修飾子の順序は定義されていません。</span><span class="sxs-lookup"><span data-stu-id="24e02-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="24e02-139">必要条件</span><span class="sxs-lookup"><span data-stu-id="24e02-139">Requirements</span></span>  

 <span data-ttu-id="24e02-140">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24e02-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24e02-141">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="24e02-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="24e02-142">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="24e02-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e02-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="24e02-143">See also</span></span>

- [<span data-ttu-id="24e02-144">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="24e02-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
