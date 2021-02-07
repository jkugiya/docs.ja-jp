---
description: 詳細については、「IAppDomainSetup インターフェイス」を参照してください。
title: IAppDomainSetup インターフェイス
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 8fd224308ea68f7b56ae174c7f71fc4f89630101
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760585"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="d92f3-103">IAppDomainSetup インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d92f3-103">IAppDomainSetup Interface</span></span>

<span data-ttu-id="d92f3-104"><xref:System.AppDomain?displayProperty=nameWithType> [ICorRuntimeHost:: CreateDomainEx](icorruntimehost-createdomainex-method.md)メソッドを呼び出して作成する前に、ホストが型を構成できるようにするプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-104">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d92f3-105">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d92f3-105">Properties</span></span>  
  
|<span data-ttu-id="d92f3-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d92f3-106">Property</span></span>|<span data-ttu-id="d92f3-107">説明</span><span class="sxs-lookup"><span data-stu-id="d92f3-107">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="d92f3-108">アプリケーションが格納されているディレクトリの名前を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-108">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="d92f3-109">アプリケーションの名前を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-109">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="d92f3-110">ファイルがシャドウコピーされるアプリケーション固有の領域の名前を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-110">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="d92f3-111">アプリケーションの構成ファイルの名前を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-111">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="d92f3-112">動的に生成されたファイルが格納およびアクセスされるディレクトリの名前を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-112">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="d92f3-113">このドメインに関連付けられているライセンスファイルへのパスを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-113">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="d92f3-114">プライベートアセンブリをプローブするディレクトリと結合されたディレクトリの一覧を取得または設定し <xref:System.AppDomainSetup.ApplicationBase%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="d92f3-114">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="d92f3-115"><xref:System.AppDomainSetup.ApplicationBase%2A>アプリケーションの検索パスに含めたり、検索パスから除外したりする文字列値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-115">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="d92f3-116">シャドウコピーされるアセンブリを含むディレクトリの名前を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-116">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="d92f3-117">シャドウコピーをオンまたはオフにするかどうかを示す文字列を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-117">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="d92f3-118">有効な値は "true" または "false" です。</span><span class="sxs-lookup"><span data-stu-id="d92f3-118">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d92f3-119">解説</span><span class="sxs-lookup"><span data-stu-id="d92f3-119">Remarks</span></span>  

 <span data-ttu-id="d92f3-120">インターフェイスは、 `IAppDomainSetup` <xref:System.IAppDomainSetup> 型が実装するマネージインターフェイスに対応 <xref:System.AppDomainSetup> します。</span><span class="sxs-lookup"><span data-stu-id="d92f3-120">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="d92f3-121"><xref:System.IAppDomainSetup?displayProperty=nameWithType>プロパティの詳細については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d92f3-121">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="d92f3-122">`IAppDomainSetup` 作成前にインスタンスに追加できるアセンブリバインディング情報を表し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="d92f3-122">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="d92f3-123">たとえば、ホストは、プロパティを設定して、 <xref:System.AppDomainSetup.ApplicationBase%2A> マネージアセンブリの共通言語ランタイム (CLR) プローブがルートディレクトリを確立することができます。</span><span class="sxs-lookup"><span data-stu-id="d92f3-123">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d92f3-124">要件</span><span class="sxs-lookup"><span data-stu-id="d92f3-124">Requirements</span></span>  

 <span data-ttu-id="d92f3-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d92f3-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d92f3-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d92f3-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d92f3-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d92f3-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d92f3-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d92f3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d92f3-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="d92f3-129">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="d92f3-130">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d92f3-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
