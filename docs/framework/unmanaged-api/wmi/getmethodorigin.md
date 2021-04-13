---
title: GetMethodOrigin 関数 (アンマネージド API リファレンス)
description: GetMethodOrigin 関数では、メソッドを宣言しているクラスが特定されます。
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 434392ffb4d9124e319bcd9c42fdd340d3fec5b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722779"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="c86d8-103">GetMethodOrigin 関数</span><span class="sxs-lookup"><span data-stu-id="c86d8-103">GetMethodOrigin function</span></span>

<span data-ttu-id="c86d8-104">メソッドを宣言しているクラスが特定されます。</span><span class="sxs-lookup"><span data-stu-id="c86d8-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="c86d8-105">構文</span><span class="sxs-lookup"><span data-stu-id="c86d8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a><span data-ttu-id="c86d8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c86d8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c86d8-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="c86d8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="c86d8-108">[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c86d8-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="c86d8-109">[in] 所有クラスが要求されているオブジェクトのメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="c86d8-109">[in] The name of the method for the object whose owning class is being requested.</span></span>

`pstrClassName`  
<span data-ttu-id="c86d8-110">[out] メソッドを所有するクラスの名前を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c86d8-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="c86d8-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="c86d8-111">Return value</span></span>

<span data-ttu-id="c86d8-112">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="c86d8-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c86d8-113">定数</span><span class="sxs-lookup"><span data-stu-id="c86d8-113">Constant</span></span>  |<span data-ttu-id="c86d8-114">[値]</span><span class="sxs-lookup"><span data-stu-id="c86d8-114">Value</span></span>  |<span data-ttu-id="c86d8-115">説明</span><span class="sxs-lookup"><span data-stu-id="c86d8-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="c86d8-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c86d8-116">0x80041002</span></span> | <span data-ttu-id="c86d8-117">指定したメソッドが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="c86d8-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c86d8-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c86d8-118">0x80041008</span></span> | <span data-ttu-id="c86d8-119">1 つ以上のパラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="c86d8-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c86d8-120">0</span><span class="sxs-lookup"><span data-stu-id="c86d8-120">0</span></span> | <span data-ttu-id="c86d8-121">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="c86d8-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c86d8-122">解説</span><span class="sxs-lookup"><span data-stu-id="c86d8-122">Remarks</span></span>

<span data-ttu-id="c86d8-123">この関数では、[IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="c86d8-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="c86d8-124">クラスは 1 つまたは複数の基底クラスからメソッドを継承できるため、多くの場合、開発者は特定のメソッドが定義されているクラスを判別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c86d8-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="c86d8-125">`pstrClassName` パラメーターは `out` パラメーターであるため、この関数が呼び出される前は有効な `BSTR` を指していてはなりません。このポインターは、関数から制御が戻った後に割り当て解除されません。</span><span class="sxs-lookup"><span data-stu-id="c86d8-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="c86d8-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="c86d8-126">Requirements</span></span>  

<span data-ttu-id="c86d8-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c86d8-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c86d8-128">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c86d8-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c86d8-129">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c86d8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c86d8-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="c86d8-130">See also</span></span>

- [<span data-ttu-id="c86d8-131">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c86d8-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
