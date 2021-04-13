---
title: SpawnDerivedClass 関数 (アンマネージド API リファレンス)
description: SpawnDerivedClass 関数では、オブジェクトから派生する新しいオブジェクトが作成されます。
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 8020dd851b6773e6c76c53892c4b2bc21e4261bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716513"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="445cc-103">SpawnDerivedClass 関数</span><span class="sxs-lookup"><span data-stu-id="445cc-103">SpawnDerivedClass function</span></span>

<span data-ttu-id="445cc-104">指定したオブジェクトから新たに派生するクラス オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="445cc-104">Creates a newly derived class object from a specified object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="445cc-105">構文</span><span class="sxs-lookup"><span data-stu-id="445cc-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a><span data-ttu-id="445cc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="445cc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="445cc-107">[in] このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="445cc-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="445cc-108">[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="445cc-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="445cc-109">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="445cc-109">[in] Reserved.</span></span> <span data-ttu-id="445cc-110">このパラメーターは、0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="445cc-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="445cc-111">[out] 新しいクラス定義オブジェクトへのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="445cc-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="445cc-112">エラーが発生した場合、新しいオブジェクトは返されず、`ppNewClass` は未変更のままになります。</span><span class="sxs-lookup"><span data-stu-id="445cc-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="445cc-113">この値を `null` にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="445cc-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="445cc-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="445cc-114">Return value</span></span>

<span data-ttu-id="445cc-115">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="445cc-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="445cc-116">定数</span><span class="sxs-lookup"><span data-stu-id="445cc-116">Constant</span></span>  |<span data-ttu-id="445cc-117">[値]</span><span class="sxs-lookup"><span data-stu-id="445cc-117">Value</span></span>  |<span data-ttu-id="445cc-118">説明</span><span class="sxs-lookup"><span data-stu-id="445cc-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="445cc-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="445cc-119">0x80041001</span></span> | <span data-ttu-id="445cc-120">一般エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="445cc-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="445cc-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="445cc-121">0x80041016</span></span> | <span data-ttu-id="445cc-122">無効な操作 (例: インスタンスからクラスを生成する) が要求されました。</span><span class="sxs-lookup"><span data-stu-id="445cc-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="445cc-123">ソース クラスが完全に定義されていないか、Windows 管理に登録されていないため、新しい派生クラスは許可されません。</span><span class="sxs-lookup"><span data-stu-id="445cc-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="445cc-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="445cc-124">0x80041006</span></span> | <span data-ttu-id="445cc-125">メモリ不足のため、操作を完了できません。</span><span class="sxs-lookup"><span data-stu-id="445cc-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="445cc-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="445cc-126">0x80041008</span></span> | <span data-ttu-id="445cc-127">`ppNewClass` が `null`です。</span><span class="sxs-lookup"><span data-stu-id="445cc-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="445cc-128">0</span><span class="sxs-lookup"><span data-stu-id="445cc-128">0</span></span> | <span data-ttu-id="445cc-129">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="445cc-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="445cc-130">解説</span><span class="sxs-lookup"><span data-stu-id="445cc-130">Remarks</span></span>

<span data-ttu-id="445cc-131">この関数では、[IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="445cc-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="445cc-132">`ptr` は、生成されたオブジェクトの親クラスになるクラス定義である必要があります。</span><span class="sxs-lookup"><span data-stu-id="445cc-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="445cc-133">返されたオブジェクトは、現在のオブジェクトのサブクラスになります。</span><span class="sxs-lookup"><span data-stu-id="445cc-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="445cc-134">`ppNewClass` で返された新しいオブジェクトは、自動的に現在のオブジェクトのサブクラスになります。</span><span class="sxs-lookup"><span data-stu-id="445cc-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="445cc-135">この動作はオーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="445cc-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="445cc-136">サブクラス (派生クラス) を作成する方法は他にありません。</span><span class="sxs-lookup"><span data-stu-id="445cc-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="445cc-137">必要条件</span><span class="sxs-lookup"><span data-stu-id="445cc-137">Requirements</span></span>  

 <span data-ttu-id="445cc-138">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="445cc-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="445cc-139">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="445cc-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="445cc-140">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="445cc-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="445cc-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="445cc-141">See also</span></span>

- [<span data-ttu-id="445cc-142">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="445cc-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
