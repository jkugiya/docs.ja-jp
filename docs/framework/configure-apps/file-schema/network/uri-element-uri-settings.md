---
description: '詳細情報: <uri> 要素 (Uri 設定)'
title: <uri> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: dc30778fdf5babfb87da0e32829ed9a3ae412c2e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740120"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="fbbb6-103">\<uri> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="fbbb6-103">\<uri> Element (Uri Settings)</span></span>

<span data-ttu-id="fbbb6-104">.NET Framework が、uniform resource identifier (Uri) を使用して表された web アドレスを処理する方法を指定する設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-104">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="fbbb6-105">構文</span><span class="sxs-lookup"><span data-stu-id="fbbb6-105">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbbb6-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fbbb6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fbbb6-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbbb6-108">属性</span><span class="sxs-lookup"><span data-stu-id="fbbb6-108">Attributes</span></span>  

 <span data-ttu-id="fbbb6-109">なし。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fbbb6-110">子要素</span><span class="sxs-lookup"><span data-stu-id="fbbb6-110">Child Elements</span></span>  
  
|<span data-ttu-id="fbbb6-111">**要素**</span><span class="sxs-lookup"><span data-stu-id="fbbb6-111">**Element**</span></span>|<span data-ttu-id="fbbb6-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="fbbb6-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fbbb6-113">idn</span><span class="sxs-lookup"><span data-stu-id="fbbb6-113">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="fbbb6-114">国際化ドメイン名 (IDN) の解析がドメイン名に適用されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="fbbb6-115">Iriparsing></span><span class="sxs-lookup"><span data-stu-id="fbbb6-115">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="fbbb6-116">国際化リソース識別子 (IRI) の解析を適用する <xref:System.Uri> かどうか、および iri 解析規則を適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-116">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="fbbb6-117">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="fbbb6-117">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="fbbb6-118"><xref:System.Uri> が特定のスキームに解析される方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-118">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbbb6-119">親要素</span><span class="sxs-lookup"><span data-stu-id="fbbb6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fbbb6-120">**要素**</span><span class="sxs-lookup"><span data-stu-id="fbbb6-120">**Element**</span></span>|<span data-ttu-id="fbbb6-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="fbbb6-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fbbb6-122">configuration</span><span class="sxs-lookup"><span data-stu-id="fbbb6-122">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="fbbb6-123">すべての名前空間の設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-123">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbbb6-124">解説</span><span class="sxs-lookup"><span data-stu-id="fbbb6-124">Remarks</span></span>  

 <span data-ttu-id="fbbb6-125">要素には、 `uri` <xref:System.Uri> 名前空間のクラスによって使用されるクラスのメンバーの設定が含まれ <xref:System.Net> ます。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-125">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="fbbb6-126">この設定により、IRI と IDN のサポートが構成されます。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-126">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbbb6-127">例</span><span class="sxs-lookup"><span data-stu-id="fbbb6-127">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fbbb6-128">説明</span><span class="sxs-lookup"><span data-stu-id="fbbb6-128">Description</span></span>  

 <span data-ttu-id="fbbb6-129">次の例は、 <xref:System.Uri> IRI 解析と IDN 名をサポートするためにクラスによって使用される構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-129">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="fbbb6-130">また、この例では、すべてのスキーム設定をクリアした後、http スキームに対してパーセントでエンコードされたパス区切り記号をエスケープしないためのサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="fbbb6-130">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fbbb6-131">コード</span><span class="sxs-lookup"><span data-stu-id="fbbb6-131">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbbb6-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbbb6-132">See also</span></span>

- [<span data-ttu-id="fbbb6-133">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="fbbb6-133">Network Settings Schema</span></span>](index.md)
