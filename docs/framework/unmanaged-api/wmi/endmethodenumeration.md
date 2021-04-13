---
title: EndMethodEnumeration 関数 (アンマネージド API リファレンス)
description: EndMethodEnumeration 関数では、メソッドの列挙シーケンスが終了します。
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 82f50530967699427d8a00b1c9f518b639273626
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708063"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="1947c-103">EndMethodEnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="1947c-103">EndMethodEnumeration function</span></span>

<span data-ttu-id="1947c-104">[BeginMethodEnumeration 関数](beginmethodenumeration.md)を呼び出すことで開始された列挙シーケンスが終了します。</span><span class="sxs-lookup"><span data-stu-id="1947c-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1947c-105">構文</span><span class="sxs-lookup"><span data-stu-id="1947c-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="1947c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1947c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1947c-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="1947c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1947c-108">[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1947c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="1947c-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="1947c-109">Return value</span></span>

<span data-ttu-id="1947c-110">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="1947c-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1947c-111">定数</span><span class="sxs-lookup"><span data-stu-id="1947c-111">Constant</span></span>  |<span data-ttu-id="1947c-112">[値]</span><span class="sxs-lookup"><span data-stu-id="1947c-112">Value</span></span>  |<span data-ttu-id="1947c-113">説明</span><span class="sxs-lookup"><span data-stu-id="1947c-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="1947c-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="1947c-114">0x8004101d</span></span> | <span data-ttu-id="1947c-115">内部エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1947c-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1947c-116">0</span><span class="sxs-lookup"><span data-stu-id="1947c-116">0</span></span> | <span data-ttu-id="1947c-117">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="1947c-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1947c-118">解説</span><span class="sxs-lookup"><span data-stu-id="1947c-118">Remarks</span></span>

<span data-ttu-id="1947c-119">この関数では、[IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="1947c-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="1947c-120">呼び出し元では、[BeginMethodEnumeration 関数](beginmethodenumeration.md)を使用して列挙シーケンスが開始され、メソッドから `WBEM_S_NO_MORE_DATA` が返されるまで [NextMethod 関数](nextmethod.md )が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1947c-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="1947c-121">呼び出し元は、`EndMethodEnumeration` を呼び出すことによってシーケンスを終了することもできます。</span><span class="sxs-lookup"><span data-stu-id="1947c-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="1947c-122">呼び出し元は、いつでも `EndMethodEnumeration` を呼び出すことによって列挙を早期に終了できます。</span><span class="sxs-lookup"><span data-stu-id="1947c-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="1947c-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="1947c-123">Requirements</span></span>  

 <span data-ttu-id="1947c-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1947c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1947c-125">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1947c-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1947c-126">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1947c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1947c-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="1947c-127">See also</span></span>

- [<span data-ttu-id="1947c-128">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1947c-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
