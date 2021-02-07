---
description: '詳細情報: <providerOption> 要素'
title: <providerOption> 要素
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: 1fdca58830e8563ef28cbca28857127252928fd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699039"
---
# <a name="provideroption-element"></a><span data-ttu-id="3572c-103">\<providerOption> 要素</span><span class="sxs-lookup"><span data-stu-id="3572c-103">\<providerOption> Element</span></span>

<span data-ttu-id="3572c-104">言語プロバイダーのコンパイラバージョン属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="3572c-104">Specifies the compiler version attributes for a language provider.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a><span data-ttu-id="3572c-105">構文</span><span class="sxs-lookup"><span data-stu-id="3572c-105">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3572c-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3572c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3572c-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3572c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3572c-108">属性</span><span class="sxs-lookup"><span data-stu-id="3572c-108">Attributes</span></span>  
  
|<span data-ttu-id="3572c-109">属性</span><span class="sxs-lookup"><span data-stu-id="3572c-109">Attribute</span></span>|<span data-ttu-id="3572c-110">説明</span><span class="sxs-lookup"><span data-stu-id="3572c-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="3572c-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="3572c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="3572c-112">オプションの名前を指定します。たとえば、"CompilerVersion" のようになります。</span><span class="sxs-lookup"><span data-stu-id="3572c-112">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="3572c-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="3572c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3572c-114">オプションの値を指定します。たとえば、"v 3.5" のようになります。</span><span class="sxs-lookup"><span data-stu-id="3572c-114">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3572c-115">子要素</span><span class="sxs-lookup"><span data-stu-id="3572c-115">Child Elements</span></span>  

 <span data-ttu-id="3572c-116">なし。</span><span class="sxs-lookup"><span data-stu-id="3572c-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3572c-117">親要素</span><span class="sxs-lookup"><span data-stu-id="3572c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3572c-118">要素</span><span class="sxs-lookup"><span data-stu-id="3572c-118">Element</span></span>|<span data-ttu-id="3572c-119">説明</span><span class="sxs-lookup"><span data-stu-id="3572c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3572c-120">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="3572c-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="3572c-121">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="3572c-121">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="3572c-122">\<system.codedom> 要素</span><span class="sxs-lookup"><span data-stu-id="3572c-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="3572c-123">使用可能な言語プロバイダーのコンパイラ構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="3572c-123">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="3572c-124">\<compilers> 要素</span><span class="sxs-lookup"><span data-stu-id="3572c-124">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="3572c-125">コンパイラ構成要素のコンテナー。0個以上の要素が含まれてい `<compiler>` ます。</span><span class="sxs-lookup"><span data-stu-id="3572c-125">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="3572c-126">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="3572c-126">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="3572c-127">言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="3572c-127">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3572c-128">解説</span><span class="sxs-lookup"><span data-stu-id="3572c-128">Remarks</span></span>  

 <span data-ttu-id="3572c-129">.NET Framework バージョン3.5 では、Code Document Object Model (CodeDOM) コードプロバイダーは、要素を使用してプロバイダー固有のオプションをサポートでき `<providerOption>` ます。</span><span class="sxs-lookup"><span data-stu-id="3572c-129">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="3572c-130">.NET Framework 3.5 には、更新された .NET Framework 2.0 アセンブリが含まれており、新しい型を含む新しいバージョンの3.5 アセンブリが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3572c-130">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="3572c-131">Microsoft C# および Visual Basic コードプロバイダーは .NET Framework 2.0 アセンブリに含まれていますが、バージョン3.5 コンパイラをサポートするように更新されています。</span><span class="sxs-lookup"><span data-stu-id="3572c-131">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="3572c-132">既定では、更新されたコードプロバイダーはバージョン2.0 コンパイラのコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="3572c-132">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="3572c-133">要素を使用し `<providerOption>` て、ターゲットコンパイラのバージョンを3.5 に変更できます。</span><span class="sxs-lookup"><span data-stu-id="3572c-133">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="3572c-134">これを行うには、属性に "CompilerVersion" を指定し、 `name` 属性に「v 3.5」を指定し `value` ます。</span><span class="sxs-lookup"><span data-stu-id="3572c-134">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="3572c-135">バージョン番号の前には、小文字の "v" を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3572c-135">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="3572c-136">`<providerOption>`.NET Framework 2.0 Machine.config またはルート Web.config ファイルに要素を追加することで、バージョン指定をグローバルにすることができます。</span><span class="sxs-lookup"><span data-stu-id="3572c-136">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="3572c-137">Machine.config ファイルで既定のコンパイラのバージョンを3.5 に更新した場合は、アプリケーション構成ファイルの要素を使用して、アプリケーションごとに2.0 に戻すことができ `<providerOption>` ます。</span><span class="sxs-lookup"><span data-stu-id="3572c-137">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="3572c-138">CodeDOM コードプロバイダーの実装者は、型のパラメーターを受け取るコンストラクターを指定することによって、カスタムオプションを処理でき `providerOptions` <xref:System.Collections.Generic.IDictionary%602> ます。</span><span class="sxs-lookup"><span data-stu-id="3572c-138">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3572c-139">例</span><span class="sxs-lookup"><span data-stu-id="3572c-139">Example</span></span>  

 <span data-ttu-id="3572c-140">次の例は、C# コードプロバイダーのバージョン3.5 を使用するように指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3572c-140">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3572c-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="3572c-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="3572c-142">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="3572c-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3572c-143">\<compilers> 要素</span><span class="sxs-lookup"><span data-stu-id="3572c-143">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="3572c-144">完全修飾型名の指定</span><span class="sxs-lookup"><span data-stu-id="3572c-144">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="3572c-145">[compilation の compilers の compiler 要素 (ASP.NET 設定スキーマ)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3572c-145">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
