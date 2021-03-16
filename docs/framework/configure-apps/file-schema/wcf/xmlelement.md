---
description: '詳細情報: <xmlElement>'
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 891f1a95c1f6a79127d48a1572bc805574225530
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682008"
---
# \<xmlElement>

<span data-ttu-id="6a43a-102">トークンの要求時にセキュリティ トークン サービスへのメッセージ本文で送信される XML 要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="6a43a-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="6a43a-103">構文</span><span class="sxs-lookup"><span data-stu-id="6a43a-103">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a43a-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6a43a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6a43a-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6a43a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a43a-106">属性</span><span class="sxs-lookup"><span data-stu-id="6a43a-106">Attributes</span></span>  
  
|<span data-ttu-id="6a43a-107">属性</span><span class="sxs-lookup"><span data-stu-id="6a43a-107">Attribute</span></span>|<span data-ttu-id="6a43a-108">説明</span><span class="sxs-lookup"><span data-stu-id="6a43a-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a43a-109">xmlElement</span><span class="sxs-lookup"><span data-stu-id="6a43a-109">xmlElement</span></span>|<span data-ttu-id="6a43a-110">トークンの要求時にセキュリティ トークン サービスへのメッセージ本文で送信される XML 要素を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="6a43a-110">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a43a-111">子要素</span><span class="sxs-lookup"><span data-stu-id="6a43a-111">Child Elements</span></span>  

 <span data-ttu-id="6a43a-112">なし。</span><span class="sxs-lookup"><span data-stu-id="6a43a-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a43a-113">親要素</span><span class="sxs-lookup"><span data-stu-id="6a43a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="6a43a-114">要素</span><span class="sxs-lookup"><span data-stu-id="6a43a-114">Element</span></span>|<span data-ttu-id="6a43a-115">説明</span><span class="sxs-lookup"><span data-stu-id="6a43a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="6a43a-116">トークン要求パラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="6a43a-116">A collection of token request parameters.</span></span> <span data-ttu-id="6a43a-117">各パラメーターは、XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="6a43a-117">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a43a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a43a-118">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="6a43a-119">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="6a43a-119">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6a43a-120">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="6a43a-120">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6a43a-121">カスタム バインディングを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="6a43a-121">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="6a43a-122">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="6a43a-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6a43a-123">バインド</span><span class="sxs-lookup"><span data-stu-id="6a43a-123">Bindings</span></span>](../../../wcf/bindings.md)
