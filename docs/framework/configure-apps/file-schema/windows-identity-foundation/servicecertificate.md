---
description: '詳細情報: <serviceCertificate>'
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: d9940fd96667211b1f9fd672b824af84e0d5143a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725325"
---
# \<serviceCertificate>

<span data-ttu-id="fb430-102">トークンの暗号化と復号化に使用される x.509 証明書を構成します。</span><span class="sxs-lookup"><span data-stu-id="fb430-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="fb430-103">構文</span><span class="sxs-lookup"><span data-stu-id="fb430-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb430-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fb430-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fb430-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb430-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb430-106">属性</span><span class="sxs-lookup"><span data-stu-id="fb430-106">Attributes</span></span>  

 <span data-ttu-id="fb430-107">なし</span><span class="sxs-lookup"><span data-stu-id="fb430-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fb430-108">子要素</span><span class="sxs-lookup"><span data-stu-id="fb430-108">Child Elements</span></span>  
  
|<span data-ttu-id="fb430-109">要素</span><span class="sxs-lookup"><span data-stu-id="fb430-109">Element</span></span>|<span data-ttu-id="fb430-110">説明</span><span class="sxs-lookup"><span data-stu-id="fb430-110">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="fb430-111">証明書ストアの x.509 証明書を検索して検証するために使用する設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="fb430-111">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb430-112">親要素</span><span class="sxs-lookup"><span data-stu-id="fb430-112">Parent Elements</span></span>  
  
|<span data-ttu-id="fb430-113">要素</span><span class="sxs-lookup"><span data-stu-id="fb430-113">Element</span></span>|<span data-ttu-id="fb430-114">説明</span><span class="sxs-lookup"><span data-stu-id="fb430-114">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="fb430-115"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfam) と (SAM) を構成する設定が含まれてい <xref:System.IdentityModel.Services.SessionAuthenticationModule> ます。</span><span class="sxs-lookup"><span data-stu-id="fb430-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fb430-116">例</span><span class="sxs-lookup"><span data-stu-id="fb430-116">Example</span></span>  

 <span data-ttu-id="fb430-117">次の XML は、要素の使用方法を示して \<serviceCertificate> います。</span><span class="sxs-lookup"><span data-stu-id="fb430-117">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="fb430-118">XML は、「」のサンプルから抜粋したものです `CustomToken` 。</span><span class="sxs-lookup"><span data-stu-id="fb430-118">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
