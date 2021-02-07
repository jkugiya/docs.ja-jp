---
description: '詳細情報: <schemeSettings> 要素 (Uri 設定)'
title: <schemeSettings> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 218676c10a8acaa79c2eb2146214e77beee9a972
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698441"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="255bf-103">\<schemeSettings> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="255bf-103">\<schemeSettings> Element (Uri Settings)</span></span>

<span data-ttu-id="255bf-104"><xref:System.Uri> が特定のスキームに解析される方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="255bf-104">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="255bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="255bf-105">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="255bf-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="255bf-106">Attributes and Elements</span></span>  

 <span data-ttu-id="255bf-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="255bf-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="255bf-108">属性</span><span class="sxs-lookup"><span data-stu-id="255bf-108">Attributes</span></span>  

 <span data-ttu-id="255bf-109">なし</span><span class="sxs-lookup"><span data-stu-id="255bf-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="255bf-110">子要素</span><span class="sxs-lookup"><span data-stu-id="255bf-110">Child Elements</span></span>  
  
|<span data-ttu-id="255bf-111">**要素**</span><span class="sxs-lookup"><span data-stu-id="255bf-111">**Element**</span></span>|<span data-ttu-id="255bf-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="255bf-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="255bf-113">add</span><span class="sxs-lookup"><span data-stu-id="255bf-113">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="255bf-114">スキーム名のスキーム設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="255bf-114">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="255bf-115">オフ</span><span class="sxs-lookup"><span data-stu-id="255bf-115">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="255bf-116">既存のスキーム設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="255bf-116">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="255bf-117">remove</span><span class="sxs-lookup"><span data-stu-id="255bf-117">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="255bf-118">スキーム名のスキーム設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="255bf-118">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="255bf-119">親要素</span><span class="sxs-lookup"><span data-stu-id="255bf-119">Parent Elements</span></span>  
  
|<span data-ttu-id="255bf-120">**要素**</span><span class="sxs-lookup"><span data-stu-id="255bf-120">**Element**</span></span>|<span data-ttu-id="255bf-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="255bf-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="255bf-122">uri</span><span class="sxs-lookup"><span data-stu-id="255bf-122">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="255bf-123">.NET Framework が、uniform resource identifier (Uri) を使用して表された web アドレスを処理する方法を指定する設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="255bf-123">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="255bf-124">解説</span><span class="sxs-lookup"><span data-stu-id="255bf-124">Remarks</span></span>  

 <span data-ttu-id="255bf-125">既定では、 <xref:System.Uri?displayProperty=nameWithType> クラスは、パスの圧縮を実行する前に、エンコードされたパス区切り記号のエスケープを解除します。</span><span class="sxs-lookup"><span data-stu-id="255bf-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="255bf-126">これは、次のような攻撃に対するセキュリティメカニズムとして実装されています。</span><span class="sxs-lookup"><span data-stu-id="255bf-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="255bf-127">% Encoded 文字を正しく処理しないモジュールにこの URI が渡された場合、サーバーによって次のコマンドが実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="255bf-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="255bf-128">このため、 <xref:System.Uri?displayProperty=nameWithType> クラスはまずパスの区切り記号をエスケープ解除し、次にパスの圧縮を適用します。</span><span class="sxs-lookup"><span data-stu-id="255bf-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="255bf-129">上の悪意のある URL をクラスコンストラクターに渡すと、次の URI が生成され <xref:System.Uri?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="255bf-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="255bf-130">この既定の動作は、特定のスキームの schemeSettings 構成オプションを使用して、パーセントエンコードされたパス区切り記号のエスケープを解除しないように変更できます。</span><span class="sxs-lookup"><span data-stu-id="255bf-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="255bf-131">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="255bf-131">Configuration Files</span></span>  

 <span data-ttu-id="255bf-132">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="255bf-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="255bf-133">例</span><span class="sxs-lookup"><span data-stu-id="255bf-133">Example</span></span>  

 <span data-ttu-id="255bf-134">次の例は、 <xref:System.Uri> http スキームに対してパーセントでエンコードされたパス区切り記号をエスケープしないようにするために、クラスによって使用される構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="255bf-134">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="255bf-135">要素情報</span><span class="sxs-lookup"><span data-stu-id="255bf-135">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="255bf-136">名前空間</span><span class="sxs-lookup"><span data-stu-id="255bf-136">Namespace</span></span>|<span data-ttu-id="255bf-137">System (システム)</span><span class="sxs-lookup"><span data-stu-id="255bf-137">System</span></span>|  
|<span data-ttu-id="255bf-138">スキーマ名</span><span class="sxs-lookup"><span data-stu-id="255bf-138">Schema Name</span></span>||  
|<span data-ttu-id="255bf-139">検証ファイル</span><span class="sxs-lookup"><span data-stu-id="255bf-139">Validation File</span></span>||  
|<span data-ttu-id="255bf-140">空にすることができます</span><span class="sxs-lookup"><span data-stu-id="255bf-140">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="255bf-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="255bf-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="255bf-142">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="255bf-142">Network Settings Schema</span></span>](index.md)
