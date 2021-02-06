---
description: '詳細情報: <module> 要素 (ネットワーク設定)'
title: <module> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: d498b79ae6046367bc81add5ea387e178ab6c29d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652836"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="6a75a-103">\<module> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="6a75a-103">\<module> Element (Network Settings)</span></span>

<span data-ttu-id="6a75a-104">新しいプロキシ モジュールをアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="6a75a-104">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="6a75a-105">構文</span><span class="sxs-lookup"><span data-stu-id="6a75a-105">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a75a-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6a75a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6a75a-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6a75a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a75a-108">属性</span><span class="sxs-lookup"><span data-stu-id="6a75a-108">Attributes</span></span>  
  
|<span data-ttu-id="6a75a-109">**属性**</span><span class="sxs-lookup"><span data-stu-id="6a75a-109">**Attribute**</span></span>|<span data-ttu-id="6a75a-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="6a75a-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="6a75a-111">プロキシを実装する、(プロパティによって示される) 完全修飾型名 <xref:System.Type.FullName%2A> と、コンマで区切られたアセンブリ名 (プロパティによって示され <xref:System.Reflection.Assembly.FullName%2A> ます)。</span><span class="sxs-lookup"><span data-stu-id="6a75a-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a75a-112">子要素</span><span class="sxs-lookup"><span data-stu-id="6a75a-112">Child Elements</span></span>  

 <span data-ttu-id="6a75a-113">なし。</span><span class="sxs-lookup"><span data-stu-id="6a75a-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a75a-114">親要素</span><span class="sxs-lookup"><span data-stu-id="6a75a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6a75a-115">**要素**</span><span class="sxs-lookup"><span data-stu-id="6a75a-115">**Element**</span></span>|<span data-ttu-id="6a75a-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="6a75a-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6a75a-117">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="6a75a-117">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="6a75a-118">ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="6a75a-118">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a75a-119">解説</span><span class="sxs-lookup"><span data-stu-id="6a75a-119">Remarks</span></span>  

 <span data-ttu-id="6a75a-120">要素は、 `module` インターフェイスを実装するプロキシクラスを登録し <xref:System.Net.IWebProxy> ます。</span><span class="sxs-lookup"><span data-stu-id="6a75a-120">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="6a75a-121">プロキシクラスを登録した後、を `module` 使用して、サポートされているプロキシ経由で情報を要求できます。</span><span class="sxs-lookup"><span data-stu-id="6a75a-121">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="6a75a-122">属性の値は、 `type` モジュールのクラス名と、対応するダイナミックリンクライブラリ (DLL) の名前にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a75a-122">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6a75a-123">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="6a75a-123">Configuration Files</span></span>  

 <span data-ttu-id="6a75a-124">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="6a75a-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a75a-125">例</span><span class="sxs-lookup"><span data-stu-id="6a75a-125">Example</span></span>  

 <span data-ttu-id="6a75a-126">次の例では、カスタムプロキシクラスを登録します。</span><span class="sxs-lookup"><span data-stu-id="6a75a-126">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a75a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a75a-127">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="6a75a-128">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="6a75a-128">Network Settings Schema</span></span>](index.md)
