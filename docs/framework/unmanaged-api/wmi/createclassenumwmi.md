---
title: CreateClassEnumWmi 関数 (アンマネージド API リファレンス)
description: CreateClassEnumWmi 関数では、指定した条件を満たすすべてのクラスの列挙子が返されます。
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b80954e288f6720c75d0af0b8af083fa4856754
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719737"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="56b69-103">CreateClassEnumWmi 関数</span><span class="sxs-lookup"><span data-stu-id="56b69-103">CreateClassEnumWmi function</span></span>

<span data-ttu-id="56b69-104">指定した選択条件を満たしたすべてのクラスに対する列挙子が返されます。</span><span class="sxs-lookup"><span data-stu-id="56b69-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="56b69-105">構文</span><span class="sxs-lookup"><span data-stu-id="56b69-105">Syntax</span></span>

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a><span data-ttu-id="56b69-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="56b69-106">Parameters</span></span>

`strSuperclass`\
<span data-ttu-id="56b69-107">[in] `null` または空白以外の場合は、親クラスの名前。列挙子では、このクラスのサブクラスのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="56b69-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="56b69-108">これが `null` または空白で、`lFlags` が WBEM_FLAG_SHALLOW の場合は、最上位のクラス (親クラスを持たないクラス) のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="56b69-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="56b69-109">これが `null` または空白で、`lFlags` が `WBEM_FLAG_DEEP` の場合は、名前空間内のすべてのクラスが返されます。</span><span class="sxs-lookup"><span data-stu-id="56b69-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`\
<span data-ttu-id="56b69-110">[in] この関数の動作に影響を与えるフラグの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="56b69-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="56b69-111">次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="56b69-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="56b69-112">定数</span><span class="sxs-lookup"><span data-stu-id="56b69-112">Constant</span></span>  |<span data-ttu-id="56b69-113">[値]</span><span class="sxs-lookup"><span data-stu-id="56b69-113">Value</span></span>  |<span data-ttu-id="56b69-114">説明</span><span class="sxs-lookup"><span data-stu-id="56b69-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="56b69-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="56b69-115">0x20000</span></span> | <span data-ttu-id="56b69-116">設定すると、関数により、現在の接続のロケールのローカライズされた名前空間に格納されている修正された修飾子が取得されます。</span><span class="sxs-lookup"><span data-stu-id="56b69-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="56b69-117">設定されていない場合、関数では、直近の名前空間に格納されている修飾子だけが取得されます。</span><span class="sxs-lookup"><span data-stu-id="56b69-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="56b69-118">0</span><span class="sxs-lookup"><span data-stu-id="56b69-118">0</span></span> | <span data-ttu-id="56b69-119">列挙には、このクラスを除く階層内のすべてのサブクラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="56b69-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="56b69-120">1</span><span class="sxs-lookup"><span data-stu-id="56b69-120">1</span></span> | <span data-ttu-id="56b69-121">列挙には、このクラスの純粋なインスタンスだけが含まれ、このクラス内に見つからないプロパティを指定するサブクラスのインスタンスはすべて除外されます。</span><span class="sxs-lookup"><span data-stu-id="56b69-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="56b69-122">0x10</span><span class="sxs-lookup"><span data-stu-id="56b69-122">0x10</span></span> | <span data-ttu-id="56b69-123">このフラグにより、半同期呼び出しが発生します。</span><span class="sxs-lookup"><span data-stu-id="56b69-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="56b69-124">0x20</span><span class="sxs-lookup"><span data-stu-id="56b69-124">0x20</span></span> | <span data-ttu-id="56b69-125">関数によって順方向専用の列挙子が返されます。</span><span class="sxs-lookup"><span data-stu-id="56b69-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="56b69-126">通常、順方向専用の列挙子は、従来の列挙子よりも高速で、使用されるメモリが少なくなりますが、[Clone](clone.md) の呼び出しは許可されません。</span><span class="sxs-lookup"><span data-stu-id="56b69-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="56b69-127">0</span><span class="sxs-lookup"><span data-stu-id="56b69-127">0</span></span> | <span data-ttu-id="56b69-128">WMI では、列挙内のオブジェクトが解放されるまで、それらに対するポインターが保持されます。</span><span class="sxs-lookup"><span data-stu-id="56b69-128">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="56b69-129">最適なパフォーマンスを得るために推奨されるフラグは `WBEM_FLAG_RETURN_IMMEDIATELY` と `WBEM_FLAG_FORWARD_ONLY` です。</span><span class="sxs-lookup"><span data-stu-id="56b69-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="56b69-130">[in] 通常、この値は `null` です。</span><span class="sxs-lookup"><span data-stu-id="56b69-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="56b69-131">それ以外の場合は、要求されたクラスを提供しているプロバイダーが使用できる [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) インスタンスへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="56b69-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="56b69-132">[out] 列挙子へのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="56b69-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="56b69-133">[in] 承認レベル。</span><span class="sxs-lookup"><span data-stu-id="56b69-133">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="56b69-134">[in] 偽装レベル。</span><span class="sxs-lookup"><span data-stu-id="56b69-134">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="56b69-135">[in] 現在の名前空間を表す [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="56b69-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="56b69-136">[in] ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="56b69-136">[in] The user name.</span></span> <span data-ttu-id="56b69-137">詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56b69-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="56b69-138">[in] パスワード。</span><span class="sxs-lookup"><span data-stu-id="56b69-138">[in] The password.</span></span> <span data-ttu-id="56b69-139">詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56b69-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="56b69-140">[in] ユーザーのドメイン名。</span><span class="sxs-lookup"><span data-stu-id="56b69-140">[in] The domain name of the user.</span></span> <span data-ttu-id="56b69-141">詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56b69-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="56b69-142">戻り値</span><span class="sxs-lookup"><span data-stu-id="56b69-142">Return value</span></span>

<span data-ttu-id="56b69-143">この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="56b69-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="56b69-144">定数</span><span class="sxs-lookup"><span data-stu-id="56b69-144">Constant</span></span>  |<span data-ttu-id="56b69-145">[値]</span><span class="sxs-lookup"><span data-stu-id="56b69-145">Value</span></span>  |<span data-ttu-id="56b69-146">説明</span><span class="sxs-lookup"><span data-stu-id="56b69-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="56b69-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="56b69-147">0x80041003</span></span> | <span data-ttu-id="56b69-148">ユーザーに、関数から返される可能性がある 1 つ以上のクラスを表示するアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="56b69-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="56b69-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="56b69-149">0x80041001</span></span> | <span data-ttu-id="56b69-150">特定できないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="56b69-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="56b69-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="56b69-151">0x80041010</span></span> | <span data-ttu-id="56b69-152">`strSuperClass` は存在しません。</span><span class="sxs-lookup"><span data-stu-id="56b69-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="56b69-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="56b69-153">0x80041008</span></span> | <span data-ttu-id="56b69-154">パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="56b69-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="56b69-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="56b69-155">0x80041006</span></span> | <span data-ttu-id="56b69-156">メモリ不足のため、操作を完了できません。</span><span class="sxs-lookup"><span data-stu-id="56b69-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="56b69-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="56b69-157">0x80041033</span></span> | <span data-ttu-id="56b69-158">WMI が停止し、再起動されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="56b69-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="56b69-159">[ConnectServerWmi](connectserverwmi.md) をもう一度呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="56b69-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="56b69-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="56b69-160">0x80041015</span></span> | <span data-ttu-id="56b69-161">現在のプロセスと WMI の間のリモート プロシージャ コール (RPC) リンクが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="56b69-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="56b69-162">0</span><span class="sxs-lookup"><span data-stu-id="56b69-162">0</span></span> | <span data-ttu-id="56b69-163">関数呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="56b69-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="56b69-164">解説</span><span class="sxs-lookup"><span data-stu-id="56b69-164">Remarks</span></span>

<span data-ttu-id="56b69-165">この関数では、[IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) メソッドの呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="56b69-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="56b69-166">関数呼び出しが失敗した場合は、[GetErrorInfo](geterrorinfo.md) 関数を呼び出して追加のエラー情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="56b69-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="56b69-167">必要条件</span><span class="sxs-lookup"><span data-stu-id="56b69-167">Requirements</span></span>

<span data-ttu-id="56b69-168">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56b69-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="56b69-169">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="56b69-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="56b69-170">**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="56b69-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="56b69-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="56b69-171">See also</span></span>

- [<span data-ttu-id="56b69-172">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="56b69-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
