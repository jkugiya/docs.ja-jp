---
description: '詳細情報: <remove> schemeSettings の要素 (Uri 設定)'
title: schemeSettings の <remove> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 125a347cfcbb1393ea70032b7e1b198a1a5a4ed0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713027"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="a6cbb-103">schemeSettings の \<remove> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="a6cbb-103">\<remove> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="a6cbb-104">スキーム名のスキーム設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-104">Removes a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="a6cbb-105">構文</span><span class="sxs-lookup"><span data-stu-id="a6cbb-105">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6cbb-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a6cbb-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a6cbb-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6cbb-108">属性</span><span class="sxs-lookup"><span data-stu-id="a6cbb-108">Attributes</span></span>  
  
|<span data-ttu-id="a6cbb-109">属性</span><span class="sxs-lookup"><span data-stu-id="a6cbb-109">Attribute</span></span>|<span data-ttu-id="a6cbb-110">説明</span><span class="sxs-lookup"><span data-stu-id="a6cbb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6cbb-111">name</span><span class="sxs-lookup"><span data-stu-id="a6cbb-111">name</span></span>|<span data-ttu-id="a6cbb-112">この設定を適用するスキーム名。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-112">The scheme name for which this setting applies.</span></span> <span data-ttu-id="a6cbb-113">サポートされている値は、name = "http" と name = "https" だけです。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-113">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6cbb-114">子要素</span><span class="sxs-lookup"><span data-stu-id="a6cbb-114">Child Elements</span></span>  

 <span data-ttu-id="a6cbb-115">なし。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6cbb-116">親要素</span><span class="sxs-lookup"><span data-stu-id="a6cbb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a6cbb-117">要素</span><span class="sxs-lookup"><span data-stu-id="a6cbb-117">Element</span></span>|<span data-ttu-id="a6cbb-118">説明</span><span class="sxs-lookup"><span data-stu-id="a6cbb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6cbb-119">\<schemeSettings> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="a6cbb-119">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="a6cbb-120"><xref:System.Uri> が特定のスキームに解析される方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6cbb-121">解説</span><span class="sxs-lookup"><span data-stu-id="a6cbb-121">Remarks</span></span>  

 <span data-ttu-id="a6cbb-122">既定では、 <xref:System.Uri?displayProperty=nameWithType> クラスは、パスの圧縮を実行する前に、エンコードされたパス区切り記号のエスケープを解除します。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-122">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="a6cbb-123">これは、次のような攻撃に対するセキュリティメカニズムとして実装されています。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-123">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="a6cbb-124">% Encoded 文字を正しく処理しないモジュールにこの URI が渡された場合、サーバーによって次のコマンドが実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-124">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="a6cbb-125">このため、 <xref:System.Uri?displayProperty=nameWithType> クラスはまずパスの区切り記号をエスケープ解除し、次にパスの圧縮を適用します。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-125">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="a6cbb-126">上の悪意のある URL をクラスコンストラクターに渡すと、次の URI が生成され <xref:System.Uri?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-126">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="a6cbb-127">この既定の動作は、特定のスキームの schemeSettings 構成オプションを使用して、パーセントエンコードされたパス区切り記号のエスケープを解除しないように変更できます。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-127">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a6cbb-128">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="a6cbb-128">Configuration Files</span></span>  

 <span data-ttu-id="a6cbb-129">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6cbb-130">例</span><span class="sxs-lookup"><span data-stu-id="a6cbb-130">Example</span></span>  

 <span data-ttu-id="a6cbb-131">次の例は、 <xref:System.Uri> http スキームのスキーム設定をすべて削除するクラスによって使用される構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="a6cbb-131">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6cbb-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6cbb-132">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="a6cbb-133">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="a6cbb-133">Network Settings Schema</span></span>](index.md)
