---
description: '詳細情報: <serviceActivations>'
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 726514af4e42cc387daf61b688d528f690ec8ee8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683022"
---
# \<serviceActivations>

<span data-ttu-id="48c72-102">Windows Communication Foundation (WCF) サービスの種類にマップする仮想サービスのアクティブ化の設定を定義する設定を追加できるようにする構成要素。</span><span class="sxs-lookup"><span data-stu-id="48c72-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="48c72-103">これにより、.svc ファイルを使用せずに、WAS/IIS でホストされているサービスをアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="48c72-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

## <a name="syntax"></a><span data-ttu-id="48c72-104">構文</span><span class="sxs-lookup"><span data-stu-id="48c72-104">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48c72-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="48c72-105">Attributes and Elements</span></span>

<span data-ttu-id="48c72-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="48c72-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="48c72-107">属性</span><span class="sxs-lookup"><span data-stu-id="48c72-107">Attributes</span></span>

<span data-ttu-id="48c72-108">なし。</span><span class="sxs-lookup"><span data-stu-id="48c72-108">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48c72-109">子要素</span><span class="sxs-lookup"><span data-stu-id="48c72-109">Child Elements</span></span>

|<span data-ttu-id="48c72-110">要素</span><span class="sxs-lookup"><span data-stu-id="48c72-110">Element</span></span>|<span data-ttu-id="48c72-111">説明</span><span class="sxs-lookup"><span data-stu-id="48c72-111">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|<span data-ttu-id="48c72-112">サービス アプリケーションのアクティベーションを指定する構成要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="48c72-112">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="48c72-113">親要素</span><span class="sxs-lookup"><span data-stu-id="48c72-113">Parent Elements</span></span>

|<span data-ttu-id="48c72-114">要素</span><span class="sxs-lookup"><span data-stu-id="48c72-114">Element</span></span>|<span data-ttu-id="48c72-115">説明</span><span class="sxs-lookup"><span data-stu-id="48c72-115">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="48c72-116">環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。</span><span class="sxs-lookup"><span data-stu-id="48c72-116">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="48c72-117">解説</span><span class="sxs-lookup"><span data-stu-id="48c72-117">Remarks</span></span>

<span data-ttu-id="48c72-118">web.config ファイルでアクティベーション設定を構成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="48c72-118">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="48c72-119">この構成を使用して、.svc ファイルを使用せずに、GreetingService をアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="48c72-119">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="48c72-120">`<serviceHostingEnvironment>` はアプリケーション レベルの構成であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="48c72-120">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="48c72-121">構成を格納した `web.config` は、仮想アプリケーションのルートの下に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48c72-121">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="48c72-122">また、 `serviceHostingEnvironment` は machineToApplication 継承可能なセクションです。</span><span class="sxs-lookup"><span data-stu-id="48c72-122">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="48c72-123">コンピューターのルートに単一のサービスを登録すると、アプリケーションの各サービスはこのサービスを継承します。</span><span class="sxs-lookup"><span data-stu-id="48c72-123">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="48c72-124">構成ベースのアクティベーションは、http および非 http プロトコル経由のアクティベーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="48c72-124">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="48c72-125">これには、relativeAddress、xoml、または .xamlx の拡張機能が必要です。</span><span class="sxs-lookup"><span data-stu-id="48c72-125">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="48c72-126">既知の buildProviders に対して独自の拡張子をマップできます。これにより、任意の拡張子を使用してサービスをアクティブ化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="48c72-126">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="48c72-127">競合が発生した場合には、`<serviceActivations>` セクションにより、.svc の登録がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="48c72-127">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="48c72-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="48c72-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
