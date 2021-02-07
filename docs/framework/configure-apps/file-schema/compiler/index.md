---
description: '詳細情報: コンパイラおよび言語プロバイダー設定スキーマ'
title: コンパイラおよび言語プロバイダー設定のスキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
ms.openlocfilehash: 64dd57581711358c9051cda5609e0c5ff4fc05bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699195"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="6f404-103">コンパイラおよび言語プロバイダー設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="6f404-103">Compiler and Language Provider Settings Schema</span></span>

<span data-ttu-id="6f404-104">コンパイラおよび言語プロバイダー設定は、使用可能な言語プロバイダーのコンパイラ構成要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f404-104">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="6f404-105">各コンパイラ構成要素は、コード プロバイダーの型名、コンパイラ パラメーター、サポートされる言語名、およびサポートされるファイル拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f404-105">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
<span data-ttu-id="6f404-106">.NET Framework は、マシン構成ファイル (Machine.config) 内でコンパイラの初期設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="6f404-106">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="6f404-107">開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> の実装のために構成設定を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="6f404-107">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="6f404-108"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。</span><span class="sxs-lookup"><span data-stu-id="6f404-108">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)
  
|<span data-ttu-id="6f404-109">要素</span><span class="sxs-lookup"><span data-stu-id="6f404-109">Element</span></span>|<span data-ttu-id="6f404-110">説明</span><span class="sxs-lookup"><span data-stu-id="6f404-110">Description</span></span>|  
|-------------|-----------------|  
|[\<system.codedom>](system-codedom-element.md)|<span data-ttu-id="6f404-111">使用可能な言語プロバイダーのコンパイラ構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f404-111">Specifies compiler configuration settings for available language providers.</span></span>|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="6f404-112">コンパイラ構成要素のコンテナー。0個以上の要素が含まれてい [\<compiler>](compiler-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="6f404-112">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
|[\<compiler>](compiler-element.md)|<span data-ttu-id="6f404-113">言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f404-113">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6f404-114">例</span><span class="sxs-lookup"><span data-stu-id="6f404-114">Example</span></span>  

 <span data-ttu-id="6f404-115">次の例は、一般的なコンパイラ構成要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="6f404-115">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f404-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f404-116">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="6f404-117">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="6f404-117">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6f404-118">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="6f404-118">\<compiler> Element</span></span>](compiler-element.md)
