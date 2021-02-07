---
description: '詳細情報: <wsdlImporter>'
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 9f95d4e6b940f36e9142eb9865327c772e3ce4db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682151"
---
# \<wsdlImporter>

<span data-ttu-id="c5008-102">WS-Policy が添付された Web サービス記述言語 (WSDL) 1.1 メタデータをインポートするすべての WSDL インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="c5008-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="c5008-103">構文</span><span class="sxs-lookup"><span data-stu-id="c5008-103">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5008-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c5008-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c5008-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5008-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5008-106">属性</span><span class="sxs-lookup"><span data-stu-id="c5008-106">Attributes</span></span>  
  
|<span data-ttu-id="c5008-107">属性</span><span class="sxs-lookup"><span data-stu-id="c5008-107">Attribute</span></span>|<span data-ttu-id="c5008-108">説明</span><span class="sxs-lookup"><span data-stu-id="c5008-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c5008-109">この要素の型です。</span><span class="sxs-lookup"><span data-stu-id="c5008-109">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5008-110">子要素</span><span class="sxs-lookup"><span data-stu-id="c5008-110">Child Elements</span></span>  

 <span data-ttu-id="c5008-111">なし。</span><span class="sxs-lookup"><span data-stu-id="c5008-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5008-112">親要素</span><span class="sxs-lookup"><span data-stu-id="c5008-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c5008-113">要素</span><span class="sxs-lookup"><span data-stu-id="c5008-113">Element</span></span>|<span data-ttu-id="c5008-114">説明</span><span class="sxs-lookup"><span data-stu-id="c5008-114">Description</span></span>|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="c5008-115">WS-Policy が添付された Web サービス記述言語 (WSDL) 1.1 メタデータをインポートするすべての WSDL インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="c5008-115">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5008-116">解説</span><span class="sxs-lookup"><span data-stu-id="c5008-116">Remarks</span></span>  

 <span data-ttu-id="c5008-117">WSDL インポーターは、メタデータのインポートに加えて、コントラクトおよびエンドポイント情報を表すさまざまなクラスにその情報を変換するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c5008-117">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="c5008-118">コントラクトおよびエンドポイントの情報やプロパティを選択的にインポートできます。これらは、任意のインポート エラーを公開し、インポートおよび変換プロセスに関連する型情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c5008-118">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="c5008-119">また、任意のポリシー ドキュメント、WSDL ドキュメント、WSDL 拡張、および XML スキーマ ドキュメントにアクセスするためのバインディング情報およびプロパティのインポートもサポートします。</span><span class="sxs-lookup"><span data-stu-id="c5008-119">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5008-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5008-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="c5008-121">WCF クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="c5008-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="c5008-122">クライアント</span><span class="sxs-lookup"><span data-stu-id="c5008-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
