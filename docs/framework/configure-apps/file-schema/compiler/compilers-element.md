---
description: '詳細情報: <compilers> 要素'
title: <compilers> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 6ced6bc81bc7d829ccebab50e0a361985c970f5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699169"
---
# <a name="compilers-element"></a><span data-ttu-id="fbb06-103">\<compilers> 要素</span><span class="sxs-lookup"><span data-stu-id="fbb06-103">\<compilers> Element</span></span>

<span data-ttu-id="fbb06-104">コンパイラ構成要素のコンテナー。0個以上の要素が含まれてい [\<compiler>](compiler-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="fbb06-104">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="fbb06-105">構文</span><span class="sxs-lookup"><span data-stu-id="fbb06-105">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbb06-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fbb06-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fbb06-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbb06-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbb06-108">属性</span><span class="sxs-lookup"><span data-stu-id="fbb06-108">Attributes</span></span>  

 <span data-ttu-id="fbb06-109">なし。</span><span class="sxs-lookup"><span data-stu-id="fbb06-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fbb06-110">子要素</span><span class="sxs-lookup"><span data-stu-id="fbb06-110">Child Elements</span></span>  
  
|<span data-ttu-id="fbb06-111">要素</span><span class="sxs-lookup"><span data-stu-id="fbb06-111">Element</span></span>|<span data-ttu-id="fbb06-112">説明</span><span class="sxs-lookup"><span data-stu-id="fbb06-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbb06-113">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="fbb06-113">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="fbb06-114">言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbb06-114">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbb06-115">親要素</span><span class="sxs-lookup"><span data-stu-id="fbb06-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fbb06-116">要素</span><span class="sxs-lookup"><span data-stu-id="fbb06-116">Element</span></span>|<span data-ttu-id="fbb06-117">説明</span><span class="sxs-lookup"><span data-stu-id="fbb06-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbb06-118">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="fbb06-118">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="fbb06-119">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="fbb06-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="fbb06-120">\<system.codedom> 要素</span><span class="sxs-lookup"><span data-stu-id="fbb06-120">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="fbb06-121">使用可能な言語プロバイダーのコンパイラ構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbb06-121">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbb06-122">解説</span><span class="sxs-lookup"><span data-stu-id="fbb06-122">Remarks</span></span>  

 <span data-ttu-id="fbb06-123">要素には、 [\<compilers>](compilers-element.md) コンピューター上の言語プロバイダーのコンパイラ構成設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fbb06-123">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="fbb06-124">各 [\<compiler>](compiler-element.md) 要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbb06-124">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="fbb06-125">.NET Framework は、マシン構成ファイル (Machine.config) の初期コンパイラおよび言語プロバイダー設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="fbb06-125">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="fbb06-126">開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> の実装のために構成設定を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="fbb06-126">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="fbb06-127"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。</span><span class="sxs-lookup"><span data-stu-id="fbb06-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="fbb06-128">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="fbb06-128">Configuration File</span></span>  

 <span data-ttu-id="fbb06-129">この要素は、マシン構成ファイルおよびアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="fbb06-129">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbb06-130">例</span><span class="sxs-lookup"><span data-stu-id="fbb06-130">Example</span></span>  

 <span data-ttu-id="fbb06-131">次の例は、一般的なコンパイラ構成要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="fbb06-131">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler
          language="c#;cs;csharp"
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbb06-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbb06-132">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="fbb06-133">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="fbb06-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fbb06-134">コンパイラおよび言語プロバイダー設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="fbb06-134">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fbb06-135">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="fbb06-135">\<compiler> Element</span></span>](compiler-element.md)
