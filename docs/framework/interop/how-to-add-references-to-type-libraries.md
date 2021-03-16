---
title: '方法: タイプ ライブラリへの参照を追加する'
description: Visual Studio で、またはコマンドラインでのコンパイルのためにタイプ ライブラリへの参照を追加する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: b5e58c5943eba8db7497b4db56bfbd99b17b1043
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477626"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="e653a-103">方法: タイプ ライブラリへの参照を追加する</span><span class="sxs-lookup"><span data-stu-id="e653a-103">How to: Add References to Type Libraries</span></span>

<span data-ttu-id="e653a-104">Visual Studio は、タイプ ライブラリに参照を追加する際に、メタデータを含む相互運用機能アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="e653a-104">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="e653a-105">プライマリ相互運用機能アセンブリが使用可能な場合、Visual Studio では、新しい相互運用機能アセンブリを生成する前に既存のアセンブリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e653a-105">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="e653a-106">Visual Studio でタイプ ライブラリへの参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="e653a-106">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="e653a-107">Windows Setup.exe ファイルで COM DLL ファイルまたは EXE ファイルがインストールされない場合は、このファイルをコンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="e653a-107">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="e653a-108">**[プロジェクト]** 、 **[参照の追加]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="e653a-108">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="e653a-109">参照マネージャーで、 **[COM]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e653a-109">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="e653a-110">一覧からタイプ ライブラリを選択するか、.tlb ファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="e653a-110">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="e653a-111">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e653a-111">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="e653a-112">ソリューション エクスプローラーで、追加した参照のショートカット メニューを開き、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e653a-112">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="e653a-113">**[プロパティ]** ウィンドウで、 **[相互運用機能型の埋め込み]** プロパティが **[True]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e653a-113">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="e653a-114">その結果、Visual Studio により、COM 型の型情報が実行可能ファイルに埋め込まれ、アプリでプライマリ相互運用機能アセンブリを配置する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="e653a-114">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e653a-115">メニュー オプションおよびダイアログ ボックス オプションは、使用中の Visula Studio のバージョンによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e653a-115">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="e653a-116">コマンド ライン コンパイルのために参照をタイプ ライブラリに追加するには</span><span class="sxs-lookup"><span data-stu-id="e653a-116">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="e653a-117">「[方法: 相互運用機能アセンブリをタイプ ライブラリから生成する](how-to-generate-interop-assemblies-from-type-libraries.md)」の説明に従って、相互運用機能アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="e653a-117">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="e653a-118">相互運用アセンブリ名を指定して [-link (C# コンパイラ オプション)](../../csharp/language-reference/compiler-options/inputs.md#embedinteroptypes) または [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) コンパイラ オプションを使用し、COM 型の型情報を実行可能ファイルに埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="e653a-118">Use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/inputs.md#embedinteroptypes) or [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e653a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e653a-119">See also</span></span>

- [<span data-ttu-id="e653a-120">タイプ ライブラリのアセンブリとしてのインポート</span><span class="sxs-lookup"><span data-stu-id="e653a-120">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="e653a-121">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="e653a-121">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="e653a-122">チュートリアル: Visual Studio でマネージド アセンブリからの型を埋め込む</span><span class="sxs-lookup"><span data-stu-id="e653a-122">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="e653a-123">-link (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="e653a-123">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/inputs.md#embedinteroptypes)
- [<span data-ttu-id="e653a-124">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e653a-124">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
