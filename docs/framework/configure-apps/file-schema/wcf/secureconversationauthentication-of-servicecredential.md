---
description: 詳細については <secureConversationAuthentication> 、 <serviceCredential>
title: <secureConversationAuthentication> の <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 8f95b4009111996d2a5c1133c9ef762375b4e3e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683321"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="527e4-103">\<secureConversationAuthentication> の \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="527e4-103">\<secureConversationAuthentication> of \<serviceCredential></span></span>

<span data-ttu-id="527e4-104">安全な会話サービスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="527e4-104">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="527e4-105">構文</span><span class="sxs-lookup"><span data-stu-id="527e4-105">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="527e4-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="527e4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="527e4-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="527e4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="527e4-108">属性</span><span class="sxs-lookup"><span data-stu-id="527e4-108">Attributes</span></span>  
  
|<span data-ttu-id="527e4-109">属性</span><span class="sxs-lookup"><span data-stu-id="527e4-109">Attribute</span></span>|<span data-ttu-id="527e4-110">説明</span><span class="sxs-lookup"><span data-stu-id="527e4-110">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="527e4-111">使用される <xref:System.ServiceModel.Security.SecurityStateEncoder> の型を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="527e4-111">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="527e4-112">子要素</span><span class="sxs-lookup"><span data-stu-id="527e4-112">Child Elements</span></span>  

 <span data-ttu-id="527e4-113">なし。</span><span class="sxs-lookup"><span data-stu-id="527e4-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="527e4-114">親要素</span><span class="sxs-lookup"><span data-stu-id="527e4-114">Parent Elements</span></span>  
  
|<span data-ttu-id="527e4-115">要素</span><span class="sxs-lookup"><span data-stu-id="527e4-115">Element</span></span>|<span data-ttu-id="527e4-116">説明</span><span class="sxs-lookup"><span data-stu-id="527e4-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="527e4-117">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="527e4-117">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="527e4-118">解説</span><span class="sxs-lookup"><span data-stu-id="527e4-118">Remarks</span></span>  

 <span data-ttu-id="527e4-119">この構成要素を使用して、セキュリティ コンテキスト トークン (SCT) クッキーのシリアル化のための既知のクレームの種類のリストと、クッキーの情報をエンコードしてセキュリティで保護するためのエンコーダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="527e4-119">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="527e4-120">SCT の詳細については、「<xref:System.ServiceModel.Security.SecureConversationServiceCredential>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="527e4-120">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="527e4-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="527e4-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
