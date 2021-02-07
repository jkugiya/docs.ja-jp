---
description: '詳細情報: <supportPortability> 要素'
title: <supportPortability> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 5a39f946d5b3841af5f4254cc2f70142aa6c013d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754512"
---
# <a name="supportportability-element"></a><span data-ttu-id="7e626-103">\<supportPortability> 要素</span><span class="sxs-lookup"><span data-stu-id="7e626-103">\<supportPortability> Element</span></span>

<span data-ttu-id="7e626-104">.NET Framework の 2 つの異なる実装にある同じアセンブリを 1 つのアプリケーションから参照できるように、既定の動作を無効にすることができます。既定の動作では、アプリケーションの移植性を高めるために、このようなアセンブリは同等のものとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="7e626-104">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a><span data-ttu-id="7e626-105">構文</span><span class="sxs-lookup"><span data-stu-id="7e626-105">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e626-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7e626-106">Attributes and Elements</span></span>  

<span data-ttu-id="7e626-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e626-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e626-108">属性</span><span class="sxs-lookup"><span data-stu-id="7e626-108">Attributes</span></span>  
  
|<span data-ttu-id="7e626-109">属性</span><span class="sxs-lookup"><span data-stu-id="7e626-109">Attribute</span></span>|<span data-ttu-id="7e626-110">説明</span><span class="sxs-lookup"><span data-stu-id="7e626-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e626-111">PKT</span><span class="sxs-lookup"><span data-stu-id="7e626-111">PKT</span></span>|<span data-ttu-id="7e626-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="7e626-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="7e626-113">対象となるアセンブリの公開キー トークンを文字列で指定します。</span><span class="sxs-lookup"><span data-stu-id="7e626-113">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="7e626-114">enabled</span><span class="sxs-lookup"><span data-stu-id="7e626-114">enabled</span></span>|<span data-ttu-id="7e626-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7e626-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7e626-116">指定した .NET Framework アセンブリの複数の実装間での移植性に対するサポートを有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e626-116">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7e626-117">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="7e626-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="7e626-118">値</span><span class="sxs-lookup"><span data-stu-id="7e626-118">Value</span></span>|<span data-ttu-id="7e626-119">説明</span><span class="sxs-lookup"><span data-stu-id="7e626-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7e626-120">true</span><span class="sxs-lookup"><span data-stu-id="7e626-120">true</span></span>|<span data-ttu-id="7e626-121">指定した .NET Framework アセンブリの複数の実装間での移植性に対するサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7e626-121">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="7e626-122">既定値です。</span><span class="sxs-lookup"><span data-stu-id="7e626-122">This is the default.</span></span>|  
|<span data-ttu-id="7e626-123">false</span><span class="sxs-lookup"><span data-stu-id="7e626-123">false</span></span>|<span data-ttu-id="7e626-124">指定した .NET Framework アセンブリの複数の実装間での移植性に対するサポートを無効にします。</span><span class="sxs-lookup"><span data-stu-id="7e626-124">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="7e626-125">この場合、指定したアセンブリの複数の実装をアプリケーションで参照できます。</span><span class="sxs-lookup"><span data-stu-id="7e626-125">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e626-126">子要素</span><span class="sxs-lookup"><span data-stu-id="7e626-126">Child Elements</span></span>  

<span data-ttu-id="7e626-127">なし。</span><span class="sxs-lookup"><span data-stu-id="7e626-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e626-128">親要素</span><span class="sxs-lookup"><span data-stu-id="7e626-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7e626-129">要素</span><span class="sxs-lookup"><span data-stu-id="7e626-129">Element</span></span>|<span data-ttu-id="7e626-130">説明</span><span class="sxs-lookup"><span data-stu-id="7e626-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7e626-131">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="7e626-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7e626-132">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7e626-132">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="7e626-133">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e626-133">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e626-134">解説</span><span class="sxs-lookup"><span data-stu-id="7e626-134">Remarks</span></span>  

<span data-ttu-id="7e626-135">.NET Framework 4 以降、.NET Framework の2つの実装のいずれかを使用できるアプリケーションに対して、サポートが自動的に提供されます。たとえば、.NET Framework の実装や、Silverlight の実装のための .NET Framework です。</span><span class="sxs-lookup"><span data-stu-id="7e626-135">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="7e626-136">特定の .NET Framework アセンブリの 2 つの実装は、アセンブリ バインダーで同等と見なされます。</span><span class="sxs-lookup"><span data-stu-id="7e626-136">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="7e626-137">一部のシナリオでは、アプリケーションの移植性を高めるためのこの機能が問題になります。</span><span class="sxs-lookup"><span data-stu-id="7e626-137">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="7e626-138">そのようなシナリオでは、`<supportPortability>` 要素を使用して、この機能を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7e626-138">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="7e626-139">一例として、特定の参照アセンブリの .NET Framework の実装と .NET Framework for Silverlight の実装の両方を参照する必要があるアセンブリが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="7e626-139">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="7e626-140">たとえば、WPF (Windows Presentation Foundation) で作成された XAML デザイナーにおいて、デザイナーのユーザー インターフェイスとして WPF デスクトップの実装を参照すると共に、Silverlight の実装に組み込まれている WPF のサブセットも参照する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e626-140">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="7e626-141">既定では、この 2 つのアセンブリはアセンブリ バインディングで同等と見なされるため、別々に参照するとコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7e626-141">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="7e626-142">この要素を使用すると、既定の動作を無効にし、コンパイルを正常に実行できます。</span><span class="sxs-lookup"><span data-stu-id="7e626-142">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7e626-143">コンパイラから共通言語ランタイムのアセンブリ バインディング ロジックに情報を渡すには、`/appconfig` コンパイラ オプションを使用して、この要素を含む app.config ファイルの場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e626-143">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e626-144">例</span><span class="sxs-lookup"><span data-stu-id="7e626-144">Example</span></span>  

<span data-ttu-id="7e626-145">.NET Framework と .NET Framework for Silverlight の両方の実装に存在する .NET Framework アセンブリについて、その両方の実装をアプリケーションで参照できるようにする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7e626-145">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="7e626-146">`/appconfig` コンパイラ オプションを使用して、この app.config ファイルの場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e626-146">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e626-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e626-147">See also</span></span>

- [<span data-ttu-id="7e626-148">-appconfig (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="7e626-148">-appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="7e626-149">[.NET Framework アセンブリ統合の概要](/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7e626-149">[.NET Framework Assembly Unification Overview](/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
