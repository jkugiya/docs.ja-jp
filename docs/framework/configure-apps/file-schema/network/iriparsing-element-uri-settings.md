---
description: '詳細情報: <iriParsing> 要素 (Uri 設定)'
title: <iriParsing> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 460216b64056cd9c9f769c5bcd1b651d249e98b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740302"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="d4789-103">\<iriParsing> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="d4789-103">\<iriParsing> Element (Uri Settings)</span></span>

<span data-ttu-id="d4789-104">International Resource Identifier (IRI) 解析が、<xref:System.Uri> に適用されるかどうか、および IRI の解析規則が適用されるどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4789-104">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a><span data-ttu-id="d4789-105">構文</span><span class="sxs-lookup"><span data-stu-id="d4789-105">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4789-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d4789-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d4789-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4789-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4789-108">属性</span><span class="sxs-lookup"><span data-stu-id="d4789-108">Attributes</span></span>  
  
|<span data-ttu-id="d4789-109">**要素**</span><span class="sxs-lookup"><span data-stu-id="d4789-109">**Element**</span></span>|<span data-ttu-id="d4789-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="d4789-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="d4789-111">IRI 解析を有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4789-111">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="d4789-112">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="d4789-112">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4789-113">子要素</span><span class="sxs-lookup"><span data-stu-id="d4789-113">Child Elements</span></span>  

 <span data-ttu-id="d4789-114">なし</span><span class="sxs-lookup"><span data-stu-id="d4789-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4789-115">親要素</span><span class="sxs-lookup"><span data-stu-id="d4789-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d4789-116">**要素**</span><span class="sxs-lookup"><span data-stu-id="d4789-116">**Element**</span></span>|<span data-ttu-id="d4789-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="d4789-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d4789-118">uri</span><span class="sxs-lookup"><span data-stu-id="d4789-118">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="d4789-119">.NET Framework が、uniform resource identifier (Uri) を使用して表された web アドレスを処理する方法を指定する設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d4789-119">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4789-120">解説</span><span class="sxs-lookup"><span data-stu-id="d4789-120">Remarks</span></span>  

 <span data-ttu-id="d4789-121">既存の <xref:System.Uri> クラスは .NET Framework 3.5 で拡張されています。</span><span class="sxs-lookup"><span data-stu-id="d4789-121">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="d4789-122">3.0 SP1 および 2.0 SP1 では、International Resource Identifier (IRI) と国際化ドメイン名 (IDN) のサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d4789-122">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="d4789-123">現在のユーザーには、IRI と IDN のサポートを明示的に有効にしない限り、.NET Framework 2.0 の動作からの変更は表示されません。</span><span class="sxs-lookup"><span data-stu-id="d4789-123">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="d4789-124">これにより、.NET Framework の以前のバージョンとのアプリケーションの互換性を保証します。</span><span class="sxs-lookup"><span data-stu-id="d4789-124">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d4789-125">IRI のサポートを有効にするには、次の2つの変更が必要です。</span><span class="sxs-lookup"><span data-stu-id="d4789-125">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="d4789-126">.NET Framework 2.0 ディレクトリの下にある machine.config ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="d4789-126">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="d4789-127">IRI 解析規則を適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4789-127">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="d4789-128">これは、machine.config ファイルまたは app.config ファイルで指定できます。</span><span class="sxs-lookup"><span data-stu-id="d4789-128">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="d4789-129">IRI 解析を有効にすると (iriParsing 有効 = `true` )、RFC 3987 の最新の IRI 規則に従って、正規化と文字チェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="d4789-129">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="d4789-130">既定値はで、 `false` rfc 2396 および rfc 3986 (IPv6 リテラルの場合) に従って、正規化と文字チェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="d4789-130">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="d4789-131">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="d4789-131">Configuration Files</span></span>  

 <span data-ttu-id="d4789-132">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4789-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4789-133">例</span><span class="sxs-lookup"><span data-stu-id="d4789-133">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d4789-134">説明</span><span class="sxs-lookup"><span data-stu-id="d4789-134">Description</span></span>  

 <span data-ttu-id="d4789-135">次の例は、 <xref:System.Uri> IRI 解析と IDN 名をサポートするためにクラスによって使用される構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="d4789-135">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d4789-136">コード</span><span class="sxs-lookup"><span data-stu-id="d4789-136">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4789-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4789-137">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="d4789-138">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="d4789-138">Network Settings Schema</span></span>](index.md)
