---
title: '方法: 厳密な名前でアセンブリに署名する'
description: この記事では、[署名] タブ、アセンブリ リンカー、アセンブリ属性、またはコンパイラ オプションを使用して、厳密な名前で .NET アセンブリに署名する方法について説明します。
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET], signing
- assemblies [.NET], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: f66b21c7b912cdf1b5e77a91cecd38580e495a51
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259656"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="f84ea-103">方法: 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="f84ea-103">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="f84ea-104">.NET Core では厳密な名前のアセンブリがサポートされており、.NET Core ライブラリ内のすべてのアセンブリは署名されていますが、ほとんどのサードパーティ アセンブリには厳密な名前は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f84ea-104">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="f84ea-105">詳細については、GitHub の「[厳密な名前の署名](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f84ea-105">For more information, see [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="f84ea-106">厳密な名前でアセンブリに署名するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="f84ea-106">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="f84ea-107">Visual Studio でプロジェクトの **[プロパティ]** ダイアログ ボックスにある **[署名]** タブを使用する。</span><span class="sxs-lookup"><span data-stu-id="f84ea-107">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="f84ea-108">これは、厳密な名前でアセンブリに署名するための最も簡単で便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="f84ea-108">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="f84ea-109">[アセンブリ リンカー (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) を使用して、.NET Framework のコード モジュール ( *.netmodule* ファイル) をキー ファイルにリンクする。</span><span class="sxs-lookup"><span data-stu-id="f84ea-109">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="f84ea-110">アセンブリ属性を使用して、厳密な名前情報をコードに挿入する。</span><span class="sxs-lookup"><span data-stu-id="f84ea-110">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="f84ea-111">使用するキー ファイルが配置されている場所に応じて、 <xref:System.Reflection.AssemblyKeyFileAttribute> または <xref:System.Reflection.AssemblyKeyNameAttribute> 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f84ea-111">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="f84ea-112">コンパイラ オプションを使用する。</span><span class="sxs-lookup"><span data-stu-id="f84ea-112">By using compiler options.</span></span>  
  
 <span data-ttu-id="f84ea-113">厳密な名前でアセンブリに署名するには、暗号キー ペアが必要です。</span><span class="sxs-lookup"><span data-stu-id="f84ea-113">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="f84ea-114">キー ペアの作成の詳細については、「[方法:公開キーと秘密キーのキー ペアを作成する](create-public-private-key-pair.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f84ea-114">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="f84ea-115">Visual Studio を使用してアセンブリを作成し、厳密な名前でそのアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="f84ea-115">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="f84ea-116">**ソリューション エクスプローラー** で、プロジェクトのショートカット メニューを開き、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-116">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="f84ea-117">**[署名]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-117">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="f84ea-118">**[アセンブリの署名]** ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-118">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="f84ea-119">**[厳密な名前のキー ファイルを選択してください]** ボックスで **[参照]** をクリックし、キー ファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-119">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="f84ea-120">新しいキー ファイルを作成するには、 **[新規作成]** を選択し、 **[厳密な名前キーの作成]** ダイアログ ボックスでその名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-120">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f84ea-121">[アセンブリの遅延署名](delay-sign.md)を行うには、公開キー ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-121">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="f84ea-122">アセンブリ リンカーを使用してアセンブリを作成し、厳密な名前でそのアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="f84ea-122">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="f84ea-123">[開発者コマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を開き、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-123">Open a [developer command-line shell](/visualstudio/ide/reference/command-prompt-powershell), and enter the following command:</span></span>  

<span data-ttu-id="f84ea-124">**al** **/out:** \<*assemblyName*> *\<moduleName>* **/keyfile:** \<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="f84ea-124">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="f84ea-125">この場合、</span><span class="sxs-lookup"><span data-stu-id="f84ea-125">Where:</span></span>  

- <span data-ttu-id="f84ea-126">*assemblyName* は、アセンブリ リンカーが生成する、厳密な名前で署名されたアセンブリ ( *.dll* ファイルまたは *.exe* ファイル) の名前です。</span><span class="sxs-lookup"><span data-stu-id="f84ea-126">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="f84ea-127">*moduleName* は、1 つ以上の型を含む、.NET Framework コード モジュール ( *.netmodule* ファイル) の名前です。</span><span class="sxs-lookup"><span data-stu-id="f84ea-127">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="f84ea-128">C# または Visual Basic で `/target:module` スイッチを使ってコードをコンパイルすることにより、 *.netmodule* ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f84ea-128">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="f84ea-129">*keyfileName* は、キー ペアを格納しているコンテナーまたはファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="f84ea-129">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="f84ea-130">アセンブリ リンカーは、現在のディレクトリとの関連で相対パスを解釈します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-130">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="f84ea-131">次の例では、キー ファイル *sgKey.snk* を使用して、厳密な名前でアセンブリ *MyAssembly.dll* に署名します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-131">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="f84ea-132">このツールの詳細については、「 [アセンブリ リカー](../../framework/tools/al-exe-assembly-linker.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f84ea-132">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="f84ea-133">属性を使用して厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="f84ea-133">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="f84ea-134"><xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> または <xref:System.Reflection.AssemblyKeyNameAttribute> 属性をソース コード ファイルに追加して、厳密な名前でアセンブリに署名するときに使用するキー ペアを格納するファイルまたはコンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  

2. <span data-ttu-id="f84ea-135">ソース コード ファイルを通常どおりにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f84ea-135">Compile the source code file normally.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="f84ea-136">C# および Visual Basic コンパイラは、ソース コードで <xref:System.Reflection.AssemblyKeyFileAttribute> または <xref:System.Reflection.AssemblyKeyNameAttribute> 属性が見つかった場合、コンパイラ警告を発行します (CS1699 と BC41008)。</span><span class="sxs-lookup"><span data-stu-id="f84ea-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="f84ea-137">この警告は無視してかまいません。</span><span class="sxs-lookup"><span data-stu-id="f84ea-137">You can ignore the warnings.</span></span>  

<span data-ttu-id="f84ea-138">次の例は、*keyfile.snk* という名前のキー ファイルを指定して、<xref:System.Reflection.AssemblyKeyFileAttribute> 属性を使用します。このキー ファイルは、アセンブリがコンパイルされるディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="f84ea-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="f84ea-139">ソース ファイルのコンパイル時に、アセンブリに遅延署名することもできます。</span><span class="sxs-lookup"><span data-stu-id="f84ea-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="f84ea-140">詳細については、「[アセンブリへの遅延署名](delay-sign.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f84ea-140">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="f84ea-141">コンパイラを使用して厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="f84ea-141">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="f84ea-142">C# と Visual Basic では `/keyfile` または `/delaysign` コンパイラ オプションを使用し、C++ では `/KEYFILE` または `/DELAYSIGN` リンカー オプションを使用して、ソース コード ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f84ea-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="f84ea-143">オプション名の後に、コロンと、キー ファイルの名前を追加します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="f84ea-144">コマンド ライン コンパイラを使用する場合は、ソース コード ファイルを格納するディレクトリにキー ファイルをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="f84ea-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="f84ea-145">遅延署名については、「[アセンブリへの遅延署名](delay-sign.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f84ea-145">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="f84ea-146">次の例は、C# コンパイラを使用し、アセンブリ *UtilityLibrary.dll* にキー ファイル *sgKey.snk* を使用して厳密な名前で署名します。</span><span class="sxs-lookup"><span data-stu-id="f84ea-146">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="f84ea-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="f84ea-147">See also</span></span>

- [<span data-ttu-id="f84ea-148">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="f84ea-148">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="f84ea-149">方法: 公開キーと秘密キーのキー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="f84ea-149">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="f84ea-150">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="f84ea-150">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="f84ea-151">アセンブリへの遅延署名</span><span class="sxs-lookup"><span data-stu-id="f84ea-151">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="f84ea-152">アセンブリおよびマニフェストへの署名の管理</span><span class="sxs-lookup"><span data-stu-id="f84ea-152">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- <span data-ttu-id="f84ea-153">[[署名] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/signing-page-project-designer)</span><span class="sxs-lookup"><span data-stu-id="f84ea-153">[Signing page, Project Designer](/visualstudio/ide/reference/signing-page-project-designer)</span></span>
