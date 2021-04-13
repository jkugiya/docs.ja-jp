---
title: NextMethod 関数 (アンマネージド API リファレンス)
description: NextMethod 関数では、列挙内の次のメソッドが取得されます。
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a0466aee47b0a6142870640c78b43f49e221ac2b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726770"
---
# <a name="nextmethod-function"></a><span data-ttu-id="5c49a-103">NextMethod 関数</span><span class="sxs-lookup"><span data-stu-id="5c49a-103">NextMethod function</span></span>

<span data-ttu-id="5c49a-104">[BeginMethodEnumeration](beginmethodenumeration.md) の呼び出しによって開始された列挙内の次のメソッドが取得されます。</span><span class="sxs-lookup"><span data-stu-id="5c49a-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5c49a-105">構文</span><span class="sxs-lookup"><span data-stu-id="5c49a-105">Syntax</span></span>  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```  

## <a name="parameters"></a><span data-ttu-id="5c49a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c49a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5c49a-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="5c49a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5c49a-108">[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5c49a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="5c49a-109">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="5c49a-109">[in] Reserved.</span></span> <span data-ttu-id="5c49a-110">このパラメーターは、0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c49a-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="5c49a-111">[out] 呼び出しの前の `null` を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="5c49a-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="5c49a-112">関数から制御が戻るときに、メソッド名を含む新しい `BSTR` のアドレスが返されます。</span><span class="sxs-lookup"><span data-stu-id="5c49a-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span>

`ppSignatureIn`  
<span data-ttu-id="5c49a-113">[out] メソッドの `in` パラメーターを格納している [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) へのポインターを受け取るポインター。</span><span class="sxs-lookup"><span data-stu-id="5c49a-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span>

`ppSignatureOut`  
<span data-ttu-id="5c49a-114">[out] メソッドの `out` パラメーターを格納している [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) へのポインターを受け取るポインター。</span><span class="sxs-lookup"><span data-stu-id="5c49a-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="5c49a-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="5c49a-115">Return value</span></span>

<span data-ttu-id="5c49a-116">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="5c49a-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5c49a-117">定数</span><span class="sxs-lookup"><span data-stu-id="5c49a-117">Constant</span></span>  |<span data-ttu-id="5c49a-118">[値]</span><span class="sxs-lookup"><span data-stu-id="5c49a-118">Value</span></span>  |<span data-ttu-id="5c49a-119">説明</span><span class="sxs-lookup"><span data-stu-id="5c49a-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="5c49a-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="5c49a-120">0x8004101d</span></span> | <span data-ttu-id="5c49a-121">[`BeginEnumeration`](beginenumeration.md) 関数の呼び出しがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="5c49a-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5c49a-122">0</span><span class="sxs-lookup"><span data-stu-id="5c49a-122">0</span></span> | <span data-ttu-id="5c49a-123">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="5c49a-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="5c49a-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="5c49a-124">0x40005</span></span> | <span data-ttu-id="5c49a-125">列挙にはこれ以上プロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="5c49a-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="5c49a-126">解説</span><span class="sxs-lookup"><span data-stu-id="5c49a-126">Remarks</span></span>

<span data-ttu-id="5c49a-127">この関数では、[IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="5c49a-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="5c49a-128">呼び出し元では、[BeginMethodEnumeration 関数](beginmethodenumeration.md)を呼び出すことで列挙シーケンスが開始され、関数から `WBEM_S_NO_MORE_DATA` が返されるまで [NextMethod] 関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5c49a-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="5c49a-129">必要に応じて、呼び出し元では [EndMethodEnumeration](endmethodenumeration.md) を呼び出すことによってシーケンスを終了します。</span><span class="sxs-lookup"><span data-stu-id="5c49a-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="5c49a-130">呼び出し元は、いつでも [EndMethodEnumeration](endmethodenumeration.md) を呼び出すことによって列挙を早期に終了できます。</span><span class="sxs-lookup"><span data-stu-id="5c49a-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="5c49a-131">例</span><span class="sxs-lookup"><span data-stu-id="5c49a-131">Example</span></span>

<span data-ttu-id="5c49a-132">C++ の例については、「[IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) メソッド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c49a-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5c49a-133">必要条件</span><span class="sxs-lookup"><span data-stu-id="5c49a-133">Requirements</span></span>  

 <span data-ttu-id="5c49a-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c49a-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c49a-135">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5c49a-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5c49a-136">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5c49a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c49a-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c49a-137">See also</span></span>

- [<span data-ttu-id="5c49a-138">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5c49a-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
