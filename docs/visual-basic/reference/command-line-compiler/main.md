---
description: '詳細情報: -main'
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 4c225c5a0030de6de0aaa510080a586272aa920b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455666"
---
# <a name="-main"></a><span data-ttu-id="ea152-103">-main</span><span class="sxs-lookup"><span data-stu-id="ea152-103">-main</span></span>

<span data-ttu-id="ea152-104">`Sub Main` プロシージャを格納するクラスまたはモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="ea152-104">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea152-105">構文</span><span class="sxs-lookup"><span data-stu-id="ea152-105">Syntax</span></span>  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="ea152-106">引数</span><span class="sxs-lookup"><span data-stu-id="ea152-106">Arguments</span></span>  

 `location`  
 <span data-ttu-id="ea152-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="ea152-107">Required.</span></span> <span data-ttu-id="ea152-108">プログラムの起動時に呼び出される `Sub Main` プロシージャを含むクラスまたはモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="ea152-108">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="ea152-109">この形式は、 **-main:module** または **-main:namespace.module** である場合があります。</span><span class="sxs-lookup"><span data-stu-id="ea152-109">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea152-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="ea152-110">Remarks</span></span>  

 <span data-ttu-id="ea152-111">このオプションは、実行可能ファイルまたは Windows 実行可能プログラムを作成するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="ea152-111">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="ea152-112">**-main** オプションを省略した場合、すべてのパブリック クラスとモジュールから、有効な共有 `Sub Main` がコンパイラにより検索されます。</span><span class="sxs-lookup"><span data-stu-id="ea152-112">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="ea152-113">`Main` プロシージャのさまざまな形式については、「[Visual Basic の Main プロシージャ](../../programming-guide/program-structure/main-procedure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea152-113">See [Main Procedure in Visual Basic](../../programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="ea152-114">`location` が <xref:System.Windows.Forms.Form> から継承されるクラスである場合にクラスに `Main` プロシージャがないとき、アプリケーションを起動する既定の `Main` プロシージャがコンパイラによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="ea152-114">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="ea152-115">これにより、開発環境で作成されたコードを、コマンド ラインでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="ea152-115">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="ea152-116">Visual Studio 統合開発環境で -main を設定するには</span><span class="sxs-lookup"><span data-stu-id="ea152-116">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="ea152-117">**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="ea152-117">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ea152-118">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea152-118">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="ea152-119">**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea152-119">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="ea152-120">**[アプリケーション フレームワークを有効にする]** チェック ボックスがオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ea152-120">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="ea152-121">**[スタートアップ オブジェクト]** ボックスの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="ea152-121">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea152-122">例</span><span class="sxs-lookup"><span data-stu-id="ea152-122">Example</span></span>  

 <span data-ttu-id="ea152-123">次のコードでは、`Sub Main` プロシージャが `Test2` クラスにあることが指定され、`T2.vb` と `T3.vb` がコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ea152-123">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea152-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea152-124">See also</span></span>

- [<span data-ttu-id="ea152-125">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="ea152-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ea152-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea152-126">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="ea152-127">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="ea152-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="ea152-128">Visual Basic の Main プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ea152-128">Main Procedure in Visual Basic</span></span>](../../programming-guide/program-structure/main-procedure.md)
