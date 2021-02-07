---
description: '詳細情報: <CompatSortNLSVersion> 要素'
title: <CompatSortNLSVersion> 要素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
ms.openlocfilehash: a064c849e53167c5f7cf16b934dfb377f3d07644
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726183"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="2b73d-103">\<CompatSortNLSVersion> 要素</span><span class="sxs-lookup"><span data-stu-id="2b73d-103">\<CompatSortNLSVersion> Element</span></span>

<span data-ttu-id="2b73d-104">文字列比較の実行時に、ランタイムがレガシ並べ替え順序を使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="2b73d-104">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
## <a name="syntax"></a><span data-ttu-id="2b73d-105">構文</span><span class="sxs-lookup"><span data-stu-id="2b73d-105">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b73d-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2b73d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2b73d-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2b73d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b73d-108">属性</span><span class="sxs-lookup"><span data-stu-id="2b73d-108">Attributes</span></span>  
  
|<span data-ttu-id="2b73d-109">属性</span><span class="sxs-lookup"><span data-stu-id="2b73d-109">Attribute</span></span>|<span data-ttu-id="2b73d-110">説明</span><span class="sxs-lookup"><span data-stu-id="2b73d-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2b73d-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="2b73d-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="2b73d-112">並べ替え順序が使用されるロケール ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="2b73d-112">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2b73d-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="2b73d-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="2b73d-114">値</span><span class="sxs-lookup"><span data-stu-id="2b73d-114">Value</span></span>|<span data-ttu-id="2b73d-115">説明</span><span class="sxs-lookup"><span data-stu-id="2b73d-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b73d-116">4096</span><span class="sxs-lookup"><span data-stu-id="2b73d-116">4096</span></span>|<span data-ttu-id="2b73d-117">代替の並べ替え順序を表すロケール ID。</span><span class="sxs-lookup"><span data-stu-id="2b73d-117">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="2b73d-118">この場合、4096は .NET Framework 3.5 以前のバージョンの並べ替え順序を表します。</span><span class="sxs-lookup"><span data-stu-id="2b73d-118">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b73d-119">子要素</span><span class="sxs-lookup"><span data-stu-id="2b73d-119">Child Elements</span></span>  

 <span data-ttu-id="2b73d-120">なし。</span><span class="sxs-lookup"><span data-stu-id="2b73d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b73d-121">親要素</span><span class="sxs-lookup"><span data-stu-id="2b73d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2b73d-122">要素</span><span class="sxs-lookup"><span data-stu-id="2b73d-122">Element</span></span>|<span data-ttu-id="2b73d-123">説明</span><span class="sxs-lookup"><span data-stu-id="2b73d-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2b73d-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="2b73d-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2b73d-125">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="2b73d-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b73d-126">解説</span><span class="sxs-lookup"><span data-stu-id="2b73d-126">Remarks</span></span>  

 <span data-ttu-id="2b73d-127">.NET Framework 4 のクラスによって実行される文字列比較、並べ替え、および大文字と小文字の区別の操作は、 <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> Unicode 5.1 標準に準拠しているため、やなどの文字列比較メソッドの結果は、 <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> 以前のバージョンの .NET Framework とは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b73d-127">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="2b73d-128">アプリケーションが従来の動作に依存している場合は、 `<CompatSortNLSVersion>` アプリケーションの構成ファイルに要素を含めることによって、.NET Framework 3.5 以前のバージョンで使用されている文字列比較規則および並べ替え規則を復元できます。</span><span class="sxs-lookup"><span data-stu-id="2b73d-128">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2b73d-129">文字列の比較および並べ替えのレガシ規則を復元する場合は、ローカル システムで sort00001000.dll ダイナミック リンク ライブラリも使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b73d-129">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="2b73d-130">アプリケーション ドメインを作成するときに、文字列 "NetFx40_Legacy20SortingBehavior" を <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> メソッドに渡すことで、文字列の比較および並べ替えのレガシ規則を特定のアプリケーション ドメインで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2b73d-130">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b73d-131">例</span><span class="sxs-lookup"><span data-stu-id="2b73d-131">Example</span></span>  

 <span data-ttu-id="2b73d-132">次の例では、2 つの <xref:System.String> オブジェクトをインスタンス化して、<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> メソッドを呼び出し、現在のカルチャの規則を使用してそれらのオブジェクトを比較する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2b73d-132">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="2b73d-133">.NET Framework 4 でこの例を実行すると、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b73d-133">When you run the example on the .NET Framework 4, it displays the following output:</span></span>
  
```console
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="2b73d-134">これは、.NET Framework 3.5 で例を実行したときに表示される出力とはまったく異なります。</span><span class="sxs-lookup"><span data-stu-id="2b73d-134">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5:</span></span>
  
```console
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="2b73d-135">ただし、次の構成ファイルを例のディレクトリに追加し、.NET Framework 4 でこの例を実行すると、出力は、.NET Framework 3.5 で実行された場合に例で生成されたものと同じになります。</span><span class="sxs-lookup"><span data-stu-id="2b73d-135">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b73d-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b73d-136">See also</span></span>

- [<span data-ttu-id="2b73d-137">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="2b73d-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b73d-138">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="2b73d-138">Configuration File Schema</span></span>](../index.md)
