---
description: '詳細情報: <remove>'
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 942148f677e10bbab7b86acfba2d0fdfb1b10ca7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664068"
---
# \<remove>

<span data-ttu-id="61742-102">指定されたセキュリティトークンハンドラーをトークンハンドラーコレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="61742-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="61742-103">構文</span><span class="sxs-lookup"><span data-stu-id="61742-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61742-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="61742-104">Attributes and Elements</span></span>  

 <span data-ttu-id="61742-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="61742-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61742-106">属性</span><span class="sxs-lookup"><span data-stu-id="61742-106">Attributes</span></span>  
  
|<span data-ttu-id="61742-107">属性</span><span class="sxs-lookup"><span data-stu-id="61742-107">Attribute</span></span>|<span data-ttu-id="61742-108">説明</span><span class="sxs-lookup"><span data-stu-id="61742-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61742-109">type</span><span class="sxs-lookup"><span data-stu-id="61742-109">type</span></span>|<span data-ttu-id="61742-110">削除するトークンハンドラーの CLR 型名。</span><span class="sxs-lookup"><span data-stu-id="61742-110">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="61742-111">属性を指定する方法の詳細については `type` 、「 [カスタム型参照](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61742-111">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="61742-112">必須。</span><span class="sxs-lookup"><span data-stu-id="61742-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61742-113">子要素</span><span class="sxs-lookup"><span data-stu-id="61742-113">Child Elements</span></span>  

 <span data-ttu-id="61742-114">なし</span><span class="sxs-lookup"><span data-stu-id="61742-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61742-115">親要素</span><span class="sxs-lookup"><span data-stu-id="61742-115">Parent Elements</span></span>  
  
|<span data-ttu-id="61742-116">要素</span><span class="sxs-lookup"><span data-stu-id="61742-116">Element</span></span>|<span data-ttu-id="61742-117">説明</span><span class="sxs-lookup"><span data-stu-id="61742-117">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="61742-118">エンドポイントに登録されているセキュリティトークンハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="61742-118">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="61742-119">例</span><span class="sxs-lookup"><span data-stu-id="61742-119">Example</span></span>  

 <span data-ttu-id="61742-120">次の XML は、および要素を使用して、 `<add>` `<remove>` 既定のセッショントークンハンドラーをカスタムセッショントークンハンドラーに置き換える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="61742-120">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="61742-121">XML は、「」のサンプルから抜粋したものです `ClaimsAwareWebFarm` 。</span><span class="sxs-lookup"><span data-stu-id="61742-121">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
