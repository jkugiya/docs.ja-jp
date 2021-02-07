---
description: '詳細情報: <issuerTokenResolver>'
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 535b6f098e168a198eb0949d6baba6659e5140db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664094"
---
# \<issuerTokenResolver>

<span data-ttu-id="bef3d-102">トークンハンドラーコレクションのハンドラーによって使用される発行者トークンリゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="bef3d-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="bef3d-103">発行者トークンリゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bef3d-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="bef3d-104">構文</span><span class="sxs-lookup"><span data-stu-id="bef3d-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bef3d-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bef3d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="bef3d-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bef3d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bef3d-107">属性</span><span class="sxs-lookup"><span data-stu-id="bef3d-107">Attributes</span></span>  
  
|<span data-ttu-id="bef3d-108">属性</span><span class="sxs-lookup"><span data-stu-id="bef3d-108">Attribute</span></span>|<span data-ttu-id="bef3d-109">説明</span><span class="sxs-lookup"><span data-stu-id="bef3d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bef3d-110">type</span><span class="sxs-lookup"><span data-stu-id="bef3d-110">type</span></span>|<span data-ttu-id="bef3d-111">発行者トークンリゾルバーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="bef3d-111">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="bef3d-112">は、クラス <xref:System.IdentityModel.Tokens.IssuerTokenResolver> またはクラスから派生した型のいずれかである必要があり <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ます。</span><span class="sxs-lookup"><span data-stu-id="bef3d-112">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="bef3d-113">必須。</span><span class="sxs-lookup"><span data-stu-id="bef3d-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bef3d-114">子要素</span><span class="sxs-lookup"><span data-stu-id="bef3d-114">Child Elements</span></span>  

 <span data-ttu-id="bef3d-115">なし</span><span class="sxs-lookup"><span data-stu-id="bef3d-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bef3d-116">親要素</span><span class="sxs-lookup"><span data-stu-id="bef3d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="bef3d-117">要素</span><span class="sxs-lookup"><span data-stu-id="bef3d-117">Element</span></span>|<span data-ttu-id="bef3d-118">説明</span><span class="sxs-lookup"><span data-stu-id="bef3d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="bef3d-119">セキュリティトークンハンドラーのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="bef3d-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bef3d-120">解説</span><span class="sxs-lookup"><span data-stu-id="bef3d-120">Remarks</span></span>  

 <span data-ttu-id="bef3d-121">発行者トークンリゾルバーは、受信トークンとメッセージの署名トークンを解決するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bef3d-121">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="bef3d-122">署名の確認に使用される暗号化マテリアルを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bef3d-122">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="bef3d-123">属性を指定する必要があり `type` ます。</span><span class="sxs-lookup"><span data-stu-id="bef3d-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="bef3d-124">指定できる型は、 <xref:System.IdentityModel.Tokens.IssuerTokenResolver> またはクラスから派生したカスタム型のいずれか <xref:System.IdentityModel.Tokens.IssuerTokenResolver> です。</span><span class="sxs-lookup"><span data-stu-id="bef3d-124">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="bef3d-125">一部のトークンハンドラーでは、構成で発行者トークンリゾルバーの設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bef3d-125">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="bef3d-126">個々のトークンハンドラーの設定は、セキュリティトークンハンドラーコレクションで指定された設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="bef3d-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bef3d-127">要素 `<issuerTokenResolver>` の子要素としての指定 [\<identityConfiguration>](identityconfiguration.md) は非推奨とされましたが、旧バージョンとの互換性のために引き続きサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bef3d-127">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="bef3d-128">要素の設定は、要素の設定 `<securityTokenHandlerConfiguration>` よりも優先さ `<identityConfiguration>` れます。</span><span class="sxs-lookup"><span data-stu-id="bef3d-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bef3d-129">例</span><span class="sxs-lookup"><span data-stu-id="bef3d-129">Example</span></span>  

 <span data-ttu-id="bef3d-130">次の XML は、から派生したカスタムクラスに基づく発行者トークンリゾルバーの構成を示して <xref:System.IdentityModel.Tokens.IssuerTokenResolver> います。</span><span class="sxs-lookup"><span data-stu-id="bef3d-130">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="bef3d-131">トークンリゾルバーは、 `<AddAudienceKeyPair>` クラスに対して定義されているカスタム構成要素 () から初期化される、ユーザーとキーのペアのディクショナリを保持します。</span><span class="sxs-lookup"><span data-stu-id="bef3d-131">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="bef3d-132">クラスは、メソッドをオーバーライドして <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> この要素を処理します。</span><span class="sxs-lookup"><span data-stu-id="bef3d-132">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="bef3d-133">オーバーライドを次の例に示します。ただし、簡潔にするために呼び出すメソッドは表示されません。</span><span class="sxs-lookup"><span data-stu-id="bef3d-133">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="bef3d-134">完全な例については、「」のサンプルを参照してください `CustomToken` 。</span><span class="sxs-lookup"><span data-stu-id="bef3d-134">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="bef3d-135">例</span><span class="sxs-lookup"><span data-stu-id="bef3d-135">Example</span></span>
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="bef3d-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="bef3d-136">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
