---
description: '詳細情報: 一般的な属性 (Visual Basic)'
title: 共通の属性
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 875554b69a23640c2d67367c93b56c34c286df37
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437788"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="efd78-103">一般的な属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efd78-103">Common Attributes (Visual Basic)</span></span>

<span data-ttu-id="efd78-104">このトピックでは、Visual Basic プログラムで最もよく使用される属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="efd78-104">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>

- [<span data-ttu-id="efd78-105">グローバル属性</span><span class="sxs-lookup"><span data-stu-id="efd78-105">Global Attributes</span></span>](#Global)

- [<span data-ttu-id="efd78-106">Obsolete 属性</span><span class="sxs-lookup"><span data-stu-id="efd78-106">Obsolete Attribute</span></span>](#Obsolete)

- [<span data-ttu-id="efd78-107">Conditional 属性</span><span class="sxs-lookup"><span data-stu-id="efd78-107">Conditional Attribute</span></span>](#Conditional)

- [<span data-ttu-id="efd78-108">呼び出し元情報属性</span><span class="sxs-lookup"><span data-stu-id="efd78-108">Caller Info Attributes</span></span>](#CallerInfo)

- [<span data-ttu-id="efd78-109">Visual Basic の属性</span><span class="sxs-lookup"><span data-stu-id="efd78-109">Visual Basic Attributes</span></span>](#VB)

## <a name="global-attributes"></a><a name="Global"></a> <span data-ttu-id="efd78-110">グローバル属性</span><span class="sxs-lookup"><span data-stu-id="efd78-110">Global Attributes</span></span>

<span data-ttu-id="efd78-111">ほとんどの属性は、クラスやメソッドなど、特定の言語要素に適用されます。ただし、属性の中にはグローバルなものがあり、アセンブリまたはモジュール全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-111">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="efd78-112">たとえば、<xref:System.Reflection.AssemblyVersionAttribute> 属性は、次のように、バージョン情報をアセンブリに埋め込むときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-112">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

<span data-ttu-id="efd78-113">ソース コードでは、グローバル属性は、トップレベルの `Imports` ステートメントより後、型、モジュール、または名前空間の宣言より前に指定します。</span><span class="sxs-lookup"><span data-stu-id="efd78-113">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="efd78-114">グローバル属性は複数のソース ファイルに指定できますが、それらのファイルは、1 つのコンパイル パスでコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="efd78-114">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="efd78-115">Visual Basic プロジェクトでは、グローバル属性が通常、AssemblyInfo.vb ファイルに配置されます (このファイルは、Visual Studio でプロジェクトを作成すると自動的に作成されます)。</span><span class="sxs-lookup"><span data-stu-id="efd78-115">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>

<span data-ttu-id="efd78-116">アセンブリの属性は、アセンブリに関する情報を提供する値です。</span><span class="sxs-lookup"><span data-stu-id="efd78-116">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="efd78-117">これらは次のカテゴリに分けられます。</span><span class="sxs-lookup"><span data-stu-id="efd78-117">They fall into the following categories:</span></span>

- <span data-ttu-id="efd78-118">アセンブリ ID 属性</span><span class="sxs-lookup"><span data-stu-id="efd78-118">Assembly identity attributes</span></span>

- <span data-ttu-id="efd78-119">情報属性</span><span class="sxs-lookup"><span data-stu-id="efd78-119">Informational attributes</span></span>

- <span data-ttu-id="efd78-120">アセンブリ マニフェスト属性</span><span class="sxs-lookup"><span data-stu-id="efd78-120">Assembly manifest attributes</span></span>

### <a name="assembly-identity-attributes"></a><span data-ttu-id="efd78-121">アセンブリ ID 属性</span><span class="sxs-lookup"><span data-stu-id="efd78-121">Assembly Identity Attributes</span></span>

<span data-ttu-id="efd78-122">アセンブリの ID は、名前、バージョン、カルチャの 3 つの属性によって識別されます (適用できる場合は厳密な名前も使用されます)。</span><span class="sxs-lookup"><span data-stu-id="efd78-122">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="efd78-123">アセンブリの完全な名前を形成するこれらの属性は、コード内でアセンブリを参照するときに必要になります。</span><span class="sxs-lookup"><span data-stu-id="efd78-123">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="efd78-124">アセンブリのバージョンとカルチャは、属性を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-124">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="efd78-125">ただし名前の値は、コンパイラ、Visual Studio IDE の [[アセンブリ情報]](/visualstudio/ide/reference/assembly-information-dialog-box) ダイアログ ボックス、またはアセンブリ リンカー (AI.exe) によってアセンブリの作成時に設定されます。このとき、設定はアセンブリ マニフェストが含まれたファイルに基づきます。</span><span class="sxs-lookup"><span data-stu-id="efd78-125">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="efd78-126"><xref:System.Reflection.AssemblyFlagsAttribute> 属性は、アセンブリの複数のコピーが共存できるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="efd78-126">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="efd78-127">次の表に ID 属性を示します。</span><span class="sxs-lookup"><span data-stu-id="efd78-127">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="efd78-128">属性</span><span class="sxs-lookup"><span data-stu-id="efd78-128">Attribute</span></span>|<span data-ttu-id="efd78-129">目的</span><span class="sxs-lookup"><span data-stu-id="efd78-129">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="efd78-130">アセンブリの ID を完全に記述します。</span><span class="sxs-lookup"><span data-stu-id="efd78-130">Fully describes the identity of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="efd78-131">アセンブリのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="efd78-131">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="efd78-132">アセンブリがサポートするカルチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="efd78-132">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="efd78-133">同じコンピューター、同じプロセス、または同じアプリケーション ドメインでの side-by-side 実行をアセンブリがサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="efd78-133">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

### <a name="informational-attributes"></a><span data-ttu-id="efd78-134">情報属性</span><span class="sxs-lookup"><span data-stu-id="efd78-134">Informational Attributes</span></span>

<span data-ttu-id="efd78-135">情報属性は、追加の会社情報または製品情報をアセンブリに指定する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-135">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="efd78-136">次の表は、<xref:System.Reflection?displayProperty=nameWithType> 名前空間で定義されている情報属性を示しています。</span><span class="sxs-lookup"><span data-stu-id="efd78-136">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="efd78-137">属性</span><span class="sxs-lookup"><span data-stu-id="efd78-137">Attribute</span></span>|<span data-ttu-id="efd78-138">目的</span><span class="sxs-lookup"><span data-stu-id="efd78-138">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="efd78-139">アセンブリ マニフェストの製品名を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="efd78-139">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="efd78-140">アセンブリ マニフェストの商標を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="efd78-140">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="efd78-141">アセンブリ マニフェストの補足バージョンを指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="efd78-141">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="efd78-142">アセンブリ マニフェストの会社名を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="efd78-142">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="efd78-143">アセンブリ マニフェストの著作権を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="efd78-143">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="efd78-144">Win32 ファイル バージョン リソースの特定のバージョン番号を使用するようコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="efd78-144">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="efd78-145">アセンブリが共通言語仕様 (CLS) に準拠しているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="efd78-145">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

### <a name="assembly-manifest-attributes"></a><span data-ttu-id="efd78-146">アセンブリ マニフェスト属性</span><span class="sxs-lookup"><span data-stu-id="efd78-146">Assembly Manifest Attributes</span></span>

<span data-ttu-id="efd78-147">アセンブリ マニフェスト属性を使用すると、アセンブリ マニフェストの情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-147">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="efd78-148">ここには、タイトル、説明、既定の別名、構成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="efd78-148">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="efd78-149">次の表は、<xref:System.Reflection?displayProperty=nameWithType> 名前空間で定義されているアセンブリ マニフェスト属性を示しています。</span><span class="sxs-lookup"><span data-stu-id="efd78-149">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="efd78-150">属性</span><span class="sxs-lookup"><span data-stu-id="efd78-150">Attribute</span></span>|<span data-ttu-id="efd78-151">目的</span><span class="sxs-lookup"><span data-stu-id="efd78-151">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="efd78-152">アセンブリ マニフェストのアセンブリのタイトルを指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="efd78-152">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="efd78-153">アセンブリ マニフェストのアセンブリの説明を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="efd78-153">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="efd78-154">アセンブリ マニフェストのアセンブリの構成 (製品版やデバッグなど) を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="efd78-154">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="efd78-155">アセンブリ マニフェストのわかりやすい既定の別名を定義します。</span><span class="sxs-lookup"><span data-stu-id="efd78-155">Defines a friendly default alias for an assembly manifest</span></span>|

## <a name="obsolete-attribute"></a><a name="Obsolete"></a> <span data-ttu-id="efd78-156">Obsolete 属性</span><span class="sxs-lookup"><span data-stu-id="efd78-156">Obsolete Attribute</span></span>

<span data-ttu-id="efd78-157">`Obsolete` 属性は、使用が推奨されなくなったプログラム エンティティをマークします。</span><span class="sxs-lookup"><span data-stu-id="efd78-157">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="efd78-158">その後、非推奨の印が付いたエンティティが使用されるたびに、この属性の構成に従って警告かエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-158">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="efd78-159">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="efd78-159">For example:</span></span>

```vb
<System.Obsolete("use class B")>
Class A
    Sub Method()
    End Sub
End Class

Class B
    <System.Obsolete("use NewMethod", True)>
    Sub OldMethod()
    End Sub

    Sub NewMethod()
    End Sub
End Class
```

<span data-ttu-id="efd78-160">この例では、`Obsolete` 属性はクラス `A` とメソッド `B.OldMethod` に適用されています。</span><span class="sxs-lookup"><span data-stu-id="efd78-160">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="efd78-161">`B.OldMethod` に適用された属性コンストラクターの 2 番目の引数が `true` に設定されているため、このメソッドではコンパイル エラーが発生します。一方、クラス `A` が使用されると、警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-161">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="efd78-162">しかし、`B.NewMethod` の呼び出しでは、警告もエラーも生成されません。</span><span class="sxs-lookup"><span data-stu-id="efd78-162">Calling `B.NewMethod`, however, produces no warning or error.</span></span>

<span data-ttu-id="efd78-163">最初の引数として属性コンストラクターに指定された文字列は、警告またはエラーの一部として表示されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-163">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="efd78-164">たとえば、前の定義でこれを使用すると、次のコードで 2 つの警告と 1 つのエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-164">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

<span data-ttu-id="efd78-165">クラス `A` の警告が 2 つ生成されます。1 つはクラス参照の宣言の警告で、もう 1 つはクラス コンストラクターの警告です。</span><span class="sxs-lookup"><span data-stu-id="efd78-165">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>

<span data-ttu-id="efd78-166">`Obsolete` 属性は引数なしで使用できますが、対象の項目が古い理由と代用する項目の説明を加えておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="efd78-166">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>

<span data-ttu-id="efd78-167">`Obsolete` 属性は、1 回だけ使用できる属性であり、属性を使用できる任意のエンティティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-167">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="efd78-168">`Obsolete` は <xref:System.ObsoleteAttribute> の別名です。</span><span class="sxs-lookup"><span data-stu-id="efd78-168">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

## <a name="conditional-attribute"></a><a name="Conditional"></a> <span data-ttu-id="efd78-169">Conditional 属性</span><span class="sxs-lookup"><span data-stu-id="efd78-169">Conditional Attribute</span></span>

<span data-ttu-id="efd78-170">`Conditional` 属性を使用すると、プリプロセス識別子に依存したメソッドの実行を指定できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-170">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="efd78-171">`Conditional` 属性は <xref:System.Diagnostics.ConditionalAttribute> の別名であり、メソッドまたは属性クラスに適用できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-171">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="efd78-172">この例では、`Conditional` は、プログラム固有の診断情報の表示を有効または無効にするメソッドに適用されています。</span><span class="sxs-lookup"><span data-stu-id="efd78-172">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

```vb
#Const TRACE_ON = True
Imports System.Diagnostics

Module TestConditionalAttribute
    Public Class Trace
        <Conditional("TRACE_ON")>
        Public Shared Sub Msg(ByVal msg As String)
            Console.WriteLine(msg)
        End Sub

    End Class

    Sub Main()
        Trace.Msg("Now in Main...")
        Console.WriteLine("Done.")
    End Sub
End Module
```

<span data-ttu-id="efd78-173">`TRACE_ON` 識別子が定義されていない場合、トレース出力は表示されません。</span><span class="sxs-lookup"><span data-stu-id="efd78-173">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>

<span data-ttu-id="efd78-174">`Conditional` 属性は、(リリース ビルドではなく) デバッグ ビルドのトレース機能とログ機能を有効にするために、`DEBUG` 識別子と共によく使用されます。これは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="efd78-174">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

<span data-ttu-id="efd78-175">条件付きの印が付いたメソッドが呼び出されると、指定のプリプロセッサ シンボルの有無に従って、呼び出しの実行か省略が決定されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-175">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="efd78-176">シンボルが定義されている場合は呼び出しが実行され、定義されていない場合は省略されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-176">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="efd78-177">次のように、`#if…#endif` ブロック内でメソッドを囲むよりも `Conditional` を使用した方が、すっきりとして洗練されているうえ、エラーも少なくなります。</span><span class="sxs-lookup"><span data-stu-id="efd78-177">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

<span data-ttu-id="efd78-178">条件付きメソッドは、クラスまたは構造体の宣言内のメソッドである必要があります。また、戻り値を持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="efd78-178">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>

### <a name="using-multiple-identifiers"></a><span data-ttu-id="efd78-179">複数の識別子の使用</span><span class="sxs-lookup"><span data-stu-id="efd78-179">Using Multiple Identifiers</span></span>

<span data-ttu-id="efd78-180">メソッドに複数の `Conditional` 属性が付いている場合、そのメソッドの呼び出しは、1 つ以上の条件付きシンボルが定義されているときに実行されます (つまり、シンボルは OR 演算子によって論理的にリンクされています)。</span><span class="sxs-lookup"><span data-stu-id="efd78-180">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="efd78-181">この例では、`A` と `B` のどちらかがあると、メソッドの呼び出しが実行されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-181">In this example, the presence of either `A` or `B` will result in a method call:</span></span>

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

<span data-ttu-id="efd78-182">AND 演算子で論理的にリンクされたシンボルの効果を実現するには、条件付きメソッドを連続して定義します。</span><span class="sxs-lookup"><span data-stu-id="efd78-182">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="efd78-183">たとえば、次の 2 番目のメソッドは、`A` と `B` が両方定義されている場合にのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-183">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>

```vb
<Conditional("A")>
Shared Sub DoIfA()
    DoIfAandB()
End Sub

<Conditional("B")>
Shared Sub DoIfAandB()
    ' Code to execute when both A and B are defined...
End Sub
```

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="efd78-184">属性クラスでの Conditional の使用</span><span class="sxs-lookup"><span data-stu-id="efd78-184">Using Conditional with Attribute Classes</span></span>

<span data-ttu-id="efd78-185">`Conditional` 属性は、属性クラスの定義にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-185">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="efd78-186">この例では、カスタム属性 `Documentation` は、DEBUG が定義されている場合にのみ、情報をメタデータに追加します。</span><span class="sxs-lookup"><span data-stu-id="efd78-186">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>

```vb
<Conditional("DEBUG")>
Public Class Documentation
    Inherits System.Attribute
    Private text As String
    Sub New(ByVal doc_text As String)
        text = doc_text
    End Sub
End Class

Class SampleClass
    ' This attribute will only be included if DEBUG is defined.
    <Documentation("This method displays an integer.")>
    Shared Sub DoWork(ByVal i As Integer)
        System.Console.WriteLine(i)
    End Sub
End Class
```

## <a name="caller-info-attributes"></a><a name="CallerInfo"></a> <span data-ttu-id="efd78-187">呼び出し元情報属性</span><span class="sxs-lookup"><span data-stu-id="efd78-187">Caller Info Attributes</span></span>

<span data-ttu-id="efd78-188">呼び出し元情報の属性を使用すると、メソッドへの呼び出し元に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-188">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="efd78-189">ソース コードのファイル パス、ソース コードの行番号、呼び出し元のメンバー名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-189">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>

<span data-ttu-id="efd78-190">メンバー呼び出し元情報を取得するには、省略可能なパラメーターに適用される属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="efd78-190">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="efd78-191">省略可能な各パラメーターでは既定値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-191">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="efd78-192">次の表は、<xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 名前空間で定義されている呼び出し元情報の属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="efd78-192">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="efd78-193">属性</span><span class="sxs-lookup"><span data-stu-id="efd78-193">Attribute</span></span>|<span data-ttu-id="efd78-194">説明</span><span class="sxs-lookup"><span data-stu-id="efd78-194">Description</span></span>|<span data-ttu-id="efd78-195">種類</span><span class="sxs-lookup"><span data-stu-id="efd78-195">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="efd78-196">呼び出し元を含むソース ファイルのフル パスです。</span><span class="sxs-lookup"><span data-stu-id="efd78-196">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="efd78-197">これはコンパイル時のパスです。</span><span class="sxs-lookup"><span data-stu-id="efd78-197">This is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="efd78-198">メソッドの呼び出し元であるソース ファイルの行番号。</span><span class="sxs-lookup"><span data-stu-id="efd78-198">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="efd78-199">呼び出し元のメソッド名またはプロパティ名。</span><span class="sxs-lookup"><span data-stu-id="efd78-199">Method name or property name of the caller.</span></span> <span data-ttu-id="efd78-200">詳細については、「[呼び出し元情報 (Visual Basic)](../caller-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efd78-200">For more information, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>|`String`|

<span data-ttu-id="efd78-201">呼び出し元情報属性の詳細については、「[呼び出し元情報 (Visual Basic)](../caller-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efd78-201">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>

## <a name="visual-basic-attributes"></a><a name="VB"></a><span data-ttu-id="efd78-202">Visual Basic の属性</span><span class="sxs-lookup"><span data-stu-id="efd78-202">Visual Basic Attributes</span></span>

<span data-ttu-id="efd78-203">次の表は、Visual Basic に固有の属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="efd78-203">The following table lists the attributes that are specific to Visual Basic.</span></span>

|<span data-ttu-id="efd78-204">属性</span><span class="sxs-lookup"><span data-stu-id="efd78-204">Attribute</span></span>|<span data-ttu-id="efd78-205">目的</span><span class="sxs-lookup"><span data-stu-id="efd78-205">Purpose</span></span>|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="efd78-206">クラスを COM オブジェクトとして公開するようコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="efd78-206">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="efd78-207">モジュールに必要な修飾子のみを使用してモジュール メンバーにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="efd78-207">Allows module members to be accessed using only the qualification needed for the module.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="efd78-208">ファイルの入出力関数で使用される構造体の固定長文字列のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="efd78-208">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="efd78-209">ファイルの入出力関数で使用される構造体の固定配列のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="efd78-209">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|

### <a name="comclassattribute"></a><span data-ttu-id="efd78-210">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="efd78-210">COMClassAttribute</span></span>

<span data-ttu-id="efd78-211">`COMClassAttribute` を使用すると、Visual Basic から COM コンポーネントを作成するプロセスを省力化できます。</span><span class="sxs-lookup"><span data-stu-id="efd78-211">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="efd78-212">COM オブジェクトは、.NET Framework のアセンブリとは大幅に異なります。`COMClassAttribute` を使用せずに Visual Basic から COM オブジェクトを生成するためには多くの手順が必要となります。</span><span class="sxs-lookup"><span data-stu-id="efd78-212">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="efd78-213">`COMClassAttribute` でマークされたクラスに対しては、そうしたさまざまな手順がコンパイラによって自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="efd78-213">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>

### <a name="hidemodulenameattribute"></a><span data-ttu-id="efd78-214">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="efd78-214">HideModuleNameAttribute</span></span>

<span data-ttu-id="efd78-215">モジュールに必要な修飾子のみを使用してモジュール メンバーにアクセスできるようにするには、`HideModuleNameAttribute` を使用します。</span><span class="sxs-lookup"><span data-stu-id="efd78-215">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>

### <a name="vbfixedstringattribute"></a><span data-ttu-id="efd78-216">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="efd78-216">VBFixedStringAttribute</span></span>

<span data-ttu-id="efd78-217">Visual Basic で強制的に固定長文字列を作成するには、`VBFixedStringAttribute` を使用します。</span><span class="sxs-lookup"><span data-stu-id="efd78-217">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="efd78-218">文字列は既定では可変長であるため、文字列をファイルに格納するときにこの属性が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="efd78-218">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="efd78-219">その例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="efd78-219">The following code demonstrates this:</span></span>

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a><span data-ttu-id="efd78-220">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="efd78-220">VBFixedArrayAttribute</span></span>

<span data-ttu-id="efd78-221">サイズ固定の配列を宣言するには、`VBFixedArrayAttribute` を使用します。</span><span class="sxs-lookup"><span data-stu-id="efd78-221">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="efd78-222">Visual Basic の文字列と同様、配列も既定では可変長です。</span><span class="sxs-lookup"><span data-stu-id="efd78-222">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="efd78-223">データをシリアル化したりファイルに書き込んだりする際に、この属性が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="efd78-223">This attribute is useful when serializing or writing data to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="efd78-224">関連項目</span><span class="sxs-lookup"><span data-stu-id="efd78-224">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="efd78-225">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="efd78-225">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="efd78-226">属性</span><span class="sxs-lookup"><span data-stu-id="efd78-226">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="efd78-227">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efd78-227">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="efd78-228">リフレクションを使用した属性へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efd78-228">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
