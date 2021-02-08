---
description: '詳細情報: <certificateValidator>'
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 0b92eada916b239ca56342021bb958da6d02c2e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802165"
---
# \<certificateValidator>

<span data-ttu-id="7ec84-102">証明書の検証に使用するカスタムの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="7ec84-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="7ec84-103">この型は `certificateValidationMode` 、要素の属性 [\<certificateValidation>](certificatevalidation.md) が "Custom" に設定されている場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="7ec84-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="7ec84-104">構文</span><span class="sxs-lookup"><span data-stu-id="7ec84-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ec84-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7ec84-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7ec84-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ec84-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ec84-107">属性</span><span class="sxs-lookup"><span data-stu-id="7ec84-107">Attributes</span></span>  
  
|<span data-ttu-id="7ec84-108">属性</span><span class="sxs-lookup"><span data-stu-id="7ec84-108">Attribute</span></span>|<span data-ttu-id="7ec84-109">説明</span><span class="sxs-lookup"><span data-stu-id="7ec84-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7ec84-110">type</span><span class="sxs-lookup"><span data-stu-id="7ec84-110">type</span></span>|<span data-ttu-id="7ec84-111">クラスから派生するカスタム型を指定し <xref:System.IdentityModel.Selectors.X509CertificateValidator> ます。</span><span class="sxs-lookup"><span data-stu-id="7ec84-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="7ec84-112">`certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) この型を使用するには、要素の属性を "Custom" に設定します。</span><span class="sxs-lookup"><span data-stu-id="7ec84-112">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="7ec84-113">属性を指定する方法の詳細については `type` 、「 [カスタム型参照](../windows-workflow-foundation/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ec84-113">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="7ec84-114">任意。</span><span class="sxs-lookup"><span data-stu-id="7ec84-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ec84-115">子要素</span><span class="sxs-lookup"><span data-stu-id="7ec84-115">Child Elements</span></span>  

 <span data-ttu-id="7ec84-116">なし</span><span class="sxs-lookup"><span data-stu-id="7ec84-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ec84-117">親要素</span><span class="sxs-lookup"><span data-stu-id="7ec84-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7ec84-118">要素</span><span class="sxs-lookup"><span data-stu-id="7ec84-118">Element</span></span>|<span data-ttu-id="7ec84-119">説明</span><span class="sxs-lookup"><span data-stu-id="7ec84-119">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="7ec84-120">トークンハンドラーが証明書を検証するために使用する設定を制御します。</span><span class="sxs-lookup"><span data-stu-id="7ec84-120">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7ec84-121">例</span><span class="sxs-lookup"><span data-stu-id="7ec84-121">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
