---
description: 詳細については <windowsAuthentication> 、 <serviceCredentials>
title: <windowsAuthentication> の <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 94f5804ac22a8c3ee1b8fc646ece8521ff639aec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682411"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="9b254-103">\<windowsAuthentication> の \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9b254-103">\<windowsAuthentication> of \<serviceCredentials></span></span>

<span data-ttu-id="9b254-104">Windows サービス資格情報の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b254-104">Specifies the settings of a Windows service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="9b254-105">構文</span><span class="sxs-lookup"><span data-stu-id="9b254-105">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b254-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9b254-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9b254-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b254-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b254-108">属性</span><span class="sxs-lookup"><span data-stu-id="9b254-108">Attributes</span></span>  
  
|<span data-ttu-id="9b254-109">属性</span><span class="sxs-lookup"><span data-stu-id="9b254-109">Attribute</span></span>|<span data-ttu-id="9b254-110">説明</span><span class="sxs-lookup"><span data-stu-id="9b254-110">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="9b254-111">セキュリティ コンテキストに Windows グループが含まれるかどうかを指定する省略可能なブール属性。</span><span class="sxs-lookup"><span data-stu-id="9b254-111">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="9b254-112">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="9b254-112">The default is `true`.</span></span><br /><br /> <span data-ttu-id="9b254-113">この属性を `true` に設定すると、グループ全体が拡張されるため、パフォーマンスに影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="9b254-113">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="9b254-114">ユーザーが属するグループの一覧を生成する必要がない場合は、この属性を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b254-114">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="9b254-115">認証されていない匿名の呼び出し元を許可するかどうかを指定する省略可能なブール属性。</span><span class="sxs-lookup"><span data-stu-id="9b254-115">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="9b254-116">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="9b254-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="9b254-117">バインディングの `clientCredentialType` 属性が `Windows` に設定されている場合、匿名の呼び出し元は許可されません。</span><span class="sxs-lookup"><span data-stu-id="9b254-117">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="9b254-118">これは、ドメインまたはワークグループの認証済み呼び出し元だけがシステムへのアクセスを許可されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="9b254-118">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="9b254-119">この動作は、この属性を使用してオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="9b254-119">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="9b254-120">この設定を使用するときは十分に注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b254-120">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b254-121">子要素</span><span class="sxs-lookup"><span data-stu-id="9b254-121">Child Elements</span></span>  

 <span data-ttu-id="9b254-122">なし。</span><span class="sxs-lookup"><span data-stu-id="9b254-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b254-123">親要素</span><span class="sxs-lookup"><span data-stu-id="9b254-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9b254-124">要素</span><span class="sxs-lookup"><span data-stu-id="9b254-124">Element</span></span>|<span data-ttu-id="9b254-125">説明</span><span class="sxs-lookup"><span data-stu-id="9b254-125">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="9b254-126">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b254-126">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b254-127">解説</span><span class="sxs-lookup"><span data-stu-id="9b254-127">Remarks</span></span>  

 <span data-ttu-id="9b254-128">匿名の Windows ユーザーのアクセスを許可するかどうかを指定するには、この要素を使用して、`allowAnonymousLogons` 属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="9b254-128">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="9b254-129">また、`includeWindowsGroups` 属性を設定すると、ユーザーが属するグループの情報を AuthorizationContext に含めるかどうかも指定できます。</span><span class="sxs-lookup"><span data-stu-id="9b254-129">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="9b254-130">この属性が `true` (既定値) に設定されている場合、サービスはクライアントが属している Windows グループを特定できます。</span><span class="sxs-lookup"><span data-stu-id="9b254-130">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b254-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b254-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
