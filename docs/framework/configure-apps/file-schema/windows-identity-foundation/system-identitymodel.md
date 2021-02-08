---
description: '詳細については、次を参照してください: <システム>'
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: c597f2a849248366f9cf3847c8ef369c13d7a286
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786526"
---
# \<system.identityModel>

<span data-ttu-id="1a5d9-103">アプリケーションで Windows Identity Foundation (WIF) オプションを有効にするための構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="1a5d9-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="1a5d9-104">構文</span><span class="sxs-lookup"><span data-stu-id="1a5d9-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a5d9-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1a5d9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1a5d9-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a5d9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a5d9-107">属性</span><span class="sxs-lookup"><span data-stu-id="1a5d9-107">Attributes</span></span>  

 <span data-ttu-id="1a5d9-108">なし</span><span class="sxs-lookup"><span data-stu-id="1a5d9-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1a5d9-109">子要素</span><span class="sxs-lookup"><span data-stu-id="1a5d9-109">Child Elements</span></span>  
  
|<span data-ttu-id="1a5d9-110">要素</span><span class="sxs-lookup"><span data-stu-id="1a5d9-110">Element</span></span>|<span data-ttu-id="1a5d9-111">説明</span><span class="sxs-lookup"><span data-stu-id="1a5d9-111">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="1a5d9-112">サービスレベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="1a5d9-112">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a5d9-113">親要素</span><span class="sxs-lookup"><span data-stu-id="1a5d9-113">Parent Elements</span></span>  
  
|<span data-ttu-id="1a5d9-114">要素</span><span class="sxs-lookup"><span data-stu-id="1a5d9-114">Element</span></span>|<span data-ttu-id="1a5d9-115">説明</span><span class="sxs-lookup"><span data-stu-id="1a5d9-115">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="1a5d9-116">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="1a5d9-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a5d9-117">解説</span><span class="sxs-lookup"><span data-stu-id="1a5d9-117">Remarks</span></span>  

 <span data-ttu-id="1a5d9-118">`<system.identityModel>`構成ファイルにセクションを追加して、Windows Identity Foundation (WIF) を使用するようにサービスまたはアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="1a5d9-118">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="1a5d9-119">`<system.identityModel>`要素は、クラスによって表され <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> ます。</span><span class="sxs-lookup"><span data-stu-id="1a5d9-119">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a5d9-120">例</span><span class="sxs-lookup"><span data-stu-id="1a5d9-120">Example</span></span>  

 <span data-ttu-id="1a5d9-121">次の例は、構成ファイルにセクションを追加する方法を示して `<system.identityModel>` います。</span><span class="sxs-lookup"><span data-stu-id="1a5d9-121">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="1a5d9-122">最初に、構成セクションと名前空間の宣言を要素の下に追加する必要があり `<configSections>` ます。</span><span class="sxs-lookup"><span data-stu-id="1a5d9-122">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="1a5d9-123">次に、要素を `<system.IdentityModel>` 構成ファイルに追加して、1つまたは複数の id 構成を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1a5d9-123">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a5d9-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a5d9-124">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
