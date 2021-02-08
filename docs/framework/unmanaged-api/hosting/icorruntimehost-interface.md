---
description: 詳細については、「ICorRuntimeHost インターフェイス」を参照してください。
title: ICorRuntimeHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: cd50d31668b2dd0718dbe644343bfe314a0afdbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789659"
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="4de03-103">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4de03-103">ICorRuntimeHost Interface</span></span>

<span data-ttu-id="4de03-104">ホストが共通言語ランタイム (CLR) を明示的に開始および停止し、アプリケーションドメインの作成と構成、既定のドメインへのアクセス、およびプロセスで実行されているすべてのドメインの列挙を行うことができるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4de03-104">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="4de03-105">.NET Framework バージョン2.0 では、このインターフェイスは [ICLRRuntimeHost](iclrruntimehost-interface.md)によって置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="4de03-105">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4de03-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-106">Methods</span></span>  
  
|<span data-ttu-id="4de03-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-107">Method</span></span>|<span data-ttu-id="4de03-108">説明</span><span class="sxs-lookup"><span data-stu-id="4de03-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4de03-109">CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-109">CloseEnum Method</span></span>](icorruntimehost-closeenum-method.md)|<span data-ttu-id="4de03-110">ドメイン列挙子をドメインリストの先頭にリセットします。</span><span class="sxs-lookup"><span data-stu-id="4de03-110">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="4de03-111">CreateDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-111">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)|<span data-ttu-id="4de03-112">アプリケーションドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="4de03-112">Creates an application domain.</span></span> <span data-ttu-id="4de03-113">呼び出し元は、型のインターフェイスポインターを <xref:System._AppDomain> 型のインスタンスに受信し <xref:System.AppDomain?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="4de03-113">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="4de03-114">CreateDomainEx メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-114">CreateDomainEx Method</span></span>](icorruntimehost-createdomainex-method.md)|<span data-ttu-id="4de03-115">アプリケーションドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="4de03-115">Creates an application domain.</span></span> <span data-ttu-id="4de03-116">このメソッドを使用すると、呼び出し元は IAppDomainSetup インスタンスを渡して、返されたインスタンスの追加の機能を構成でき <xref:System._AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="4de03-116">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="4de03-117">CreateDomainSetup メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-117">CreateDomainSetup Method</span></span>](icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="4de03-118">インスタンスへの型のインターフェイスポインターを取得し `IAppDomainSetup` <xref:System.AppDomainSetup> ます。</span><span class="sxs-lookup"><span data-stu-id="4de03-118">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="4de03-119">`IAppDomainSetup` アプリケーションドメインを作成する前に構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4de03-119">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="4de03-120">CreateEvidence メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-120">CreateEvidence Method</span></span>](icorruntimehost-createevidence-method.md)|<span data-ttu-id="4de03-121">型のインターフェイスポインターを取得します <xref:System.Security.Principal.IIdentity> 。これにより、ホストは、 [createdomain](icorruntimehost-createdomain-method.md) または [createdomainex](icorruntimehost-createdomainex-method.md)に渡すセキュリティ証拠を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4de03-121">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="4de03-122">CreateLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-122">CreateLogicalThreadState Method</span></span>](icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="4de03-123">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4de03-123">Do not use.</span></span>|  
|[<span data-ttu-id="4de03-124">CurrentDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-124">CurrentDomain Method</span></span>](icorruntimehost-currentdomain-method.md)|<span data-ttu-id="4de03-125"><xref:System._AppDomain>現在のスレッドに読み込まれているドメインを表す型のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4de03-125">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="4de03-126">DeleteLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-126">DeleteLogicalThreadState Method</span></span>](icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="4de03-127">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4de03-127">Do not use.</span></span>|  
|[<span data-ttu-id="4de03-128">EnumDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-128">EnumDomains Method</span></span>](icorruntimehost-enumdomains-method.md)|<span data-ttu-id="4de03-129">現在のプロセス内のドメインの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="4de03-129">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="4de03-130">GetConfiguration メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-130">GetConfiguration Method</span></span>](icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="4de03-131">ホストが CLR のコールバック構成を指定できるようにするオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="4de03-131">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="4de03-132">GetDefaultDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-132">GetDefaultDomain Method</span></span>](icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="4de03-133"><xref:System._AppDomain>現在のプロセスの既定のドメインを表す型のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4de03-133">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="4de03-134">LocksHeldByLogicalThread メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-134">LocksHeldByLogicalThread Method</span></span>](icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="4de03-135">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4de03-135">Do not use.</span></span>|  
|[<span data-ttu-id="4de03-136">MapFile メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-136">MapFile Method</span></span>](icorruntimehost-mapfile-method.md)|<span data-ttu-id="4de03-137">指定されたファイルをメモリにマップします。</span><span class="sxs-lookup"><span data-stu-id="4de03-137">Maps the specified file into memory.</span></span> <span data-ttu-id="4de03-138">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="4de03-138">This method is obsolete.</span></span>|  
|[<span data-ttu-id="4de03-139">NextDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-139">NextDomain Method</span></span>](icorruntimehost-nextdomain-method.md)|<span data-ttu-id="4de03-140">列挙体の次のドメインへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4de03-140">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="4de03-141">Start メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-141">Start Method</span></span>](icorruntimehost-start-method.md)|<span data-ttu-id="4de03-142">CLR を開始します。</span><span class="sxs-lookup"><span data-stu-id="4de03-142">Starts the CLR.</span></span>|  
|[<span data-ttu-id="4de03-143">Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-143">Stop Method</span></span>](icorruntimehost-stop-method.md)|<span data-ttu-id="4de03-144">現在のプロセスのランタイムでコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="4de03-144">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="4de03-145">SwitchInLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-145">SwitchInLogicalThreadState Method</span></span>](icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="4de03-146">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4de03-146">Do not use.</span></span>|  
|[<span data-ttu-id="4de03-147">SwitchOutLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-147">SwitchOutLogicalThreadState Method</span></span>](icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="4de03-148">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4de03-148">Do not use.</span></span>|  
|[<span data-ttu-id="4de03-149">UnloadDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="4de03-149">UnloadDomain Method</span></span>](icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="4de03-150">現在のプロセスから、指定されたアプリケーションドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="4de03-150">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4de03-151">要件</span><span class="sxs-lookup"><span data-stu-id="4de03-151">Requirements</span></span>  

 <span data-ttu-id="4de03-152">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4de03-152">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4de03-153">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4de03-153">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4de03-154">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4de03-154">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4de03-155">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="4de03-155">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4de03-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="4de03-156">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="4de03-157">ホスティング</span><span class="sxs-lookup"><span data-stu-id="4de03-157">Hosting</span></span>](index.md)
- [<span data-ttu-id="4de03-158">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4de03-158">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- <span data-ttu-id="4de03-159">[ランタイム ホスト](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4de03-159">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
- [<span data-ttu-id="4de03-160">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4de03-160">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="4de03-161">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="4de03-161">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
