---
description: 詳細については、「ICLRRuntimeHost インターフェイス」を参照してください。
title: ICLRRuntimeHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
ms.openlocfilehash: 92bab42fa1cf2cca5caa0eb039c88fec3e65390c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753888"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="d61a7-103">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d61a7-103">ICLRRuntimeHost Interface</span></span>

<span data-ttu-id="d61a7-104">.NET Framework バージョン1で提供される [ICorRuntimeHost](icorruntimehost-interface.md) インターフェイスと同様の機能を提供します。次の変更点があります。</span><span class="sxs-lookup"><span data-stu-id="d61a7-104">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="d61a7-105">ホストコントロールインターフェイスを設定するための [Sethostcontrol](iclrruntimehost-sethostcontrol-method.md) メソッドの追加。</span><span class="sxs-lookup"><span data-stu-id="d61a7-105">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="d61a7-106">によって提供されるいくつかのメソッドの省略 `ICorRuntimeHost` 。</span><span class="sxs-lookup"><span data-stu-id="d61a7-106">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d61a7-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-107">Methods</span></span>  
  
|<span data-ttu-id="d61a7-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-108">Method</span></span>|<span data-ttu-id="d61a7-109">説明</span><span class="sxs-lookup"><span data-stu-id="d61a7-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d61a7-110">ExecuteApplication メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-110">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="d61a7-111">新しいドメインでアクティブ化するアプリケーションを指定するために、マニフェストベースの ClickOnce 配置シナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="d61a7-111">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="d61a7-112">ExecuteInAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-112">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="d61a7-113">指定し <xref:System.AppDomain> たマネージコードを実行するを指定します。</span><span class="sxs-lookup"><span data-stu-id="d61a7-113">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="d61a7-114">ExecuteInDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-114">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="d61a7-115">指定したアセンブリ内で、指定した型の指定したメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d61a7-115">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="d61a7-116">GetCLRControl メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-116">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="d61a7-117">ホストが共通言語ランタイム (CLR) の側面をカスタマイズするために使用できる、 [ICLRControl](iclrcontrol-interface.md) 型のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d61a7-117">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="d61a7-118">GetCurrentAppDomainId メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-118">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="d61a7-119">現在実行中のの数値識別子を取得し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="d61a7-119">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="d61a7-120">SetHostControl メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-120">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="d61a7-121">ホストコントロールインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="d61a7-121">Sets the host control interface.</span></span> <span data-ttu-id="d61a7-122">を呼び出す前に、を呼び出す必要があり `SetHostControl` `Start` ます。</span><span class="sxs-lookup"><span data-stu-id="d61a7-122">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="d61a7-123">Start メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-123">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="d61a7-124">CLR をプロセスに初期化します。</span><span class="sxs-lookup"><span data-stu-id="d61a7-124">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="d61a7-125">Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-125">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="d61a7-126">ランタイムによるコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="d61a7-126">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="d61a7-127">UnloadAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="d61a7-127">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="d61a7-128">指定した <xref:System.AppDomain> 数値識別子に対応するをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="d61a7-128">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d61a7-129">解説</span><span class="sxs-lookup"><span data-stu-id="d61a7-129">Remarks</span></span>  

 <span data-ttu-id="d61a7-130">.NET Framework 4 以降では、 [ICLRMetaHost](iclrmetahost-interface.md) インターフェイスを使用して [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスへのポインターを取得し、 [ICLRRuntimeInfo:: getinterface](iclrruntimeinfo-getinterface-method.md) メソッドを呼び出して、へのポインターを取得し `ICLRRuntimeHost` ます。</span><span class="sxs-lookup"><span data-stu-id="d61a7-130">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="d61a7-131">以前のバージョンの .NET Framework では、ホストは `ICLRRuntimeHost` [Corbindtoruntimeex](corbindtoruntimeex-function.md) または [Corbindtoの entruntime](corbindtocurrentruntime-function.md)を呼び出すことによって、インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d61a7-131">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="d61a7-132">.NET Framework バージョン2.0 で提供されるテクノロジの実装を提供するには、の代わりにを使用する必要があり `ICLRRuntimeHost` `ICorRuntimeHost` ます。</span><span class="sxs-lookup"><span data-stu-id="d61a7-132">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d61a7-133">マニフェストベースのアプリケーションをアクティブ化するには、 [Executeapplication](iclrruntimehost-executeapplication-method.md)メソッドを呼び出す前に[Start](iclrruntimehost-start-method.md)メソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="d61a7-133">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="d61a7-134">`Start`メソッドが最初に呼び出された場合、 `ExecuteApplication` メソッドの呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="d61a7-134">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d61a7-135">要件</span><span class="sxs-lookup"><span data-stu-id="d61a7-135">Requirements</span></span>  

 <span data-ttu-id="d61a7-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d61a7-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d61a7-137">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d61a7-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d61a7-138">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d61a7-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d61a7-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d61a7-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d61a7-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="d61a7-140">See also</span></span>

- [<span data-ttu-id="d61a7-141">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="d61a7-141">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="d61a7-142">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="d61a7-142">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="d61a7-143">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d61a7-143">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="d61a7-144">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d61a7-144">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="d61a7-145">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d61a7-145">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="d61a7-146">CLRRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="d61a7-146">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
