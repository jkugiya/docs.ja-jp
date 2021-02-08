---
description: '詳細について: ICLRMetaHostPolicy:: GetRequestedRuntime メソッド'
title: ICLRMetaHostPolicy::GetRequestedRuntime メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy.GetRequestedRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type:
- apiref
ms.openlocfilehash: 0e11694b0cb66ad7fc28abf7bb9f7fc8c6931a19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789841"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a><span data-ttu-id="bb746-103">ICLRMetaHostPolicy::GetRequestedRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="bb746-103">ICLRMetaHostPolicy::GetRequestedRuntime Method</span></span>

<span data-ttu-id="bb746-104">ホスト ポリシー、マネージド アセンブリ、バージョン文字列、および構成ストリームに基づいて、適切な共通言語ランタイム (CLR) のバージョンへのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="bb746-104">Provides an interface to a preferred version of the common language runtime (CLR) based on a hosting policy, managed assembly, version string, and configuration stream.</span></span> <span data-ttu-id="bb746-105">このメソッドは、実際には CLR の読み込みもアクティブ化も行いませんが、単にポリシー結果を表す [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを返します。</span><span class="sxs-lookup"><span data-stu-id="bb746-105">This method does not actually load or activate the CLR, but simply returns the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents the policy result.</span></span> <span data-ttu-id="bb746-106">このメソッドは、 [Getrequestedruntimeinfo](getrequestedruntimeinfo-function.md)、 [getrequestedruntimeinfo](getrequestedruntimeversion-function.md)、 [corbindtoruntimehost](corbindtoruntimehost-function.md)、 [Corbindtoruntimebycfg](corbindtoruntimebycfg-function.md)、および [getcorrequiredversion](getcorrequiredversion-function.md) メソッドを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bb746-106">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md), and [GetCORRequiredVersion](getcorrequiredversion-function.md) methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb746-107">構文</span><span class="sxs-lookup"><span data-stu-id="bb746-107">Syntax</span></span>

```cpp
HRESULT GetRequestedRuntime(
    [in]  METAHOST_POLICY_FLAGS dwPolicyFlags,
    [in]  LPCWSTR pwzBinary,
    [in]  IStream *pCfgStream,
    [in, out, size_is(*pcchVersion)] LPWSTR pwzVersion,
    [in, out]  DWORD *pcchVersion,
    [out, size_is(*pcchImageVersion)] LPWSTR pwzImageVersion,
    [in, out]  DWORD *pcchImageVersion,
    [out] DWORD *pdwConfigFlags,
    [in]  REFIID  riid
    [out, iid_is(riid), retval] LPVOID *ppRuntime);
```

## <a name="parameters"></a><span data-ttu-id="bb746-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb746-108">Parameters</span></span>

|<span data-ttu-id="bb746-109">名前</span><span class="sxs-lookup"><span data-stu-id="bb746-109">Name</span></span>|<span data-ttu-id="bb746-110">説明</span><span class="sxs-lookup"><span data-stu-id="bb746-110">Description</span></span>|
|----------|-----------------|
|`dwPolicyFlags`|<span data-ttu-id="bb746-111">[in] 必須。</span><span class="sxs-lookup"><span data-stu-id="bb746-111">[in] Required.</span></span> <span data-ttu-id="bb746-112">バインディングポリシーを表す [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) 列挙体のメンバーと、任意の数の修飾子を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb746-112">Specifies a member of the [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration, representing a binding policy, and any number of modifiers.</span></span> <span data-ttu-id="bb746-113">現在使用できるポリシーは [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md)のみです。</span><span class="sxs-lookup"><span data-stu-id="bb746-113">The only policy that is currently available is [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span></span><br /><br /> <span data-ttu-id="bb746-114">修飾子には、 [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md)、 [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md)、 [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md)、 [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)、および [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md)が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb746-114">Modifiers include [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md), and [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span></span>|
|`pwzBinary`|<span data-ttu-id="bb746-115">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="bb746-115">[in] Optional.</span></span> <span data-ttu-id="bb746-116">アセンブリのファイル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb746-116">Specifies the assembly file path.</span></span>|
|`pCfgStream`|<span data-ttu-id="bb746-117">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="bb746-117">[in] Optional.</span></span> <span data-ttu-id="bb746-118">構成ファイルを <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> として指定します。</span><span class="sxs-lookup"><span data-stu-id="bb746-118">Specifies the configuration file as a <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span></span>|
|`pwzVersion`|<span data-ttu-id="bb746-119">[in、out] 省略可能です。</span><span class="sxs-lookup"><span data-stu-id="bb746-119">[in, out] Optional.</span></span> <span data-ttu-id="bb746-120">読み込む適切な CLR のバージョンを指定するか返します。 </span><span class="sxs-lookup"><span data-stu-id="bb746-120">Specifies or returns the preferred CLR version to be loaded.</span></span>|
|`pcchVersion`|<span data-ttu-id="bb746-121">[in、out] 必須です。</span><span class="sxs-lookup"><span data-stu-id="bb746-121">[in, out] Required.</span></span> <span data-ttu-id="bb746-122">バッファー オーバーランを回避するため、入力として必要なサイズの `pwzVersion` を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb746-122">Specifies the expected size of `pwzVersion` as input, to avoid buffer overruns.</span></span> <span data-ttu-id="bb746-123">`pwzVersion` が null の場合、`GetRequestedRuntime` が返されるときに、`pcchVersion` には必要なサイズの `pwzVersion` が含まれて、事前の割り当てが可能になります。それ以外の場合、`pcchVersion` には `pwzVersion` に書き込まれる文字数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb746-123">If `pwzVersion` is null, `pcchVersion` contains the expected size of `pwzVersion` when `GetRequestedRuntime` returns, to allow pre-allocation; otherwise, `pcchVersion` contains the number of characters written to `pwzVersion`.</span></span>|
|`pwzImageVersion`|<span data-ttu-id="bb746-124">[out] 省略可能です。</span><span class="sxs-lookup"><span data-stu-id="bb746-124">[out] Optional.</span></span> <span data-ttu-id="bb746-125">が返されるときに `GetRequestedRuntime` 、返される [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスに対応する CLR バージョンを格納します。</span><span class="sxs-lookup"><span data-stu-id="bb746-125">When `GetRequestedRuntime` returns, contains the CLR version corresponding to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that is returned.</span></span>|
|`pcchImageVersion`|<span data-ttu-id="bb746-126">[in、out] 省略可能です。</span><span class="sxs-lookup"><span data-stu-id="bb746-126">[in, out] Optional.</span></span> <span data-ttu-id="bb746-127">バッファー オーバーランを回避するため、入力として `pwzImageVersion` のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb746-127">Specifies the size of `pwzImageVersion` as input to avoid buffer overruns.</span></span> <span data-ttu-id="bb746-128">`pwzImageVersion` が null の場合、`GetRequestedRuntime` が返されるとき、`pcchImageVersion` には必要なサイズの `pwzImageVersion` が含まれて、事前の割り当てが可能になります。</span><span class="sxs-lookup"><span data-stu-id="bb746-128">If `pwzImageVersion` is null, `pcchImageVersion` contains the required size of `pwzImageVersion` when `GetRequestedRuntime` returns, to allow pre-allocation.</span></span>|
|`pdwConfigFlags`|<span data-ttu-id="bb746-129">[out] 省略可能です。</span><span class="sxs-lookup"><span data-stu-id="bb746-129">[out] Optional.</span></span> <span data-ttu-id="bb746-130">が `GetRequestedRuntime` バインドプロセス中に構成ファイルを使用する場合、が返されるときに、 `pdwConfigFlags` 要素に属性セットがあるかどうか、 [](metahost-config-flags-enumeration.md) [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) `useLegacyV2RuntimeActivationPolicy` および属性の値が含まれているかどうかを示す METAHOST_CONFIG_FLAGS 値を格納します。</span><span class="sxs-lookup"><span data-stu-id="bb746-130">If `GetRequestedRuntime` uses a configuration file during the binding process, when it returns, `pdwConfigFlags` contains a [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) value that indicates whether the [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) element has the `useLegacyV2RuntimeActivationPolicy` attribute set, and the value of the attribute.</span></span> <span data-ttu-id="bb746-131">に関連する値を取得するには、 [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) マスクをに適用し `pdwConfigFlags` `useLegacyV2RuntimeActivationPolicy` ます。</span><span class="sxs-lookup"><span data-stu-id="bb746-131">Apply the [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) mask to `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|
|`riid`|<span data-ttu-id="bb746-132">から要求された [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスのインターフェイス識別子 IID_ICLRRuntimeInfo を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb746-132">[in] Specifies the interface identifier IID_ICLRRuntimeInfo for the requested [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|
|`ppRuntime`|<span data-ttu-id="bb746-133">入出力が返されるときに `GetRequestedRuntime` 、対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスへのポインターを格納します。</span><span class="sxs-lookup"><span data-stu-id="bb746-133">[out] When `GetRequestedRuntime` returns, contains a pointer to the corresponding [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bb746-134">解説</span><span class="sxs-lookup"><span data-stu-id="bb746-134">Remarks</span></span>

<span data-ttu-id="bb746-135">このメソッドが正常に実行されると、`<configuration><runtime>` セクション内の構成ストリームに次の要素の 1 つ以上が存在する場合 にのみ、返されるランタイム インターフェイスの追加フラグと現在の既定のスタートアップ フラグが結合するという副作用が発生します。</span><span class="sxs-lookup"><span data-stu-id="bb746-135">When this method succeeds, it has the side effect of combining additional flags with the current default startup flags of the returned runtime interface, if and only if one or more of the following elements exist in the configuration stream within the `<configuration><runtime>` section:</span></span>

- <span data-ttu-id="bb746-136">`<gcServer enabled="true"/>` により `STARTUP_SERVER_GC` が設定されます。</span><span class="sxs-lookup"><span data-stu-id="bb746-136">`<gcServer enabled="true"/>` causes `STARTUP_SERVER_GC` to be set.</span></span>

- <span data-ttu-id="bb746-137">`<etwEnable enabled="true"/>` により `STARTUP_ETW` が設定されます。</span><span class="sxs-lookup"><span data-stu-id="bb746-137">`<etwEnable enabled="true"/>` causes `STARTUP_ETW` to be set.</span></span>

- <span data-ttu-id="bb746-138">`<appDomainResourceMonitoring enabled="true"/>` により `STARTUP_ARM` が設定されます。</span><span class="sxs-lookup"><span data-stu-id="bb746-138">`<appDomainResourceMonitoring enabled="true"/>` causes `STARTUP_ARM` to be set.</span></span>

<span data-ttu-id="bb746-139">結果として得られる既定の `STARTUP_FLAGS` 値は、上記の既定のスタートアップ フラグの一覧から設定される値のビットごとの OR の組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="bb746-139">The resulting default `STARTUP_FLAGS` value is the bitwise OR combination of the values that are set from the preceding list with the default startup flags.</span></span>

## <a name="return-value"></a><span data-ttu-id="bb746-140">戻り値</span><span class="sxs-lookup"><span data-stu-id="bb746-140">Return Value</span></span>

<span data-ttu-id="bb746-141">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="bb746-141">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="bb746-142">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb746-142">HRESULT</span></span>|<span data-ttu-id="bb746-143">説明</span><span class="sxs-lookup"><span data-stu-id="bb746-143">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="bb746-144">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb746-144">S_OK</span></span>|<span data-ttu-id="bb746-145">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="bb746-145">The method completed successfully.</span></span>|
|<span data-ttu-id="bb746-146">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="bb746-146">E_POINTER</span></span>|<span data-ttu-id="bb746-147">`pwzVersion` は null 以外で、`pcchVersion` は null です。</span><span class="sxs-lookup"><span data-stu-id="bb746-147">`pwzVersion` is not null and `pcchVersion` is null.</span></span><br /><br /> <span data-ttu-id="bb746-148">\- または -</span><span class="sxs-lookup"><span data-stu-id="bb746-148">-or-</span></span><br /><br /> <span data-ttu-id="bb746-149">`pwzImageVersion` は null 以外で、`pcchImageVersion` は null です。</span><span class="sxs-lookup"><span data-stu-id="bb746-149">`pwzImageVersion` is not null and `pcchImageVersion` is null.</span></span>|
|<span data-ttu-id="bb746-150">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bb746-150">E_INVALIDARG</span></span>|<span data-ttu-id="bb746-151">`dwPolicyFlags` は `METAHOST_POLICY_HIGHCOMPAT` を指定しません。</span><span class="sxs-lookup"><span data-stu-id="bb746-151">`dwPolicyFlags` does not specify `METAHOST_POLICY_HIGHCOMPAT`.</span></span>|
|<span data-ttu-id="bb746-152">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="bb746-152">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="bb746-153">`pwzVersion` に割り当てられたメモリが不十分です。</span><span class="sxs-lookup"><span data-stu-id="bb746-153">The memory allocated to `pwzVersion` is inadequate.</span></span><br /><br /> <span data-ttu-id="bb746-154">\- または -</span><span class="sxs-lookup"><span data-stu-id="bb746-154">-or-</span></span><br /><br /> <span data-ttu-id="bb746-155">`pwzImageVersion` に割り当てられたメモリが不十分です。</span><span class="sxs-lookup"><span data-stu-id="bb746-155">The memory allocated to `pwzImageVersion` is inadequate.</span></span>|
|<span data-ttu-id="bb746-156">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="bb746-156">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="bb746-157">`dwPolicyFlags` には METAHOST_POLICY_APPLY_UPGRADE_POLICY が含まれ、`pwzVersion` と `pcchVersion` はいずれも null です。</span><span class="sxs-lookup"><span data-stu-id="bb746-157">`dwPolicyFlags` includes METAHOST_POLICY_APPLY_UPGRADE_POLICY, and both `pwzVersion` and `pcchVersion` are null.</span></span>|

## <a name="requirements"></a><span data-ttu-id="bb746-158">要件</span><span class="sxs-lookup"><span data-stu-id="bb746-158">Requirements</span></span>

<span data-ttu-id="bb746-159">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb746-159">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="bb746-160">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="bb746-160">**Header:** MetaHost.h</span></span>

<span data-ttu-id="bb746-161">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bb746-161">**Library:** Included as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="bb746-162">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb746-162">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bb746-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb746-163">See also</span></span>

- [<span data-ttu-id="bb746-164">ICLRMetaHostPolicy インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb746-164">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)
- [<span data-ttu-id="bb746-165">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb746-165">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="bb746-166">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb746-166">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="bb746-167">ホスティング</span><span class="sxs-lookup"><span data-stu-id="bb746-167">Hosting</span></span>](index.md)
