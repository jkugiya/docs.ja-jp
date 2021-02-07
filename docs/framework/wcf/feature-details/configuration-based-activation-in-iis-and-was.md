---
description: 詳細については、「IIS および WAS での Configuration-Based のアクティブ化」を参照してください。
title: IIS と WAS における構成ベースのアクティブ化
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 7515e3f0d3035e1ab93c67980bd00eeb0a063d17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743370"
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="c30da-103">IIS と WAS における構成ベースのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="c30da-103">Configuration-Based Activation in IIS and WAS</span></span>

<span data-ttu-id="c30da-104">通常、インターネットインフォメーションサービス (IIS) または Windows プロセスアクティブ化サービス (WAS) で Windows Communication Foundation (WCF) サービスをホストする場合は、.svc ファイルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c30da-104">Normally when hosting a Windows Communication Foundation (WCF) service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="c30da-105">.svc ファイルには、サービスの名前と、オプションのカスタム サービス ホスト ファクトリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c30da-105">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="c30da-106">この追加ファイルによって、管理のオーバーヘッドが増加します。</span><span class="sxs-lookup"><span data-stu-id="c30da-106">This additional file adds manageability overhead.</span></span> <span data-ttu-id="c30da-107">構成ベースのアクティブ化機能により、.svc ファイルを用意する必要がなくなり、関連するオーバーヘッドも発生しません。</span><span class="sxs-lookup"><span data-stu-id="c30da-107">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>

## <a name="configuration-based-activation"></a><span data-ttu-id="c30da-108">構成ベースのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="c30da-108">Configuration-Based Activation</span></span>

<span data-ttu-id="c30da-109">構成ベースのアクティブ化では、以前は .svc ファイルに配置されていたメタデータを受け取り、それを Web.config ファイルに配置します。</span><span class="sxs-lookup"><span data-stu-id="c30da-109">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="c30da-110"><`serviceHostingEnvironment`> 要素内に <`serviceActivations`> 要素があります。</span><span class="sxs-lookup"><span data-stu-id="c30da-110">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="c30da-111"><`serviceActivations`> 要素内には、ホストされる `add` サービスごとに1つの <> 要素が1つ以上含まれます。</span><span class="sxs-lookup"><span data-stu-id="c30da-111">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="c30da-112"><の> 要素には、サービス `add` の相対アドレス、サービスの種類、サービスホストファクトリを設定できる属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c30da-112">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="c30da-113">次の構成コード例は、このセクションの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c30da-113">The following configuration example code shows how this section is used.</span></span>

> [!NOTE]
> <span data-ttu-id="c30da-114">各 <`add`> 要素には、サービスまたはファクトリ属性を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c30da-114">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="c30da-115">サービスとファクトリ属性の両方を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c30da-115">Specifying both service and factory attributes is allowed.</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 <span data-ttu-id="c30da-116">このコードを Web.config ファイルに含めると、サービス ソース コードをアプリケーションの App_Code ディレクトリに配置するか、コンパイル済みアセンブリをアプリケーションの Bin ディレクトリに配置することができます。</span><span class="sxs-lookup"><span data-stu-id="c30da-116">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="c30da-117">構成ベースのアクティブ化機能を使用する場合、.svc ファイルのインライン コードはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="c30da-117">When using configuration-based activation, inline code in .svc files is not supported.</span></span>
> - <span data-ttu-id="c30da-118">属性は、 `relativeAddress` " \<sub-directory> /servicesub-directory" や "~/ \< /service .svc" などの相対アドレスに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c30da-118">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>
> - <span data-ttu-id="c30da-119">WCF と関連付けられている既知の拡張子を持たない相対アドレスを登録すると、構成例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c30da-119">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>
> - <span data-ttu-id="c30da-120">指定された相対アドレスは、仮想アプリケーションのルートが基準になります。</span><span class="sxs-lookup"><span data-stu-id="c30da-120">The relative address specified is relative to the root of the virtual application.</span></span>
> - <span data-ttu-id="c30da-121">構成の階層的モデルにより、コンピューター レベルおよびサイト レベルの登録された相対アドレスは、仮想アプリケーションによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="c30da-121">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>
> - <span data-ttu-id="c30da-122">構成ファイル内での登録は、.svc、.xamlx、.xoml、またはその他のファイルでの設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="c30da-122">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>
> - <span data-ttu-id="c30da-123">IIS/WAS に送信された URI 内の \ (円記号) は、自動的に / (スラッシュ) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c30da-123">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="c30da-124">\ を含む相対アドレスが追加され、その相対アドレスを使用する URI を IIS に送信した場合は、円記号がスラッシュに変換されるため、IIS では、それを相対アドレスと一致させることができません。</span><span class="sxs-lookup"><span data-stu-id="c30da-124">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="c30da-125">IIS は、一致するものが見つからなかったことを示すトレース情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="c30da-125">IIS sends out trace information that indicates that there are no matches found.</span></span>

## <a name="see-also"></a><span data-ttu-id="c30da-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c30da-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [<span data-ttu-id="c30da-127">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="c30da-127">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="c30da-128">ワークフロー サービスのホストの概要</span><span class="sxs-lookup"><span data-stu-id="c30da-128">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md)
- <span data-ttu-id="c30da-129">[AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c30da-129">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
