---
description: '詳細情報: -libpath'
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: cdc3f557e0d069930032ac3b0af7a0e88762189d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455679"
---
# <a name="-libpath"></a><span data-ttu-id="bc404-103">-libpath</span><span class="sxs-lookup"><span data-stu-id="bc404-103">-libpath</span></span>

<span data-ttu-id="bc404-104">参照アセンブリの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="bc404-104">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc404-105">構文</span><span class="sxs-lookup"><span data-stu-id="bc404-105">Syntax</span></span>  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="bc404-106">引数</span><span class="sxs-lookup"><span data-stu-id="bc404-106">Arguments</span></span>  
  
|<span data-ttu-id="bc404-107">用語</span><span class="sxs-lookup"><span data-stu-id="bc404-107">Term</span></span>|<span data-ttu-id="bc404-108">定義</span><span class="sxs-lookup"><span data-stu-id="bc404-108">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="bc404-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="bc404-109">Required.</span></span> <span data-ttu-id="bc404-110">参照されているアセンブリが現在の作業ディレクトリ (コンパイラの呼び出し元のディレクトリ) または共通言語ランタイムのシステム ディレクトリに見つからない場合に、コンパイラによって検索されるディレクトリのセミコロン区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="bc404-110">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="bc404-111">ディレクトリ名に空白が含まれている場合は、名前を二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="bc404-111">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc404-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="bc404-112">Remarks</span></span>  

 <span data-ttu-id="bc404-113">`-libpath` オプションでは、[-reference](reference.md) オプションによって参照されるアセンブリの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="bc404-113">The `-libpath` option specifies the location of assemblies referenced by the [-reference](reference.md) option.</span></span>  
  
 <span data-ttu-id="bc404-114">コンパイラは、完全に修飾されていないアセンブリ参照を次の順序で検索します。</span><span class="sxs-lookup"><span data-stu-id="bc404-114">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="bc404-115">現在の作業ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="bc404-115">Current working directory.</span></span> <span data-ttu-id="bc404-116">これは、コンパイラを起動したディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="bc404-116">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="bc404-117">共通言語ランタイムのシステム ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="bc404-117">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="bc404-118">`-libpath` によって指定されているディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="bc404-118">Directories specified by `-libpath`.</span></span>  
  
4. <span data-ttu-id="bc404-119">LIB 環境変数によって指定されているディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="bc404-119">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="bc404-120">`-libpath` オプションは付加的なものであり、複数回指定すると、前の値に追加されます。</span><span class="sxs-lookup"><span data-stu-id="bc404-120">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="bc404-121">アセンブリ参照を指定するには、`-reference` を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc404-121">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="bc404-122">Visual Studio 統合開発環境で -libpath を設定するには</span><span class="sxs-lookup"><span data-stu-id="bc404-122">To set -libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="bc404-123">1.**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="bc404-123">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bc404-124">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc404-124">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="bc404-125">2. **[参照]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc404-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="bc404-126">3. **[参照パス...]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc404-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="bc404-127">4. **[参照パス]** ダイアログ ボックスで、 **[フォルダー]** ボックスにディレクトリ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="bc404-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="bc404-128">5. **[フォルダーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc404-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bc404-129">例</span><span class="sxs-lookup"><span data-stu-id="bc404-129">Example</span></span>  

 <span data-ttu-id="bc404-130">次のコードでは、`T2.vb` をコンパイルして .exe ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc404-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="bc404-131">コンパイラでは、作業ディレクトリ、C: ドライブのルート ディレクトリ、およびアセンブリ参照の C: ドライブの New Assemblies ディレクトリ内を検索します。</span><span class="sxs-lookup"><span data-stu-id="bc404-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc404-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc404-132">See also</span></span>

- [<span data-ttu-id="bc404-133">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="bc404-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="bc404-134">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="bc404-134">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="bc404-135">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="bc404-135">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
