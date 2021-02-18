---
description: '詳細情報: -addmodule'
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: ca08aa599003897e680240af21c4a0eb568e31d8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468292"
---
# <a name="-addmodule"></a><span data-ttu-id="ad515-103">-addmodule</span><span class="sxs-lookup"><span data-stu-id="ad515-103">-addmodule</span></span>

<span data-ttu-id="ad515-104">指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ad515-104">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad515-105">構文</span><span class="sxs-lookup"><span data-stu-id="ad515-105">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="ad515-106">引数</span><span class="sxs-lookup"><span data-stu-id="ad515-106">Arguments</span></span>  

 `fileList`  
 <span data-ttu-id="ad515-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="ad515-107">Required.</span></span> <span data-ttu-id="ad515-108">メタデータは含まれるが、アセンブリ マニフェストは含まれないファイルのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="ad515-108">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="ad515-109">ファイル名に空白が含まれる場合は、名前を二重引用符 ("") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="ad515-109">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad515-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="ad515-110">Remarks</span></span>  

 <span data-ttu-id="ad515-111">`fileList` パラメーターで指定するファイルは、`-target:module` オプションを使用して作成するか、`-target:module` と同等の別のコンパイラを使用して作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad515-111">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="ad515-112">`-addmodule` で追加したモジュールはすべて、実行時に出力ファイルと同じディレクトリに置かれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad515-112">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="ad515-113">つまり、コンパイル時には任意のディレクトリからモジュールを指定できますが、実行時にはアプリケーション ディレクトリにこのモジュールが置かれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad515-113">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="ad515-114">そうでない場合、<xref:System.TypeLoadException> エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ad515-114">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="ad515-115">`-addmodule` で `-target:module` 以外の [-target (Visual Basic)](target.md) オプションを (暗黙的または明示的に) 指定すると、`-addmodule` に渡すファイルはプロジェクトのアセンブリの一部になります。</span><span class="sxs-lookup"><span data-stu-id="ad515-115">If you specify (implicitly or explicitly) any[-target (Visual Basic)](target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="ad515-116">`-addmodule` で追加された 1 つ以上のファイルを含む出力ファイルを実行するには、アセンブリが必要です。</span><span class="sxs-lookup"><span data-stu-id="ad515-116">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="ad515-117">アセンブリが含まれるファイルからメタデータをインポートするには、[-reference (Visual Basic)](reference.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="ad515-117">Use [-reference (Visual Basic)](reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad515-118">`-addmodule` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad515-118">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad515-119">例</span><span class="sxs-lookup"><span data-stu-id="ad515-119">Example</span></span>  

 <span data-ttu-id="ad515-120">モジュールは、次のコード例で作成されます。</span><span class="sxs-lookup"><span data-stu-id="ad515-120">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="ad515-121">次のコードにより、モジュールの型がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="ad515-121">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="ad515-122">`t1` を実行すると、`802` が出力されます。</span><span class="sxs-lookup"><span data-stu-id="ad515-122">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad515-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad515-123">See also</span></span>

- [<span data-ttu-id="ad515-124">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="ad515-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ad515-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad515-125">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="ad515-126">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad515-126">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="ad515-127">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="ad515-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
