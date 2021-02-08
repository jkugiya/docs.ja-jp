---
description: '詳細情報: <idn> 要素 (Uri 設定)'
title: <idn> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: a53afd59b713a804d5b969521f468000dbbad6e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802477"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="ebcee-103">\<idn> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="ebcee-103">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="ebcee-104">国際化ドメイン名 (IDN) の解析がドメイン名に適用されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ebcee-104">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**  
  
## <a name="syntax"></a><span data-ttu-id="ebcee-105">構文</span><span class="sxs-lookup"><span data-stu-id="ebcee-105">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebcee-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ebcee-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ebcee-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebcee-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebcee-108">属性</span><span class="sxs-lookup"><span data-stu-id="ebcee-108">Attributes</span></span>  

|<span data-ttu-id="ebcee-109">**要素**</span><span class="sxs-lookup"><span data-stu-id="ebcee-109">**Element**</span></span>|<span data-ttu-id="ebcee-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="ebcee-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="ebcee-111">国際化ドメイン名 (IDN) の解析がドメイン名に適用されるかどうかを指定します。既定値は none です。</span><span class="sxs-lookup"><span data-stu-id="ebcee-111">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="ebcee-112">子要素</span><span class="sxs-lookup"><span data-stu-id="ebcee-112">Child elements</span></span>

<span data-ttu-id="ebcee-113">なし</span><span class="sxs-lookup"><span data-stu-id="ebcee-113">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="ebcee-114">親要素</span><span class="sxs-lookup"><span data-stu-id="ebcee-114">Parent elements</span></span>

|<span data-ttu-id="ebcee-115">**要素**</span><span class="sxs-lookup"><span data-stu-id="ebcee-115">**Element**</span></span>|<span data-ttu-id="ebcee-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="ebcee-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ebcee-117">uri</span><span class="sxs-lookup"><span data-stu-id="ebcee-117">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="ebcee-118">.NET Framework が、uniform resource identifier (Uri) を使用して表された web アドレスを処理する方法を指定する設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ebcee-118">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="ebcee-119">解説</span><span class="sxs-lookup"><span data-stu-id="ebcee-119">Remarks</span></span>

<span data-ttu-id="ebcee-120">既存の <xref:System.Uri> クラスは .NET Framework 3.5 で拡張されています。</span><span class="sxs-lookup"><span data-stu-id="ebcee-120">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="ebcee-121">3.0 SP1 および 2.0 SP1 (国際リソース識別子 (IRI) と国際化ドメイン名 (IDN) をサポート)。</span><span class="sxs-lookup"><span data-stu-id="ebcee-121">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="ebcee-122">現在のユーザーには、IRI と IDN のサポートを明示的に有効にしない限り、.NET Framework 2.0 の動作からの変更は表示されません。</span><span class="sxs-lookup"><span data-stu-id="ebcee-122">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="ebcee-123">これにより、.NET Framework の以前のバージョンとのアプリケーションの互換性を保証します。</span><span class="sxs-lookup"><span data-stu-id="ebcee-123">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="ebcee-124">IRI のサポートを有効にするには、次の2つの変更が必要です。</span><span class="sxs-lookup"><span data-stu-id="ebcee-124">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="ebcee-125">次の行を、.NET Framework 2.0 ディレクトリの下の machine.config ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="ebcee-125">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="ebcee-126">国際化ドメイン名 (IDN) の解析をドメイン名に適用するかどうか、および IRI 解析規則を適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ebcee-126">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="ebcee-127">これは、machine.config ファイルまたは app.config ファイルで指定できます。</span><span class="sxs-lookup"><span data-stu-id="ebcee-127">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="ebcee-128">IDN には、使用する DNS サーバーに応じて、次の3つの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ebcee-128">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="ebcee-129">idn enabled = すべて</span><span class="sxs-lookup"><span data-stu-id="ebcee-129">idn enabled = All</span></span>  

     <span data-ttu-id="ebcee-130">この値は、Unicode のドメイン名があれば、それを等価の Punycode (IDN 名) に変換します。</span><span class="sxs-lookup"><span data-stu-id="ebcee-130">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="ebcee-131">idn enabled = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="ebcee-131">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="ebcee-132">この値を指定すると、ローカルイントラネット上にないすべての Unicode ドメイン名が、Punycode に相当する (IDN 名) を使用するように変換されます。</span><span class="sxs-lookup"><span data-stu-id="ebcee-132">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="ebcee-133">この場合は、イントラネットで使用される DNS サーバーが Unicode 名前解決をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebcee-133">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="ebcee-134">idn enabled = なし</span><span class="sxs-lookup"><span data-stu-id="ebcee-134">idn enabled = None</span></span>

     <span data-ttu-id="ebcee-135">この値は、どの Unicode のドメイン名も、Punycode を使用するように変換しません。</span><span class="sxs-lookup"><span data-stu-id="ebcee-135">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="ebcee-136">これは、.NET Framework 2.0 の動作と一貫した既定値です。</span><span class="sxs-lookup"><span data-stu-id="ebcee-136">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="ebcee-137">IDN を有効にすると、ドメイン名に含まれるすべての Unicode のラベルが Punycode のラベルに変換されます。</span><span class="sxs-lookup"><span data-stu-id="ebcee-137">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="ebcee-138">Punycode 名には ASCII 文字のみが含まれ、常に xn-- プレフィックスで始まります。</span><span class="sxs-lookup"><span data-stu-id="ebcee-138">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="ebcee-139">この理由は、ほとんどの DNS サーバーは ASCII 文字しかサポートしていないため、インターネットで既存の DNS サーバーをサポートするためです (RFC 3940 を参照)。</span><span class="sxs-lookup"><span data-stu-id="ebcee-139">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="ebcee-140">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="ebcee-140">Configuration files</span></span>

<span data-ttu-id="ebcee-141">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ebcee-141">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="ebcee-142">例</span><span class="sxs-lookup"><span data-stu-id="ebcee-142">Example</span></span>

<span data-ttu-id="ebcee-143">次の例は、 <xref:System.Uri> IRI 解析と IDN 名をサポートするためにクラスによって使用される構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="ebcee-143">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ebcee-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebcee-144">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="ebcee-145">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="ebcee-145">Network Settings Schema</span></span>](index.md)
