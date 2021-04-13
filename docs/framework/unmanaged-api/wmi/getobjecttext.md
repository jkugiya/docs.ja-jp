---
title: GetObjectText 関数 (アンマネージド API リファレンス)
description: GetObjectText 関数では、MOF 構文でのオブジェクトのテキスト形式のレンダリングが返されます。
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6ad2b29202222d594cc7976a13929002164314a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718372"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="0e1bd-103">GetObjectText 関数</span><span class="sxs-lookup"><span data-stu-id="0e1bd-103">GetObjectText function</span></span>

<span data-ttu-id="0e1bd-104">管理オブジェクト フォーマット (MOF) 構文でのオブジェクトのテキスト形式のレンダリングが返されます。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0e1bd-105">構文</span><span class="sxs-lookup"><span data-stu-id="0e1bd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a><span data-ttu-id="0e1bd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0e1bd-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0e1bd-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0e1bd-108">[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="0e1bd-109">[in] 通常は 0 です。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-109">[in] Normally 0.</span></span> <span data-ttu-id="0e1bd-110">`WBEM_FLAG_NO_FLAVORS` (または 0x1) が指定されている場合、修飾子は伝達または種類の情報なしで含まれます。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

<span data-ttu-id="0e1bd-111">`pstrObjectText` [out] エントリの `null` へのポインター 。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-111">`pstrObjectText` [out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="0e1bd-112">戻り時は、オブジェクトの MOF 構文レンダリングを含む新しく割り当てられた `BSTR` です。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="0e1bd-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="0e1bd-113">Return value</span></span>

<span data-ttu-id="0e1bd-114">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0e1bd-115">定数</span><span class="sxs-lookup"><span data-stu-id="0e1bd-115">Constant</span></span>  |<span data-ttu-id="0e1bd-116">[値]</span><span class="sxs-lookup"><span data-stu-id="0e1bd-116">Value</span></span>  |<span data-ttu-id="0e1bd-117">説明</span><span class="sxs-lookup"><span data-stu-id="0e1bd-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="0e1bd-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0e1bd-118">0x80041001</span></span> | <span data-ttu-id="0e1bd-119">一般エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0e1bd-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0e1bd-120">0x80041008</span></span> | <span data-ttu-id="0e1bd-121">パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0e1bd-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0e1bd-122">0x80041006</span></span> | <span data-ttu-id="0e1bd-123">メモリ不足のため、操作を完了できません。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0e1bd-124">0</span><span class="sxs-lookup"><span data-stu-id="0e1bd-124">0</span></span> | <span data-ttu-id="0e1bd-125">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0e1bd-126">解説</span><span class="sxs-lookup"><span data-stu-id="0e1bd-126">Remarks</span></span>

<span data-ttu-id="0e1bd-127">この関数では、[IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="0e1bd-128">返される MOF テキストには、オブジェクトに関するすべての情報ではなく、MOF コンパイラが元のオブジェクトを再作成するのに十分な情報だけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="0e1bd-129">たとえば、伝達された修飾子や親クラスのプロパティは含まれません。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="0e1bd-130">次のアルゴリズムは、メソッドのパラメーターのテキストを再構築するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="0e1bd-131">パラメーターは、識別子の値の順序で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="0e1bd-132">`[in]` および `[out]` として指定されたパラメーターは、1 つのパラメーターに結合されます。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>

<span data-ttu-id="0e1bd-133">`pstrObjectText` は、関数が呼び出されたときの `null` へのポインターである必要があります。ポインターの割り当ては解除されないため、メソッド呼び出しの前に有効な文字列を指していてはなりません。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e1bd-134">必要条件</span><span class="sxs-lookup"><span data-stu-id="0e1bd-134">Requirements</span></span>  

<span data-ttu-id="0e1bd-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e1bd-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e1bd-136">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0e1bd-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0e1bd-137">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0e1bd-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e1bd-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e1bd-138">See also</span></span>

- [<span data-ttu-id="0e1bd-139">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0e1bd-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
