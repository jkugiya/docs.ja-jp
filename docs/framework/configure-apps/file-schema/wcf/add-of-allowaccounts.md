---
description: 詳細については <add> 、 <allowAccounts>
title: <add> の <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 275631c4467a888966e89a2f664b186f989ae101
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782222"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="5a18a-103">\<add> の \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="5a18a-103">\<add> of \<allowAccounts></span></span>

<span data-ttu-id="5a18a-104">WCF サービスをホストし、共有サービスへの接続アクセスが許可されているプロセスのユーザーアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a18a-104">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="5a18a-105">構文</span><span class="sxs-lookup"><span data-stu-id="5a18a-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a18a-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5a18a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5a18a-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a18a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a18a-108">属性</span><span class="sxs-lookup"><span data-stu-id="5a18a-108">Attributes</span></span>  
  
|<span data-ttu-id="5a18a-109">属性</span><span class="sxs-lookup"><span data-stu-id="5a18a-109">Attribute</span></span>|<span data-ttu-id="5a18a-110">説明</span><span class="sxs-lookup"><span data-stu-id="5a18a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a18a-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="5a18a-111">securityIdentifier</span></span>|<span data-ttu-id="5a18a-112">ユーザー アカウントの識別に使用される一意の識別子を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="5a18a-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="5a18a-113">既定値は LocalSystem、Administrators、NS、LS、および IIS_USRS です。</span><span class="sxs-lookup"><span data-stu-id="5a18a-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a18a-114">子要素</span><span class="sxs-lookup"><span data-stu-id="5a18a-114">Child Elements</span></span>  

 <span data-ttu-id="5a18a-115">なし。</span><span class="sxs-lookup"><span data-stu-id="5a18a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a18a-116">親要素</span><span class="sxs-lookup"><span data-stu-id="5a18a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5a18a-117">要素</span><span class="sxs-lookup"><span data-stu-id="5a18a-117">Element</span></span>|<span data-ttu-id="5a18a-118">説明</span><span class="sxs-lookup"><span data-stu-id="5a18a-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="5a18a-119">`securityIdentifier`WCF サービスをホストするプロセスのユーザーアカウントを指定する属性を含む構成要素のコレクション。共有サービスへの接続アクセス権が付与されます。</span><span class="sxs-lookup"><span data-stu-id="5a18a-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5a18a-120">例</span><span class="sxs-lookup"><span data-stu-id="5a18a-120">Example</span></span>  

 <span data-ttu-id="5a18a-121">次の構成例は、このコレクションにユーザー アカウントの 5 つの既定の識別子を追加します。</span><span class="sxs-lookup"><span data-stu-id="5a18a-121">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>
  <!-- LocalSystem account -->
  <add securityIdentifier="S-1-5-18" />
  <!-- LocalService account -->
  <add securityIdentifier="S-1-5-19" />
  <!-- Administrators account -->
  <add securityIdentifier="S-1-5-20" />
  <!-- Network Service account -->
  <add securityIdentifier="S-1-5-32-544" />
  <!-- IIS_IUSRS account (Vista only) -->
  <add securityIdentifier="S-1-5-32-568" />
</allowAccounts>
```  
  
## <a name="see-also"></a><span data-ttu-id="5a18a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a18a-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
