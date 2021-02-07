---
description: '詳細情報: <add> schemeSettings の要素 (Uri 設定)'
title: schemeSettings の <add> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: c372577af1c7fbfe669455b50c8b55c82da4fc52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698622"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="08fe7-103">schemeSettings の \<add> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="08fe7-103">\<add> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="08fe7-104">スキーム名のスキーム設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="08fe7-104">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="08fe7-105">構文</span><span class="sxs-lookup"><span data-stu-id="08fe7-105">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08fe7-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="08fe7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="08fe7-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="08fe7-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08fe7-108">属性</span><span class="sxs-lookup"><span data-stu-id="08fe7-108">Attributes</span></span>  
  
|<span data-ttu-id="08fe7-109">属性</span><span class="sxs-lookup"><span data-stu-id="08fe7-109">Attribute</span></span>|<span data-ttu-id="08fe7-110">説明</span><span class="sxs-lookup"><span data-stu-id="08fe7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08fe7-111">name</span><span class="sxs-lookup"><span data-stu-id="08fe7-111">name</span></span>|<span data-ttu-id="08fe7-112">この設定を適用するスキーム名。</span><span class="sxs-lookup"><span data-stu-id="08fe7-112">The scheme name for which this setting applies.</span></span> <span data-ttu-id="08fe7-113">サポートされている値は、name = "http" と name = "https" だけです。</span><span class="sxs-lookup"><span data-stu-id="08fe7-113">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="08fe7-114">{属性名}属性</span><span class="sxs-lookup"><span data-stu-id="08fe7-114">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="08fe7-115">値</span><span class="sxs-lookup"><span data-stu-id="08fe7-115">Value</span></span>|<span data-ttu-id="08fe7-116">説明</span><span class="sxs-lookup"><span data-stu-id="08fe7-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08fe7-117">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="08fe7-117">genericUriParserOptions</span></span>|<span data-ttu-id="08fe7-118">このスキームのパーサーオプション。</span><span class="sxs-lookup"><span data-stu-id="08fe7-118">The parser options for this scheme.</span></span> <span data-ttu-id="08fe7-119">サポートされている値は、genericUriParserOptions = "DontUnescapePathDotsAndSlashes" だけです。</span><span class="sxs-lookup"><span data-stu-id="08fe7-119">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08fe7-120">子要素</span><span class="sxs-lookup"><span data-stu-id="08fe7-120">Child Elements</span></span>  

 <span data-ttu-id="08fe7-121">なし</span><span class="sxs-lookup"><span data-stu-id="08fe7-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08fe7-122">親要素</span><span class="sxs-lookup"><span data-stu-id="08fe7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="08fe7-123">要素</span><span class="sxs-lookup"><span data-stu-id="08fe7-123">Element</span></span>|<span data-ttu-id="08fe7-124">説明</span><span class="sxs-lookup"><span data-stu-id="08fe7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08fe7-125">\<schemeSettings> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="08fe7-125">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="08fe7-126"><xref:System.Uri> が特定のスキームに解析される方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="08fe7-126">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08fe7-127">解説</span><span class="sxs-lookup"><span data-stu-id="08fe7-127">Remarks</span></span>  

 <span data-ttu-id="08fe7-128">既定では、 <xref:System.Uri?displayProperty=nameWithType> クラスは、パスの圧縮を実行する前に、エンコードされたパス区切り記号のエスケープを解除します。</span><span class="sxs-lookup"><span data-stu-id="08fe7-128">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="08fe7-129">これは、次のような攻撃に対するセキュリティメカニズムとして実装されています。</span><span class="sxs-lookup"><span data-stu-id="08fe7-129">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="08fe7-130">% Encoded 文字を正しく処理しないモジュールにこの URI が渡された場合、サーバーによって次のコマンドが実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="08fe7-130">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="08fe7-131">このため、 <xref:System.Uri?displayProperty=nameWithType> クラスはまずパスの区切り記号をエスケープ解除し、次にパスの圧縮を適用します。</span><span class="sxs-lookup"><span data-stu-id="08fe7-131">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="08fe7-132">上の悪意のある URL をクラスコンストラクターに渡すと、次の URI が生成され <xref:System.Uri?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="08fe7-132">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="08fe7-133">この既定の動作は、特定のスキームの schemeSettings 構成オプションを使用して、パーセントエンコードされたパス区切り記号のエスケープを解除しないように変更できます。</span><span class="sxs-lookup"><span data-stu-id="08fe7-133">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="08fe7-134">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="08fe7-134">Configuration Files</span></span>  

 <span data-ttu-id="08fe7-135">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="08fe7-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08fe7-136">例</span><span class="sxs-lookup"><span data-stu-id="08fe7-136">Example</span></span>  

 <span data-ttu-id="08fe7-137">次の例は、 <xref:System.Uri> http スキームに対してパーセントでエンコードされたパス区切り記号をエスケープしないようにするために、クラスによって使用される構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="08fe7-137">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08fe7-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="08fe7-138">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="08fe7-139">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="08fe7-139">Network Settings Schema</span></span>](index.md)
