---
title: QualifierSet_Delete 関数 (アンマネージド API リファレンス)
description: QualifierSet_Delete 関数では、名前で指定した修飾子が削除されます。
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2000de77903c3dabb43116fa1700b4ed393aeb5a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721154"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="87d5a-103">QualifierSet_Delete 関数</span><span class="sxs-lookup"><span data-stu-id="87d5a-103">QualifierSet_Delete function</span></span>

<span data-ttu-id="87d5a-104">名前によって指定した修飾子が削除されます。</span><span class="sxs-lookup"><span data-stu-id="87d5a-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="87d5a-105">構文</span><span class="sxs-lookup"><span data-stu-id="87d5a-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="87d5a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87d5a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="87d5a-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="87d5a-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="87d5a-108">`ptr` [in] [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="87d5a-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="87d5a-109">`wszName` [in] 削除する修飾子の名前。</span><span class="sxs-lookup"><span data-stu-id="87d5a-109">`wszName` [in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="87d5a-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="87d5a-110">Return value</span></span>

<span data-ttu-id="87d5a-111">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="87d5a-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="87d5a-112">定数</span><span class="sxs-lookup"><span data-stu-id="87d5a-112">Constant</span></span>  |<span data-ttu-id="87d5a-113">[値]</span><span class="sxs-lookup"><span data-stu-id="87d5a-113">Value</span></span>  |<span data-ttu-id="87d5a-114">説明</span><span class="sxs-lookup"><span data-stu-id="87d5a-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="87d5a-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="87d5a-115">0x80041008</span></span> | <span data-ttu-id="87d5a-116">`wszName` パラメーターが有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="87d5a-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="87d5a-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="87d5a-117">0x80041016</span></span> | <span data-ttu-id="87d5a-118">この修飾子の削除は無効です。</span><span class="sxs-lookup"><span data-stu-id="87d5a-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="87d5a-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="87d5a-119">0x80041002</span></span> | <span data-ttu-id="87d5a-120">指定した修飾子が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="87d5a-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="87d5a-121">0</span><span class="sxs-lookup"><span data-stu-id="87d5a-121">0</span></span> | <span data-ttu-id="87d5a-122">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="87d5a-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="87d5a-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="87d5a-123">0x40002</span></span> | <span data-ttu-id="87d5a-124">ローカル オーバーライドが削除され、親オブジェクトからの元の修飾子のスコープが再開されました。</span><span class="sxs-lookup"><span data-stu-id="87d5a-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="87d5a-125">解説</span><span class="sxs-lookup"><span data-stu-id="87d5a-125">Remarks</span></span>

<span data-ttu-id="87d5a-126">この関数では、[IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="87d5a-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="87d5a-127">修飾子の伝達規則により、特定の修飾子が別のオブジェクトから継承され、現在のクラスまたはインスタンス内で単にオーバーライドされている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="87d5a-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="87d5a-128">この場合、`QualifierSet_Delete` メソッドによって、修飾子が元の継承された値にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="87d5a-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="87d5a-129">この場合、関数では状態コード `WBEM_S_RESET_TO_DEFAULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="87d5a-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="87d5a-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="87d5a-130">Requirements</span></span>  

 <span data-ttu-id="87d5a-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87d5a-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d5a-132">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="87d5a-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="87d5a-133">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="87d5a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d5a-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="87d5a-134">See also</span></span>

- [<span data-ttu-id="87d5a-135">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="87d5a-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
