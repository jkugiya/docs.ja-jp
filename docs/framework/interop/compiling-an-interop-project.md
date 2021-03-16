---
title: 相互運用プロジェクトのコンパイル
description: COM 相互運用機能プロジェクトをコンパイルする方法を確認します。インポートされた COM 型を含む 1 つ以上のアセンブリを参照する場合は、マネージド プロジェクトと同様にコンパイルされます。
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
ms.openlocfilehash: 9621d2e060db38549dcaab2e55e7645179831767
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480170"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="2d94c-103">相互運用プロジェクトのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2d94c-103">Compiling an Interop Project</span></span>

<span data-ttu-id="2d94c-104">インポートされた COM 型を含む 1 つ以上のアセンブリを参照する COM 相互運用プロジェクトは、他のマネージド プロジェクトと同じようにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="2d94c-104">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="2d94c-105">相互運用機能アセンブリは、Visual Studio などの開発環境で参照できます。コマンド ライン コンパイラを使用して参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="2d94c-105">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="2d94c-106">どちらの場合でも、正常にコンパイルするには、相互運用機能アセンブリを、その他のプロジェクト ファイルと同じディレクトリに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d94c-106">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="2d94c-107">相互運用機能アセンブリを参照する方法には、次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="2d94c-107">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="2d94c-108">埋め込まれた相互運用機能型:.NET Framework 4 および Visual Studio 2010 以降では、相互運用機能アセンブリから実行可能ファイルに型情報を埋め込むようにコンパイラに指示できます。</span><span class="sxs-lookup"><span data-stu-id="2d94c-108">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="2d94c-109">この手法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2d94c-109">This is the recommended technique.</span></span>

- <span data-ttu-id="2d94c-110">相互運用機能アセンブリの配置:相互運用機能アセンブリへの標準の参照を作成できます。</span><span class="sxs-lookup"><span data-stu-id="2d94c-110">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="2d94c-111">この場合、アプリケーションで相互運用機能アセンブリを展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d94c-111">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="2d94c-112">この 2 つの手法の違いの詳細については、「[Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))」(マネージド コードでの COM 型の使用) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d94c-112">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="2d94c-113">Visual Studio での相互運用機能型の埋め込みについては、「[チュートリアル:Visual Studio でマネージド アセンブリからの型を埋め込む](../../standard/assembly/embed-types-visual-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d94c-113">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="2d94c-114">コマンド ライン コンパイラを使用して相互運用アセンブリを参照し、実行可能ファイルに型情報を埋め込むには、[-link (C# コンパイラ オプション)](../../csharp/language-reference/compiler-options/inputs.md#embedinteroptypes) または [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) コンパイラ スイッチを使用して、相互運用アセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2d94c-114">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/inputs.md#embedinteroptypes) or the [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="2d94c-115">Visual C++ アプリケーションは型情報を埋め込むことはできませんが、型情報を埋め込むことができるアプリケーションまたはアドインと相互運用できます。</span><span class="sxs-lookup"><span data-stu-id="2d94c-115">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="2d94c-116">配置時にプライマリ相互運用機能アセンブリを含むアプリケーションをコンパイルするには、 **/reference** コンパイラ スイッチを使用して、相互運用機能アセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2d94c-116">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d94c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d94c-117">See also</span></span>

- [<span data-ttu-id="2d94c-118">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="2d94c-118">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="2d94c-119">言語への非依存性、および言語非依存コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2d94c-119">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="2d94c-120">[マネージド コードでの COM 型の使用](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2d94c-120">[Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="2d94c-121">チュートリアル: Visual Studio でマネージド アセンブリからの型を埋め込む</span><span class="sxs-lookup"><span data-stu-id="2d94c-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="2d94c-122">タイプ ライブラリのアセンブリとしてのインポート</span><span class="sxs-lookup"><span data-stu-id="2d94c-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
