---
description: '詳細情報: -keycontainer'
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: d8b83162d9404eb2ce80e5e531457360b040f27d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436813"
---
# <a name="-keycontainer"></a><span data-ttu-id="b4319-103">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="b4319-103">-keycontainer</span></span>

<span data-ttu-id="b4319-104">アセンブリに厳密な名前を付けるキー ペアのキー コンテナー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4319-104">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4319-105">構文</span><span class="sxs-lookup"><span data-stu-id="b4319-105">Syntax</span></span>  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="b4319-106">引数</span><span class="sxs-lookup"><span data-stu-id="b4319-106">Arguments</span></span>  
  
|<span data-ttu-id="b4319-107">用語</span><span class="sxs-lookup"><span data-stu-id="b4319-107">Term</span></span>|<span data-ttu-id="b4319-108">定義</span><span class="sxs-lookup"><span data-stu-id="b4319-108">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="b4319-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="b4319-109">Required.</span></span> <span data-ttu-id="b4319-110">キーが格納されているコンテナー ファイル。</span><span class="sxs-lookup"><span data-stu-id="b4319-110">Container file that contains the key.</span></span> <span data-ttu-id="b4319-111">ファイル名に空白が含まれている場合は、名前を二重引用符 ("") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="b4319-111">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4319-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="b4319-112">Remarks</span></span>  

 <span data-ttu-id="b4319-113">コンパイラにより、アセンブリ マニフェストに公開キーが挿入され、秘密キーで最終アセンブリに署名されて、共有可能なコンポーネントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b4319-113">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="b4319-114">キー ファイルを生成するには、コマンド ラインで「`sn -k file`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b4319-114">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="b4319-115">`-i` オプションでは、キー ペアがコンテナーにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b4319-115">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="b4319-116">詳細については、「[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4319-116">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="b4319-117">`-target:module` を指定してコンパイルした場合は、キー ファイルの名前はモジュールに保持され、[-addmodule](addmodule.md) を使用してコンパイルして作成したアセンブリに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="b4319-117">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="b4319-118">このオプションは、任意の Microsoft Intermediate Language (MSIL) モジュールのソース コードで、カスタム属性 (<xref:System.Reflection.AssemblyKeyNameAttribute>) として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b4319-118">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="b4319-119">また、暗号化情報を [-keyfile](keyfile.md) でコンパイラに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b4319-119">You can also pass your encryption information to the compiler with [-keyfile](keyfile.md).</span></span> <span data-ttu-id="b4319-120">部分的に署名されたアセンブリを作成する場合は、[-delaysign](delaysign.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="b4319-120">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="b4319-121">アセンブリへの署名の詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../standard/assembly/create-use-strong-named.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4319-121">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4319-122">`-keycontainer` オプションは、Visual Studio 開発環境内からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b4319-122">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4319-123">例</span><span class="sxs-lookup"><span data-stu-id="b4319-123">Example</span></span>  

 <span data-ttu-id="b4319-124">次のコードでは、ソース ファイル `Input.vb` がコンパイルされ、キー コンテナーが指定されます。</span><span class="sxs-lookup"><span data-stu-id="b4319-124">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4319-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4319-125">See also</span></span>

- [<span data-ttu-id="b4319-126">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="b4319-126">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="b4319-127">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="b4319-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b4319-128">-keyfile</span><span class="sxs-lookup"><span data-stu-id="b4319-128">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="b4319-129">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="b4319-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
