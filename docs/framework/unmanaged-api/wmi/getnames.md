---
title: GetNames 関数 (アンマネージド API リファレンス)
description: GetNames 関数では、オブジェクトのプロパティの名前が取得されます。
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd889158e61b86f42d88bcf86eda7d816277e6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687659"
---
# <a name="getnames-function"></a><span data-ttu-id="43dca-103">GetNames 関数</span><span class="sxs-lookup"><span data-stu-id="43dca-103">GetNames function</span></span>

<span data-ttu-id="43dca-104">オブジェクトのプロパティの名前の一部またはすべてが取得されます。</span><span class="sxs-lookup"><span data-stu-id="43dca-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="43dca-105">構文</span><span class="sxs-lookup"><span data-stu-id="43dca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
);
```  

## <a name="parameters"></a><span data-ttu-id="43dca-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="43dca-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="43dca-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="43dca-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="43dca-108">[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="43dca-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="43dca-109">[in] フィルターの一部として動作する修飾子名を指定する有効な `LPCWSTR` へのポインター。</span><span class="sxs-lookup"><span data-stu-id="43dca-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="43dca-110">詳細については、「[解説](#remarks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43dca-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="43dca-111">このパラメーターは、`null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="43dca-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="43dca-112">[in] ビット フィールドの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="43dca-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="43dca-113">詳細については、「[解説](#remarks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43dca-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="43dca-114">`pQualifierValue` [in] フィルター値に初期化される有効な `VARIANT` 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="43dca-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="43dca-115">このパラメーターは、`null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="43dca-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="43dca-116">[out] プロパティ名を格納している `SAFEARRAY` 構造体。</span><span class="sxs-lookup"><span data-stu-id="43dca-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="43dca-117">入力時には、このパラメーターは常に `null` へのポインターである必要があります。</span><span class="sxs-lookup"><span data-stu-id="43dca-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="43dca-118">詳細については、「[解説](#remarks)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="43dca-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="43dca-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="43dca-119">Return value</span></span>

<span data-ttu-id="43dca-120">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="43dca-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="43dca-121">定数</span><span class="sxs-lookup"><span data-stu-id="43dca-121">Constant</span></span>  |<span data-ttu-id="43dca-122">[値]</span><span class="sxs-lookup"><span data-stu-id="43dca-122">Value</span></span>  |<span data-ttu-id="43dca-123">説明</span><span class="sxs-lookup"><span data-stu-id="43dca-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="43dca-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="43dca-124">0x80041001</span></span> | <span data-ttu-id="43dca-125">一般エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="43dca-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="43dca-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="43dca-126">0x80041008</span></span> | <span data-ttu-id="43dca-127">1 つ以上のパラメーターが無効であるか、指定したフラグとパラメーターの組み合わせが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="43dca-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="43dca-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="43dca-128">0x80041006</span></span> | <span data-ttu-id="43dca-129">メモリ不足のため、操作を完了できません。</span><span class="sxs-lookup"><span data-stu-id="43dca-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="43dca-130">0</span><span class="sxs-lookup"><span data-stu-id="43dca-130">0</span></span> | <span data-ttu-id="43dca-131">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="43dca-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="43dca-132">解説</span><span class="sxs-lookup"><span data-stu-id="43dca-132">Remarks</span></span>

<span data-ttu-id="43dca-133">この関数では、[IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="43dca-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="43dca-134">返される名前は、フラグとパラメーターの組み合わせによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="43dca-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="43dca-135">たとえば、関数では、すべてのプロパティの名前、またはキー プロパティの名前のみを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="43dca-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="43dca-136">プライマリ フィルターは `lFlags` パラメーターで指定され、その他のパラメーターはそれに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="43dca-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="43dca-137">`lFlags` 内のフラグ値はビット フィールドです</span><span class="sxs-lookup"><span data-stu-id="43dca-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="43dca-138">`lEnumFlags` 引数として渡すことができるフラグは、*WbemCli.h* ヘッダー ファイル内で定義されているか、コード内で定数として定義することができるビット フィールドです。</span><span class="sxs-lookup"><span data-stu-id="43dca-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="43dca-139">各グループのフラグを他のグループの任意のフラグと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="43dca-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="43dca-140">ただし、同じグループのフラグは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="43dca-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="43dca-141">グループ 1 フラグ</span><span class="sxs-lookup"><span data-stu-id="43dca-141">Group 1 flags</span></span> |<span data-ttu-id="43dca-142">[値]</span><span class="sxs-lookup"><span data-stu-id="43dca-142">Value</span></span>  |<span data-ttu-id="43dca-143">説明</span><span class="sxs-lookup"><span data-stu-id="43dca-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="43dca-144">0</span><span class="sxs-lookup"><span data-stu-id="43dca-144">0</span></span> | <span data-ttu-id="43dca-145">すべてのプロパティ名を返します。</span><span class="sxs-lookup"><span data-stu-id="43dca-145">Return all property names.</span></span> <span data-ttu-id="43dca-146">`strQualifierName` と `pQualifierVal` は使用されません。</span><span class="sxs-lookup"><span data-stu-id="43dca-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="43dca-147">1</span><span class="sxs-lookup"><span data-stu-id="43dca-147">1</span></span> | <span data-ttu-id="43dca-148">`strQualifierName` パラメーターで指定された名前の修飾子を持つプロパティのみを返します。</span><span class="sxs-lookup"><span data-stu-id="43dca-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="43dca-149">このフラグを使用する場合は、`strQualifierName` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43dca-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="43dca-150">2</span><span class="sxs-lookup"><span data-stu-id="43dca-150">2</span></span> |  <span data-ttu-id="43dca-151">`strQualifierName` パラメーターで指定された名前の修飾子を持たないプロパティのみを返します。</span><span class="sxs-lookup"><span data-stu-id="43dca-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="43dca-152">このフラグを使用する場合は、`strQualifierName` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43dca-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="43dca-153">3</span><span class="sxs-lookup"><span data-stu-id="43dca-153">3</span></span> | <span data-ttu-id="43dca-154">`wszQualifierName` パラメーターで指定された名前の修飾子を持ち、`pQualifierVal` 構造体で指定されたものと同じ値も持つプロパティのみを返します。</span><span class="sxs-lookup"><span data-stu-id="43dca-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="43dca-155">このフラグを使用する場合は、`wszQualifierName` と `pQualifierValue` の両方を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43dca-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="43dca-156">グループ 2 フラグ</span><span class="sxs-lookup"><span data-stu-id="43dca-156">Group 2 flags</span></span> |<span data-ttu-id="43dca-157">[値]</span><span class="sxs-lookup"><span data-stu-id="43dca-157">Value</span></span>  |<span data-ttu-id="43dca-158">説明</span><span class="sxs-lookup"><span data-stu-id="43dca-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="43dca-159">0x4</span><span class="sxs-lookup"><span data-stu-id="43dca-159">0x4</span></span> | <span data-ttu-id="43dca-160">キーを定義するプロパティの名前だけを返します。</span><span class="sxs-lookup"><span data-stu-id="43dca-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="43dca-161">0x8</span><span class="sxs-lookup"><span data-stu-id="43dca-161">0x8</span></span> | <span data-ttu-id="43dca-162">オブジェクト参照であるプロパティ名だけを返します。</span><span class="sxs-lookup"><span data-stu-id="43dca-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="43dca-163">グループ 3 フラグ</span><span class="sxs-lookup"><span data-stu-id="43dca-163">Group 3 flags</span></span> |<span data-ttu-id="43dca-164">[値]</span><span class="sxs-lookup"><span data-stu-id="43dca-164">Value</span></span>  |<span data-ttu-id="43dca-165">説明</span><span class="sxs-lookup"><span data-stu-id="43dca-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="43dca-166">0x10</span><span class="sxs-lookup"><span data-stu-id="43dca-166">0x10</span></span> | <span data-ttu-id="43dca-167">最派生クラスに属しているプロパティ名だけを返します。</span><span class="sxs-lookup"><span data-stu-id="43dca-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="43dca-168">親クラスからのプロパティは除外します。</span><span class="sxs-lookup"><span data-stu-id="43dca-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="43dca-169">0x20</span><span class="sxs-lookup"><span data-stu-id="43dca-169">0x20</span></span> | <span data-ttu-id="43dca-170">親クラスに属しているプロパティ名だけを返します。</span><span class="sxs-lookup"><span data-stu-id="43dca-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="43dca-171">0x30</span><span class="sxs-lookup"><span data-stu-id="43dca-171">0x30</span></span> | <span data-ttu-id="43dca-172">システム プロパティの名前だけを返します。</span><span class="sxs-lookup"><span data-stu-id="43dca-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="43dca-173">0x40</span><span class="sxs-lookup"><span data-stu-id="43dca-173">0x40</span></span> | <span data-ttu-id="43dca-174">システム以外のプロパティの名前だけを返します。</span><span class="sxs-lookup"><span data-stu-id="43dca-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="43dca-175">この関数では、`WBEM_S_NO_ERROR` を返す場合には常に新しい `SAFEARRAY` が割り当てられ、`pstrNames` は常にそれを指すように設定されます。</span><span class="sxs-lookup"><span data-stu-id="43dca-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="43dca-176">指定したフィルターに一致するプロパティがない場合、返される配列には 0 個の要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="43dca-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="43dca-177">関数によって `WBM_S_NO_ERROR` 以外の値が返される場合、新しい `SAFEARRAY` 構造体は返されません。</span><span class="sxs-lookup"><span data-stu-id="43dca-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="43dca-178">必要条件</span><span class="sxs-lookup"><span data-stu-id="43dca-178">Requirements</span></span>  

 <span data-ttu-id="43dca-179">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43dca-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43dca-180">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="43dca-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="43dca-181">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="43dca-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43dca-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="43dca-182">See also</span></span>

- [<span data-ttu-id="43dca-183">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="43dca-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
