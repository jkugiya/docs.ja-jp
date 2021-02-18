---
description: '詳細情報: -keyfile'
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 6d19f136d5961e8a933380164a3a77055e1da329
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466940"
---
# <a name="-keyfile"></a><span data-ttu-id="8238a-103">-keyfile</span><span class="sxs-lookup"><span data-stu-id="8238a-103">-keyfile</span></span>

<span data-ttu-id="8238a-104">アセンブリに厳密な名前を付けるキーまたはキー ペアを含むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="8238a-104">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8238a-105">構文</span><span class="sxs-lookup"><span data-stu-id="8238a-105">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="8238a-106">引数</span><span class="sxs-lookup"><span data-stu-id="8238a-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="8238a-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="8238a-107">Required.</span></span> <span data-ttu-id="8238a-108">キーが含まれるファイル。</span><span class="sxs-lookup"><span data-stu-id="8238a-108">File that contains the key.</span></span> <span data-ttu-id="8238a-109">ファイル名に空白が含まれている場合は、名前を二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="8238a-109">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8238a-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="8238a-110">Remarks</span></span>  

 <span data-ttu-id="8238a-111">コンパイラでは、アセンブリ マニフェストに公開キーを挿入してから、秘密キーで最終的なアセンブリに署名します。</span><span class="sxs-lookup"><span data-stu-id="8238a-111">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="8238a-112">キー ファイルを生成するには、コマンド ラインで「`sn -k file`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8238a-112">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="8238a-113">詳細については、「[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8238a-113">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="8238a-114">`-target:module` を指定してコンパイルした場合は、キー ファイルの名前がモジュールに保持され、[-addmodule](addmodule.md) でアセンブリをコンパイルすると作成されるアセンブリに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="8238a-114">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="8238a-115">また、暗号化情報を [-keycontainer](keycontainer.md) でコンパイラに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="8238a-115">You can also pass your encryption information to the compiler with [-keycontainer](keycontainer.md).</span></span> <span data-ttu-id="8238a-116">部分的に署名されたアセンブリを作成する場合は、[-delaysign](delaysign.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="8238a-116">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="8238a-117">このオプションは、任意の Microsoft Intermediate Language モジュールのソース コードで、カスタム属性 (<xref:System.Reflection.AssemblyKeyFileAttribute>) として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="8238a-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="8238a-118">同じコンパイルで (コマンドライン オプションまたはカスタム属性によって) `-keyfile` と [-keycontainer](keycontainer.md) の両方が指定されている場合、コンパイラでは最初にキー コンテナーが試されます。</span><span class="sxs-lookup"><span data-stu-id="8238a-118">In case both `-keyfile` and [-keycontainer](keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="8238a-119">それが成功すると、アセンブリはキー コンテナーの情報で署名されます。</span><span class="sxs-lookup"><span data-stu-id="8238a-119">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="8238a-120">コンパイラでは、キー コンテナーが見つからない場合、`-keyfile` で指定されたファイルが試されます。</span><span class="sxs-lookup"><span data-stu-id="8238a-120">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="8238a-121">これが成功すると、アセンブリはキー ファイルの情報で署名され、キー情報はキー コンテナーにインストールされるため (`sn -i` と同様)、次のコンパイル時にはキー コンテナーが有効になります。</span><span class="sxs-lookup"><span data-stu-id="8238a-121">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="8238a-122">キー ファイルには公開キーだけが含まれる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8238a-122">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="8238a-123">アセンブリの署名の詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../standard/assembly/create-use-strong-named.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8238a-123">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8238a-124">`-keyfile` オプションは、Visual Studio 開発環境内からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8238a-124">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="8238a-125">例</span><span class="sxs-lookup"><span data-stu-id="8238a-125">Example</span></span>

<span data-ttu-id="8238a-126">次のコードでは、ソース ファイル `Input.vb` をコンパイルし、キー ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="8238a-126">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="8238a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="8238a-127">See also</span></span>

- [<span data-ttu-id="8238a-128">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="8238a-128">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="8238a-129">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="8238a-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="8238a-130">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8238a-130">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="8238a-131">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="8238a-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
