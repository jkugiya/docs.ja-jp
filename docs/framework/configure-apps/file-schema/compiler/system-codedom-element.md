---
description: 詳細については、「<システム> 要素」を参照してください。
title: <system.codedom> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 4761f971255b8ff7d60edfb8d9f5789c2e545aef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699013"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="c3e55-103">\<system.codedom> 要素</span><span class="sxs-lookup"><span data-stu-id="c3e55-103">\<system.codedom> Element</span></span>

<span data-ttu-id="c3e55-104">使用可能な言語プロバイダーのコンパイラ構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3e55-104">Specifies compiler configuration settings for available language providers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a><span data-ttu-id="c3e55-105">構文</span><span class="sxs-lookup"><span data-stu-id="c3e55-105">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3e55-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c3e55-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c3e55-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c3e55-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3e55-108">属性</span><span class="sxs-lookup"><span data-stu-id="c3e55-108">Attributes</span></span>  

 <span data-ttu-id="c3e55-109">なし。</span><span class="sxs-lookup"><span data-stu-id="c3e55-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c3e55-110">子要素</span><span class="sxs-lookup"><span data-stu-id="c3e55-110">Child Elements</span></span>  
  
|<span data-ttu-id="c3e55-111">要素</span><span class="sxs-lookup"><span data-stu-id="c3e55-111">Element</span></span>|<span data-ttu-id="c3e55-112">説明</span><span class="sxs-lookup"><span data-stu-id="c3e55-112">Description</span></span>|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="c3e55-113">コンパイラ構成要素のコンテナー。0個以上の要素が含まれてい [\<compiler>](compiler-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="c3e55-113">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3e55-114">親要素</span><span class="sxs-lookup"><span data-stu-id="c3e55-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c3e55-115">要素</span><span class="sxs-lookup"><span data-stu-id="c3e55-115">Element</span></span>|<span data-ttu-id="c3e55-116">説明</span><span class="sxs-lookup"><span data-stu-id="c3e55-116">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="c3e55-117">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="c3e55-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3e55-118">解説</span><span class="sxs-lookup"><span data-stu-id="c3e55-118">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="c3e55-119">.NET Framework バージョン2.0</span><span class="sxs-lookup"><span data-stu-id="c3e55-119">.NET Framework Version 2.0</span></span>  

 <span data-ttu-id="c3e55-120">要素には、およびなど、 [\<system.codedom>](system-codedom-element.md) .NET Framework と共にインストールされる既定のプロバイダーに加えて、コンピューターにインストールされている言語プロバイダーのコンパイラ構成設定が含まれてい <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider> ます。</span><span class="sxs-lookup"><span data-stu-id="c3e55-120">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="c3e55-121">[\<compilers>](compilers-element.md)要素に0個以上の要素が含まれてい [\<compiler>](compiler-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="c3e55-121">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="c3e55-122">各 [\<compiler>](compiler-element.md) 要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3e55-122">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="c3e55-123">開発者やコンパイラベンダーは、新しい実装のために構成設定をマシン構成ファイル (Machine.config) に追加でき <xref:System.CodeDom.Compiler.CodeDomProvider> ます。</span><span class="sxs-lookup"><span data-stu-id="c3e55-123">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="c3e55-124">メソッドを使用して、 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> コンピューター上のコンパイラ構成設定によって識別される既定の言語プロバイダーと言語プロバイダーの両方をプログラムによって列挙します。</span><span class="sxs-lookup"><span data-stu-id="c3e55-124">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3e55-125">.NET Framework バージョン1.0 および1.1 では、.NET Framework によって提供される既定の言語プロバイダーが要素で識別され [\<compilers>](compilers-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="c3e55-125">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="c3e55-126">.NET Framework バージョン2.0 では、既定の言語プロバイダーは要素で識別されません [\<compilers>](compilers-element.md) が、メソッドを使用して列挙でき <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="c3e55-126">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="c3e55-127">.NET Framework バージョン1.0 および1.1</span><span class="sxs-lookup"><span data-stu-id="c3e55-127">.NET Framework Versions 1.0 and 1.1</span></span>  

 <span data-ttu-id="c3e55-128">要素には、 [\<system.codedom>](system-codedom-element.md) コンピューター上の言語プロバイダーのコンパイラ構成設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c3e55-128">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="c3e55-129">[\<compilers>](compilers-element.md)要素に0個以上の要素が含まれてい [\<compiler>](compiler-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="c3e55-129">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="c3e55-130">各 [\<compiler>](compiler-element.md) 要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3e55-130">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="c3e55-131">.NET Framework は、マシン構成ファイル (Machine.config) 内でコンパイラの初期設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="c3e55-131">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="c3e55-132">開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> の実装のために構成設定を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="c3e55-132">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="c3e55-133"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。</span><span class="sxs-lookup"><span data-stu-id="c3e55-133">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="c3e55-134">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="c3e55-134">Configuration File</span></span>  

 <span data-ttu-id="c3e55-135">この要素は、マシン構成ファイルおよびアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3e55-135">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3e55-136">例</span><span class="sxs-lookup"><span data-stu-id="c3e55-136">Example</span></span>  

 <span data-ttu-id="c3e55-137">次の例は、一般的なコンパイラ構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="c3e55-137">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=1.0.5000.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3e55-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3e55-138">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="c3e55-139">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="c3e55-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c3e55-140">コンパイラおよび言語プロバイダー設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="c3e55-140">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c3e55-141">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="c3e55-141">\<compiler> Element</span></span>](compiler-element.md)
