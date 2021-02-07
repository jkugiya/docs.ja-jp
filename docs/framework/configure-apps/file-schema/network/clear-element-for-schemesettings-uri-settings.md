---
description: '詳細情報: <clear> schemeSettings の要素 (Uri 設定)'
title: schemeSettings の <clear> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 719296285c9a7da26eb6eaf16c630a63a10698b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740458"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="de377-103">schemeSettings の \<clear> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="de377-103">\<clear> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="de377-104">既存のスキーム設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="de377-104">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="de377-105">構文</span><span class="sxs-lookup"><span data-stu-id="de377-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de377-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="de377-106">Attributes and Elements</span></span>  

 <span data-ttu-id="de377-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="de377-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de377-108">属性</span><span class="sxs-lookup"><span data-stu-id="de377-108">Attributes</span></span>  

 <span data-ttu-id="de377-109">なし。</span><span class="sxs-lookup"><span data-stu-id="de377-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de377-110">子要素</span><span class="sxs-lookup"><span data-stu-id="de377-110">Child Elements</span></span>  

 <span data-ttu-id="de377-111">なし。</span><span class="sxs-lookup"><span data-stu-id="de377-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de377-112">親要素</span><span class="sxs-lookup"><span data-stu-id="de377-112">Parent Elements</span></span>  
  
|<span data-ttu-id="de377-113">要素</span><span class="sxs-lookup"><span data-stu-id="de377-113">Element</span></span>|<span data-ttu-id="de377-114">説明</span><span class="sxs-lookup"><span data-stu-id="de377-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de377-115">\<schemeSettings> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="de377-115">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="de377-116"><xref:System.Uri> が特定のスキームに解析される方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="de377-116">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de377-117">解説</span><span class="sxs-lookup"><span data-stu-id="de377-117">Remarks</span></span>  

 <span data-ttu-id="de377-118">既定では、 <xref:System.Uri?displayProperty=nameWithType> クラスは、パスの圧縮を実行する前に、エンコードされたパス区切り記号のエスケープを解除します。</span><span class="sxs-lookup"><span data-stu-id="de377-118">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="de377-119">これは、次のような攻撃に対するセキュリティメカニズムとして実装されています。</span><span class="sxs-lookup"><span data-stu-id="de377-119">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="de377-120">% Encoded 文字を正しく処理しないモジュールにこの URI が渡された場合、サーバーによって次のコマンドが実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="de377-120">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="de377-121">このため、 <xref:System.Uri?displayProperty=nameWithType> クラスはまずパスの区切り記号をエスケープ解除し、次にパスの圧縮を適用します。</span><span class="sxs-lookup"><span data-stu-id="de377-121">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="de377-122">上の悪意のある URL をクラスコンストラクターに渡すと、次の URI が生成され <xref:System.Uri?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="de377-122">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="de377-123">この既定の動作は、特定のスキームの schemeSettings 構成オプションを使用して、パーセントエンコードされたパス区切り記号のエスケープを解除しないように変更できます。</span><span class="sxs-lookup"><span data-stu-id="de377-123">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="de377-124">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="de377-124">Configuration Files</span></span>  

 <span data-ttu-id="de377-125">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="de377-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de377-126">例</span><span class="sxs-lookup"><span data-stu-id="de377-126">Example</span></span>  

 <span data-ttu-id="de377-127">次の例は、すべてのスキーム設定をクリアするクラスによって使用される構成を示して <xref:System.Uri> います。その後、http スキームに対してパーセントでエンコードされたパス区切り記号をエスケープしないためのサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="de377-127">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de377-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="de377-128">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="de377-129">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="de377-129">Network Settings Schema</span></span>](index.md)
