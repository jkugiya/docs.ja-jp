---
description: '詳細情報: 参照と Imports ステートメント (Visual Basic)'
title: 参照と Imports ステートメント
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 3ca685d33f69224a6eea324d7357be4b5203eb45
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468240"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="36600-103">参照と Imports ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36600-103">References and the Imports Statement (Visual Basic)</span></span>

<span data-ttu-id="36600-104">プロジェクトで外部オブジェクトを使用できるようにするには、 **[プロジェクト]** メニューの **[参照の追加]** コマンドを選択します。</span><span class="sxs-lookup"><span data-stu-id="36600-104">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="36600-105">Visual Basic の参照ではアセンブリを参照できます。アセンブリはタイプ ライブラリに似ていますが、より多くの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="36600-105">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="36600-106">Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="36600-106">The Imports Statement</span></span>  

 <span data-ttu-id="36600-107">アセンブリには、1 つ以上の名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="36600-107">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="36600-108">アセンブリへの参照を追加するときに、モジュール内でそのアセンブリの名前空間の可視性を制御する `Imports` ステートメントをモジュールに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="36600-108">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="36600-109">`Imports` ステートメントは、一意の参照を指定するために必要な名前空間の部分だけを使用できるようにする、スコープ コンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="36600-109">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="36600-110">`Imports` ステートメントの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="36600-110">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="36600-111">`Aliasname` は、インポートされた名前空間を参照するためにコード内で使用できる短い名前を参照します。</span><span class="sxs-lookup"><span data-stu-id="36600-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="36600-112">`Namespace` は、プロジェクト参照、プロジェクト内の定義、または前の `Imports` ステートメントを通じて使用できる名前空間です。</span><span class="sxs-lookup"><span data-stu-id="36600-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="36600-113">モジュールには、`Imports` ステートメントをいくつでも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="36600-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="36600-114">これらは、`Option` ステートメント (存在する場合) の後の、他のコードの前に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36600-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36600-115">`Imports` ステートメントまたは `Declare` ステートメントとプロジェクト参照を混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="36600-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="36600-116">プロジェクト参照は、アセンブリ内のオブジェクトなどの外部オブジェクトを、Visual Basic プロジェクトで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="36600-116">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="36600-117">`Imports` ステートメントは、プロジェクト参照へのアクセスを簡素化するために使用されますが、これらのオブジェクトへのアクセスは提供しません。</span><span class="sxs-lookup"><span data-stu-id="36600-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="36600-118">`Declare` ステートメントは、ダイナミックリンク ライブラリ (DLL) 内の外部プロシージャへの参照を宣言するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="36600-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="36600-119">Imports ステートメントでの別名の使用</span><span class="sxs-lookup"><span data-stu-id="36600-119">Using Aliases with the Imports Statement</span></span>  

 <span data-ttu-id="36600-120">`Imports` ステートメントにより、参照の完全修飾名を明示的に入力する必要がなくなるため、クラスのメソッドに簡単にアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="36600-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="36600-121">別名を使用すると、名前空間の一部分にのみ、わかりやすい名前を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="36600-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="36600-122">たとえば、単一のテキストが複数行に表示されるキャリッジ リターン/ライン フィード シーケンスは、<xref:Microsoft.VisualBasic?displayProperty=nameWithType> 名前空間の <xref:Microsoft.VisualBasic.ControlChars> モジュールの一部です。</span><span class="sxs-lookup"><span data-stu-id="36600-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="36600-123">別名なしで、この定数をプログラムで使用するには、次のコードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36600-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="36600-124">`Imports` ステートメントは、常にモジュール内の `Option` ステートメントの直後の最初の行である必要があります。</span><span class="sxs-lookup"><span data-stu-id="36600-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="36600-125">次のコード フラグメントは、別名をインポートして <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> モジュールに割り当てる方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="36600-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="36600-126">この名前空間への今後の参照は、かなり短くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="36600-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="36600-127">`Imports` ステートメントに別名が含まれていない場合、インポートされた名前空間内で定義されている要素を、修飾せずにモジュールで使用できます。</span><span class="sxs-lookup"><span data-stu-id="36600-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="36600-128">別名が指定されている場合は、その名前空間に含まれる名前の修飾子として使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36600-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36600-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="36600-129">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="36600-130">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="36600-130">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="36600-131">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="36600-131">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="36600-132">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="36600-132">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
