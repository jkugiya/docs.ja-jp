---
title: WritePropertyValue 関数 (アンマネージド API リファレンス)
description: WritePropertyValue 関数では、プロパティにバイトが書き込まれます。
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e225516b06c477dc1a24cf721bc3e1ade9076b75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729409"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="668e0-103">WritePropertyValue 関数</span><span class="sxs-lookup"><span data-stu-id="668e0-103">WritePropertyValue function</span></span>

<span data-ttu-id="668e0-104">指定したバイト数が、プロパティ ハンドルによって識別されるプロパティに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="668e0-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="668e0-105">構文</span><span class="sxs-lookup"><span data-stu-id="668e0-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="668e0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="668e0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="668e0-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="668e0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="668e0-108">[in] [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="668e0-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="668e0-109">[in] このプロパティを識別するハンドルを格納している整数。</span><span class="sxs-lookup"><span data-stu-id="668e0-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="668e0-110">ハンドルは、[GetPropertyHandle](getpropertyhandle.md) 関数を呼び出すことによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="668e0-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="668e0-111">[in] プロパティに書き込まれるバイト数。</span><span class="sxs-lookup"><span data-stu-id="668e0-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="668e0-112">詳細については、「[解説](#remarks)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="668e0-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="668e0-113">`pHandle` [out] データが格納されているバイト配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="668e0-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="668e0-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="668e0-114">Return value</span></span>

<span data-ttu-id="668e0-115">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="668e0-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="668e0-116">定数</span><span class="sxs-lookup"><span data-stu-id="668e0-116">Constant</span></span>  |<span data-ttu-id="668e0-117">[値]</span><span class="sxs-lookup"><span data-stu-id="668e0-117">Value</span></span>  |<span data-ttu-id="668e0-118">説明</span><span class="sxs-lookup"><span data-stu-id="668e0-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="668e0-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="668e0-119">0x80041008</span></span> | <span data-ttu-id="668e0-120">パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="668e0-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="668e0-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="668e0-121">0x80041005</span></span> | <span data-ttu-id="668e0-122">型の不一致が発生しました。</span><span class="sxs-lookup"><span data-stu-id="668e0-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="668e0-123">0</span><span class="sxs-lookup"><span data-stu-id="668e0-123">0</span></span> | <span data-ttu-id="668e0-124">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="668e0-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="668e0-125">解説</span><span class="sxs-lookup"><span data-stu-id="668e0-125">Remarks</span></span>

<span data-ttu-id="668e0-126">この関数では、[IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="668e0-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="668e0-127">この関数を使用して、文字列と、`DWORD` または `QWORD` 以外のその他すべてのデータを設定できます。</span><span class="sxs-lookup"><span data-stu-id="668e0-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="668e0-128">文字列以外のプロパティ値の場合、`lNumBytes` は、指定されたプロパティ型の正しいデータ サイズである必要があります。</span><span class="sxs-lookup"><span data-stu-id="668e0-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="668e0-129">文字列プロパティ値の場合、`lNumBytes` は、指定された文字列の長さ (バイト単位) である必要があり、文字列自体は偶数バイト単位の長さで、その後に null 終端文字が続く必要があります。</span><span class="sxs-lookup"><span data-stu-id="668e0-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="668e0-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="668e0-130">Requirements</span></span>  

<span data-ttu-id="668e0-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="668e0-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="668e0-132">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="668e0-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="668e0-133">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="668e0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="668e0-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="668e0-134">See also</span></span>

- [<span data-ttu-id="668e0-135">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="668e0-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
