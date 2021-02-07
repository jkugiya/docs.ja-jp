---
description: '詳細情報: <userNameAuthentication>'
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 0edd92ba343ec38207d60c99616058d0b28f045b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664445"
---
# \<userNameAuthentication>

<span data-ttu-id="e9af2-102">ユーザー名とパスワードに基づいてサービスの資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9af2-102">Specifies a service's credentials based on user name and password.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="e9af2-103">構文</span><span class="sxs-lookup"><span data-stu-id="e9af2-103">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9af2-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e9af2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e9af2-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9af2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9af2-106">属性</span><span class="sxs-lookup"><span data-stu-id="e9af2-106">Attributes</span></span>  
  
|<span data-ttu-id="e9af2-107">属性</span><span class="sxs-lookup"><span data-stu-id="e9af2-107">Attribute</span></span>|<span data-ttu-id="e9af2-108">説明</span><span class="sxs-lookup"><span data-stu-id="e9af2-108">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="e9af2-109">トークンがキャッシュ内に保持される最大時間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="e9af2-109">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="e9af2-110">既定値は 00:15:00 です。</span><span class="sxs-lookup"><span data-stu-id="e9af2-110">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="e9af2-111">ログオン トークンがキャッシュされるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="e9af2-111">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="e9af2-112">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="e9af2-112">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="e9af2-113">使用されるカスタム ユーザー名およびパスワード検証の種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="e9af2-113">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="e9af2-114">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="e9af2-114">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="e9af2-115">セキュリティ コンテキストに Windows グループが含まれるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="e9af2-115">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="e9af2-116">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="e9af2-116">The default is `true`.</span></span><br /><br /> <span data-ttu-id="e9af2-117">この属性を `true` に設定すると、グループ全体が拡張されるため、パフォーマンスに影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="e9af2-117">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="e9af2-118">ユーザーが属するグループの一覧を生成する必要がない場合は、このプロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="e9af2-118">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="e9af2-119">キャッシュするログオン トークンの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="e9af2-119">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="e9af2-120">この値は、ゼロより大きい値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9af2-120">This value should be larger than zero.</span></span> <span data-ttu-id="e9af2-121">既定値は 128 です。</span><span class="sxs-lookup"><span data-stu-id="e9af2-121">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="e9af2-122">バインディングの `clientCredentialType` 属性が `username` に設定されている場合、ユーザー名は Windows アカウントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="e9af2-122">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="e9af2-123">関連するパスワード検証機構を提供する <xref:System.Web.Security.MembershipProvider> 値の名前を含む文字列であるこの属性を使用して動作をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="e9af2-123">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="e9af2-124">ユーザー名とパスワードを検証する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9af2-124">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="e9af2-125">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e9af2-125">Valid values are:</span></span><br /><br /> <span data-ttu-id="e9af2-126">-Windows</span><span class="sxs-lookup"><span data-stu-id="e9af2-126">-   Windows</span></span><br /><span data-ttu-id="e9af2-127">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="e9af2-127">-   MembershipProvider</span></span><br /><span data-ttu-id="e9af2-128">-カスタム</span><span class="sxs-lookup"><span data-stu-id="e9af2-128">-   Custom</span></span><br /><br /> <span data-ttu-id="e9af2-129">既定は Windows です。</span><span class="sxs-lookup"><span data-stu-id="e9af2-129">The default is Windows.</span></span> <span data-ttu-id="e9af2-130">この属性は <xref:System.ServiceModel.Security.UserNamePasswordValidationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="e9af2-130">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9af2-131">子要素</span><span class="sxs-lookup"><span data-stu-id="e9af2-131">Child Elements</span></span>  

 <span data-ttu-id="e9af2-132">なし。</span><span class="sxs-lookup"><span data-stu-id="e9af2-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9af2-133">親要素</span><span class="sxs-lookup"><span data-stu-id="e9af2-133">Parent Elements</span></span>  
  
|<span data-ttu-id="e9af2-134">要素</span><span class="sxs-lookup"><span data-stu-id="e9af2-134">Element</span></span>|<span data-ttu-id="e9af2-135">説明</span><span class="sxs-lookup"><span data-stu-id="e9af2-135">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="e9af2-136">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9af2-136">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9af2-137">解説</span><span class="sxs-lookup"><span data-stu-id="e9af2-137">Remarks</span></span>  

 <span data-ttu-id="e9af2-138">サービスで使用されるバインディングがユーザー名とパスワード ベースの認証を使用するように構成されていない場合、この要素の属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="e9af2-138">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="e9af2-139">これには、`customUserNamePasswordValidatorType`、`includeWindowsGroups`、`membershipProviderName`、および `userNamePasswordValidationMode` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e9af2-139">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="e9af2-140">サービスで使用されるバインディングが Windows 認証のユーザー名とパスワードを使用するように構成されていない場合、ログオン トークンのキャッシュに関連する設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="e9af2-140">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="e9af2-141">これには、`cacheLogonTokenLifetime`、`cacheLogonTokens`、および `maxCacheLogonTokens`、が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e9af2-141">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9af2-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9af2-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
