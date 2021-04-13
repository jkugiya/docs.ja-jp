---
title: PutMethod 関数 (アンマネージド API リファレンス)
description: PutMethod 関数ではメソッドが作成されます。
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 8edbb8074573b98c017f98197d370c2ad37db80c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726757"
---
# <a name="putmethod-function"></a><span data-ttu-id="d56b2-103">PutMethod 関数</span><span class="sxs-lookup"><span data-stu-id="d56b2-103">PutMethod function</span></span>

<span data-ttu-id="d56b2-104">メソッドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d56b2-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="d56b2-105">構文</span><span class="sxs-lookup"><span data-stu-id="d56b2-105">Syntax</span></span>  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*  ptr,
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
);
```  

## <a name="parameters"></a><span data-ttu-id="d56b2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d56b2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d56b2-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="d56b2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d56b2-108">[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d56b2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="d56b2-109">[in] 作成するメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="d56b2-109">[in] The name of the method to create.</span></span>

`lFlags`  
<span data-ttu-id="d56b2-110">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="d56b2-110">[in] Reserved.</span></span> <span data-ttu-id="d56b2-111">このパラメーターは、0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d56b2-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="d56b2-112">[in] メソッドの `in` パラメーターを格納している [__Parameters システム クラス](/windows/desktop/WmiSdk/--parameters)のコピーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d56b2-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="d56b2-113">`null` に設定されている場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="d56b2-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="d56b2-114">[in] メソッドの `out` パラメーターを格納している [__Parameters システム クラス](/windows/desktop/WmiSdk/--parameters)のコピーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d56b2-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="d56b2-115">`null` に設定されている場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="d56b2-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d56b2-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="d56b2-116">Return value</span></span>

<span data-ttu-id="d56b2-117">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="d56b2-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d56b2-118">定数</span><span class="sxs-lookup"><span data-stu-id="d56b2-118">Constant</span></span>  |<span data-ttu-id="d56b2-119">[値]</span><span class="sxs-lookup"><span data-stu-id="d56b2-119">Value</span></span>  |<span data-ttu-id="d56b2-120">説明</span><span class="sxs-lookup"><span data-stu-id="d56b2-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d56b2-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d56b2-121">0x80041008</span></span> | <span data-ttu-id="d56b2-122">1 つ以上のパラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="d56b2-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="d56b2-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="d56b2-123">0x80041043</span></span> | <span data-ttu-id="d56b2-124">*pInSignature* と *pOutSignature* の両方のオブジェクトで指定された `[in, out]` メソッド パラメーターの修飾子が異なります。</span><span class="sxs-lookup"><span data-stu-id="d56b2-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="d56b2-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="d56b2-125">0x80041036</span></span> | <span data-ttu-id="d56b2-126">メソッド パラメーターに **ID** 修飾子の指定がありません。</span><span class="sxs-lookup"><span data-stu-id="d56b2-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="d56b2-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="d56b2-127">0x80041038</span></span> | <span data-ttu-id="d56b2-128">メソッドのパラメーターに割り当てられている ID 系列が連続していないか、0 から始まっていません。</span><span class="sxs-lookup"><span data-stu-id="d56b2-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="d56b2-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="d56b2-129">0x80041039</span></span> | <span data-ttu-id="d56b2-130">メソッドの戻り値に **ID** 修飾子があります。</span><span class="sxs-lookup"><span data-stu-id="d56b2-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="d56b2-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="d56b2-131">0x80041034</span></span> | <span data-ttu-id="d56b2-132">親クラスから既存のメソッド名を再使用しようとしました。また、シグネチャは一致しませんでした。</span><span class="sxs-lookup"><span data-stu-id="d56b2-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="d56b2-133">0</span><span class="sxs-lookup"><span data-stu-id="d56b2-133">0</span></span> | <span data-ttu-id="d56b2-134">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="d56b2-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d56b2-135">解説</span><span class="sxs-lookup"><span data-stu-id="d56b2-135">Remarks</span></span>

<span data-ttu-id="d56b2-136">この関数では、[IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="d56b2-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="d56b2-137">このメソッド呼び出しは、`ptr` が CIM クラス定義の場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d56b2-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="d56b2-138">CIM インスタンスを指す [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ポインターからは、メソッド操作を使用できません。</span><span class="sxs-lookup"><span data-stu-id="d56b2-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="d56b2-139">ユーザーは、アンダースコアで開始または終了する名前を持つメソッドを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="d56b2-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="d56b2-140">これは、システム クラスおよびプロパティ用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="d56b2-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="d56b2-141">メソッドの場合、`in` および `out` パラメーターは [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) オブジェクトのプロパティとして記述されます。</span><span class="sxs-lookup"><span data-stu-id="d56b2-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="d56b2-142">`[in/out]` パラメーターを定義するには、`pInSignature` および `pOutSignature` パラメーターが指す両方のオブジェクトに同じプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="d56b2-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="d56b2-143">この場合、プロパティは同じ **ID** 修飾子値を共有します。</span><span class="sxs-lookup"><span data-stu-id="d56b2-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="d56b2-144">`ReturnValue` 以外の [__Parameters](/windows/desktop/WmiSdk/--parameters) クラス オブジェクトの各プロパティには **ID** 修飾子が必要です。これは、パラメーターが表示される順序を示す 0 から始まる数値です。</span><span class="sxs-lookup"><span data-stu-id="d56b2-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="d56b2-145">2 つのパラメーターの **ID** 値を同じにすることはできません。また、**ID** 値をスキップすることもできません。</span><span class="sxs-lookup"><span data-stu-id="d56b2-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="d56b2-146">どちらかの条件が発生した場合は、`PutMethod` 関数から `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` が返されます。</span><span class="sxs-lookup"><span data-stu-id="d56b2-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="d56b2-147">例</span><span class="sxs-lookup"><span data-stu-id="d56b2-147">Example</span></span>

<span data-ttu-id="d56b2-148">例については、「[IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) メソッド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d56b2-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d56b2-149">必要条件</span><span class="sxs-lookup"><span data-stu-id="d56b2-149">Requirements</span></span>  

 <span data-ttu-id="d56b2-150">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d56b2-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d56b2-151">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d56b2-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d56b2-152">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d56b2-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d56b2-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="d56b2-153">See also</span></span>

- [<span data-ttu-id="d56b2-154">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d56b2-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
