---
title: Next 関数 (アンマネージド API リファレンス)
description: Next 関数では、列挙内の次のプロパティが取得されます。
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c2a7fae32e82caae40a95bfdad10fa78082988ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726787"
---
# <a name="next-function"></a><span data-ttu-id="81b68-103">Next 関数</span><span class="sxs-lookup"><span data-stu-id="81b68-103">Next function</span></span>

<span data-ttu-id="81b68-104">[BeginEnumeration](beginenumeration.md) の呼び出しによって開始された列挙内の次のプロパティが取得されます。</span><span class="sxs-lookup"><span data-stu-id="81b68-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="81b68-105">構文</span><span class="sxs-lookup"><span data-stu-id="81b68-105">Syntax</span></span>

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="81b68-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81b68-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="81b68-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="81b68-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="81b68-108">[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="81b68-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`\
<span data-ttu-id="81b68-109">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="81b68-109">[in] Reserved.</span></span> <span data-ttu-id="81b68-110">このパラメーターは、0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="81b68-110">This parameter must be 0.</span></span>

`pstrName`\
<span data-ttu-id="81b68-111">[out] プロパティ名を格納している新しい `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="81b68-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="81b68-112">名前が不要な場合は、このパラメーターを `null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="81b68-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`\
<span data-ttu-id="81b68-113">[out] プロパティの値が格納された `VARIANT`。</span><span class="sxs-lookup"><span data-stu-id="81b68-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="81b68-114">値が不要な場合は、このパラメーターを `null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="81b68-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="81b68-115">関数からエラー コードが返される場合、`pVal` に渡された `VARIANT` は変更されずに残ります。</span><span class="sxs-lookup"><span data-stu-id="81b68-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span>

`pvtType`\
<span data-ttu-id="81b68-116">[out] `CIMTYPE` 変数 (プロパティの型が配置される `LONG`) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81b68-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="81b68-117">このプロパティの値には、`VT_NULL_VARIANT` を指定できます。この場合、プロパティの実際の型を特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81b68-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="81b68-118">このパラメーターは、`null` にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="81b68-118">This parameter can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="81b68-119">[out] `null`、またはプロパティの発生元に関する情報を受け取る値。</span><span class="sxs-lookup"><span data-stu-id="81b68-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="81b68-120">考えられる値については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81b68-120">See the [Remarks] section for possible values.</span></span>

## <a name="return-value"></a><span data-ttu-id="81b68-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="81b68-121">Return value</span></span>

<span data-ttu-id="81b68-122">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="81b68-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="81b68-123">定数</span><span class="sxs-lookup"><span data-stu-id="81b68-123">Constant</span></span>  |<span data-ttu-id="81b68-124">[値]</span><span class="sxs-lookup"><span data-stu-id="81b68-124">Value</span></span>  |<span data-ttu-id="81b68-125">説明</span><span class="sxs-lookup"><span data-stu-id="81b68-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="81b68-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="81b68-126">0x80041001</span></span> | <span data-ttu-id="81b68-127">一般エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="81b68-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="81b68-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="81b68-128">0x80041008</span></span> | <span data-ttu-id="81b68-129">パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="81b68-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="81b68-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="81b68-130">0x8004101d</span></span> | <span data-ttu-id="81b68-131">[`BeginEnumeration`](beginenumeration.md) 関数の呼び出しがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="81b68-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="81b68-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="81b68-132">0x80041006</span></span> | <span data-ttu-id="81b68-133">新しい列挙を開始するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="81b68-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="81b68-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="81b68-134">0x80041015</span></span> | <span data-ttu-id="81b68-135">現在のプロセスと Windows 管理間のリモート プロシージャ コールが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="81b68-135">The remote procedure call between the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="81b68-136">0</span><span class="sxs-lookup"><span data-stu-id="81b68-136">0</span></span> | <span data-ttu-id="81b68-137">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="81b68-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="81b68-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="81b68-138">0x40005</span></span> | <span data-ttu-id="81b68-139">列挙にはこれ以上プロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="81b68-139">There are no more properties in the enumeration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="81b68-140">解説</span><span class="sxs-lookup"><span data-stu-id="81b68-140">Remarks</span></span>

<span data-ttu-id="81b68-141">この関数では、[IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="81b68-141">This function wraps a call to the [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) method.</span></span>

<span data-ttu-id="81b68-142">このメソッドからは、システム プロパティも返されます。</span><span class="sxs-lookup"><span data-stu-id="81b68-142">This method also returns system properties.</span></span>

<span data-ttu-id="81b68-143">プロパティの基になる型がオブジェクト パス、日付か時刻、または別の特殊な型である場合、戻り値の型には十分な情報が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="81b68-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="81b68-144">呼び出し元では、プロパティがオブジェクト参照、日付か時刻、または別の特殊な型であるかどうかを判断するために、指定されたプロパティの `CIMTYPE` を調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="81b68-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="81b68-145">`plFlavor` が `null` でない場合、`LONG` の値は、次のように、プロパティの発生元に関する情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="81b68-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="81b68-146">定数</span><span class="sxs-lookup"><span data-stu-id="81b68-146">Constant</span></span>  |<span data-ttu-id="81b68-147">[値]</span><span class="sxs-lookup"><span data-stu-id="81b68-147">Value</span></span>  |<span data-ttu-id="81b68-148">説明</span><span class="sxs-lookup"><span data-stu-id="81b68-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="81b68-149">0x40</span><span class="sxs-lookup"><span data-stu-id="81b68-149">0x40</span></span> | <span data-ttu-id="81b68-150">プロパティは、標準のシステム プロパティです。</span><span class="sxs-lookup"><span data-stu-id="81b68-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="81b68-151">0x20</span><span class="sxs-lookup"><span data-stu-id="81b68-151">0x20</span></span> | <span data-ttu-id="81b68-152">クラスの場合: プロパティは親クラスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="81b68-152">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="81b68-153">インスタンスの場合: プロパティは親クラスから継承されましたが、インスタンスによって変更されていません。</span><span class="sxs-lookup"><span data-stu-id="81b68-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="81b68-154">0</span><span class="sxs-lookup"><span data-stu-id="81b68-154">0</span></span> | <span data-ttu-id="81b68-155">クラスの場合: プロパティは派生クラスに属します。</span><span class="sxs-lookup"><span data-stu-id="81b68-155">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="81b68-156">インスタンスの場合: プロパティは、インスタンスによって変更されています。つまり、値が指定されたか、修飾子が追加または変更されました。</span><span class="sxs-lookup"><span data-stu-id="81b68-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="81b68-157">必要条件</span><span class="sxs-lookup"><span data-stu-id="81b68-157">Requirements</span></span>

<span data-ttu-id="81b68-158">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81b68-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="81b68-159">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="81b68-159">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="81b68-160">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="81b68-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="81b68-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="81b68-161">See also</span></span>

- [<span data-ttu-id="81b68-162">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="81b68-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
