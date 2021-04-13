---
title: CloneEnumWbemClassObject 関数 (アンマネージド API リファレンス)
description: CloneEnumWbemClassObject 関数では、列挙子の論理コピーが作成されます。
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fa8a7f436c018e3e083be452d300eb21e17f93f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708128"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="c6e76-103">CloneEnumWbemClassObject 関数</span><span class="sxs-lookup"><span data-stu-id="c6e76-103">CloneEnumWbemClassObject function</span></span>

<span data-ttu-id="c6e76-104">列挙型内での位置を維持して、列挙子の論理コピーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c6e76-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="c6e76-105">構文</span><span class="sxs-lookup"><span data-stu-id="c6e76-105">Syntax</span></span>

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum,
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject,
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority
);
```

## <a name="parameters"></a><span data-ttu-id="c6e76-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c6e76-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="c6e76-107">[out] 新しい [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) へのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c6e76-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="c6e76-108">[in] 承認レベル。</span><span class="sxs-lookup"><span data-stu-id="c6e76-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="c6e76-109">[in] 偽装レベル。</span><span class="sxs-lookup"><span data-stu-id="c6e76-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="c6e76-110">[out] 複製する [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c6e76-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="c6e76-111">[in] ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="c6e76-111">[in] The user name.</span></span> <span data-ttu-id="c6e76-112">詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6e76-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="c6e76-113">[in] パスワード。</span><span class="sxs-lookup"><span data-stu-id="c6e76-113">[in] The password.</span></span> <span data-ttu-id="c6e76-114">詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6e76-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="c6e76-115">[in] ユーザーのドメイン名。</span><span class="sxs-lookup"><span data-stu-id="c6e76-115">[in] The domain name of the user.</span></span> <span data-ttu-id="c6e76-116">詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6e76-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="c6e76-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="c6e76-117">Return value</span></span>

<span data-ttu-id="c6e76-118">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="c6e76-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c6e76-119">定数</span><span class="sxs-lookup"><span data-stu-id="c6e76-119">Constant</span></span>  |<span data-ttu-id="c6e76-120">[値]</span><span class="sxs-lookup"><span data-stu-id="c6e76-120">Value</span></span>  |<span data-ttu-id="c6e76-121">説明</span><span class="sxs-lookup"><span data-stu-id="c6e76-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="c6e76-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="c6e76-122">0x80041001</span></span> | <span data-ttu-id="c6e76-123">一般エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c6e76-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c6e76-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c6e76-124">0x80041008</span></span> | <span data-ttu-id="c6e76-125">パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="c6e76-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c6e76-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c6e76-126">0x80041006</span></span> | <span data-ttu-id="c6e76-127">メモリ不足のため、操作を完了できません。</span><span class="sxs-lookup"><span data-stu-id="c6e76-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="c6e76-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="c6e76-128">0x80041015</span></span> | <span data-ttu-id="c6e76-129">現在のプロセスと WMI の間のリモート プロシージャ コール (RPC) リンクが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="c6e76-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="c6e76-130">0</span><span class="sxs-lookup"><span data-stu-id="c6e76-130">0</span></span> | <span data-ttu-id="c6e76-131">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="c6e76-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="c6e76-132">解説</span><span class="sxs-lookup"><span data-stu-id="c6e76-132">Remarks</span></span>

<span data-ttu-id="c6e76-133">この関数では、[IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="c6e76-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="c6e76-134">このメソッドでは、"ベスト エフォート" コピーだけが行われます。</span><span class="sxs-lookup"><span data-stu-id="c6e76-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="c6e76-135">多くの CIM オブジェクトは動的な性質を持つため、新しい列挙子ではソース列挙子と同じオブジェクトのセットが列挙されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c6e76-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="c6e76-136">関数呼び出しが失敗した場合は、[GetErrorInfo](geterrorinfo.md) 関数を呼び出して追加のエラー情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="c6e76-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="c6e76-137">例</span><span class="sxs-lookup"><span data-stu-id="c6e76-137">Example</span></span>

<span data-ttu-id="c6e76-138">例については、「[IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) メソッド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6e76-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c6e76-139">必要条件</span><span class="sxs-lookup"><span data-stu-id="c6e76-139">Requirements</span></span>

 <span data-ttu-id="c6e76-140">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6e76-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="c6e76-141">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c6e76-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="c6e76-142">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c6e76-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c6e76-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6e76-143">See also</span></span>

- [<span data-ttu-id="c6e76-144">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c6e76-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
