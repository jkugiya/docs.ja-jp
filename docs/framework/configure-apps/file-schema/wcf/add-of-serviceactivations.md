---
description: 詳細については <add> 、 <serviceActivations>
title: <add> の <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 53c89321c8cde1966a04870c62fa0777610ff547
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750144"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="cc9fb-103">\<add> の \<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="cc9fb-103">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="cc9fb-104">Windows Communication Foundation (WCF) サービスの種類にマップする仮想サービスのアクティブ化の設定を定義できるようにする構成要素。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-104">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="cc9fb-105">これにより、.svc ファイルを使用せずに、WAS/IIS でホストされているサービスをアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-105">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="cc9fb-106">構文</span><span class="sxs-lookup"><span data-stu-id="cc9fb-106">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc9fb-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cc9fb-107">Attributes and Elements</span></span>

<span data-ttu-id="cc9fb-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc9fb-109">属性</span><span class="sxs-lookup"><span data-stu-id="cc9fb-109">Attributes</span></span>

|<span data-ttu-id="cc9fb-110">属性</span><span class="sxs-lookup"><span data-stu-id="cc9fb-110">Attribute</span></span>|<span data-ttu-id="cc9fb-111">説明</span><span class="sxs-lookup"><span data-stu-id="cc9fb-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="cc9fb-112">factory</span><span class="sxs-lookup"><span data-stu-id="cc9fb-112">factory</span></span>|<span data-ttu-id="cc9fb-113">サービス アクティベーション要素を生成するファクトリの CLR 型名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-113">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="cc9fb-114">service</span><span class="sxs-lookup"><span data-stu-id="cc9fb-114">service</span></span>|<span data-ttu-id="cc9fb-115">サービスを実装する ServiceType (完全修飾 Typename または省略形の Typename (App_Code フォルダーに配置されている場合))。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-115">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="cc9fb-116">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="cc9fb-116">relativeAddress</span></span>|<span data-ttu-id="cc9fb-117">現在の IIS アプリケーション内の相対アドレス (たとえば "Service.svc")。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-117">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="cc9fb-118">WCF 4.0 では、この相対アドレスには既知のファイル拡張子 (.svc、.xamlx、...) のいずれかが含まれている必要があります。RelativeUrl の物理ファイルが存在しません</span><span class="sxs-lookup"><span data-stu-id="cc9fb-118">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="cc9fb-119">子要素</span><span class="sxs-lookup"><span data-stu-id="cc9fb-119">Child Elements</span></span>

<span data-ttu-id="cc9fb-120">なし。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cc9fb-121">親要素</span><span class="sxs-lookup"><span data-stu-id="cc9fb-121">Parent Elements</span></span>

|<span data-ttu-id="cc9fb-122">要素</span><span class="sxs-lookup"><span data-stu-id="cc9fb-122">Element</span></span>|<span data-ttu-id="cc9fb-123">説明</span><span class="sxs-lookup"><span data-stu-id="cc9fb-123">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="cc9fb-124">アクティベーション設定を記述する構成セクション。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-124">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc9fb-125">解説</span><span class="sxs-lookup"><span data-stu-id="cc9fb-125">Remarks</span></span>

<span data-ttu-id="cc9fb-126">web.config ファイルでアクティベーション設定を構成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-126">The following example shows how to configure activation settings within your web.config file.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="cc9fb-127">この構成を使用して、.svc ファイルを使用せずに、GreetingService をアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-127">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="cc9fb-128">`<serviceHostingEnvironment>` はアプリケーション レベルの構成であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-128">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="cc9fb-129">構成を格納した `web.config` は、仮想アプリケーションのルートの下に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-129">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="cc9fb-130">また、 `serviceHostingEnvironment` は machineToApplication 継承可能なセクションです。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-130">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="cc9fb-131">コンピューターのルートに単一のサービスを登録すると、アプリケーションの各サービスはこのサービスを継承します。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-131">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="cc9fb-132">構成ベースのアクティベーションは、http および非 http プロトコル経由のアクティベーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-132">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="cc9fb-133">RelativeAddress の拡張機能、つまり .svc、xoml、または .xamlx が必要です。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-133">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="cc9fb-134">既知の buildProviders に対して独自の拡張子をマップできます。これにより、任意の拡張子を使用してサービスをアクティブ化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-134">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="cc9fb-135">競合が発生した場合には、`<serviceActivations>` セクションにより、.svc の登録がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="cc9fb-135">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc9fb-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc9fb-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
