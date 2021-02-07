---
description: 詳細については <add> 、 <protocolMapping>
title: <add> の <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 530ef6b2893eb55a979aba2ef7ec21efffc3070a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750248"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="7427a-103">\<add> の \<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="7427a-103">\<add> of \<protocolMapping></span></span>

<span data-ttu-id="7427a-104">トランスポートプロトコルスキーム (http、net.tcp、net.pipe など) と Windows Communication Foundation (WCF) バインドとの間の既定のプロトコルマッピングを表します。</span><span class="sxs-lookup"><span data-stu-id="7427a-104">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="7427a-105">実行時に既定のエンドポイントを作成する場合、WCF は構成されたマッピングを調べ、特定のベースアドレスに使用するバインドを決定します。</span><span class="sxs-lookup"><span data-stu-id="7427a-105">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="7427a-106">構文</span><span class="sxs-lookup"><span data-stu-id="7427a-106">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7427a-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7427a-107">Attributes and Elements</span></span>  

 <span data-ttu-id="7427a-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7427a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7427a-109">属性</span><span class="sxs-lookup"><span data-stu-id="7427a-109">Attributes</span></span>  
  
|<span data-ttu-id="7427a-110">要素</span><span class="sxs-lookup"><span data-stu-id="7427a-110">Element</span></span>|<span data-ttu-id="7427a-111">説明</span><span class="sxs-lookup"><span data-stu-id="7427a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7427a-112">binding</span><span class="sxs-lookup"><span data-stu-id="7427a-112">binding</span></span>|<span data-ttu-id="7427a-113">既定のエンドポイントを作成するときにエンドポイントに使用されるバインディングの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="7427a-113">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="7427a-114">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="7427a-114">bindingConfiguration</span></span>|<span data-ttu-id="7427a-115">参照されるバインディング構成セクションの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="7427a-115">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="7427a-116">scheme</span><span class="sxs-lookup"><span data-stu-id="7427a-116">scheme</span></span>|<span data-ttu-id="7427a-117">既定のエンドポイントに使用されるトランスポート プロトコル スキーム。</span><span class="sxs-lookup"><span data-stu-id="7427a-117">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7427a-118">子要素</span><span class="sxs-lookup"><span data-stu-id="7427a-118">Child Elements</span></span>  

 <span data-ttu-id="7427a-119">なし。</span><span class="sxs-lookup"><span data-stu-id="7427a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7427a-120">親要素</span><span class="sxs-lookup"><span data-stu-id="7427a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7427a-121">要素</span><span class="sxs-lookup"><span data-stu-id="7427a-121">Element</span></span>|<span data-ttu-id="7427a-122">説明</span><span class="sxs-lookup"><span data-stu-id="7427a-122">Description</span></span>|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="7427a-123">トランスポートプロトコルスキーム (http、net.tcp、net.pipe など) と Windows Communication Foundation (WCF) バインド間の既定のプロトコルマッピングを定義するための構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="7427a-123">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7427a-124">例</span><span class="sxs-lookup"><span data-stu-id="7427a-124">Example</span></span>  

 <span data-ttu-id="7427a-125">次の構成例は、machine.config ファイル内の既定のプロトコル マッピングを示しています。</span><span class="sxs-lookup"><span data-stu-id="7427a-125">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="7427a-126">machine.config ファイルを変更することで、既定のマッピングをコンピューター レベルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="7427a-126">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="7427a-127">または、アプリケーションのスコープ内だけでオーバーライドする場合は、アプリケーション構成ファイルのこのセクションをオーバーライドし、各プロトコル スキームのマッピングを変更できます。</span><span class="sxs-lookup"><span data-stu-id="7427a-127">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="7427a-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="7427a-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
