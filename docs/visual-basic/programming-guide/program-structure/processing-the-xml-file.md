---
description: '詳細情報: XML ファイルの処理 (Visual Basic)'
title: XML ファイルの処理
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 2314e7dafbd747f9a19b73d06d71c73631e53861
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468396"
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="11590-103">XML ファイルの処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11590-103">Processing the XML File (Visual Basic)</span></span>

<span data-ttu-id="11590-104">コンパイラは、ドキュメントを生成するためにタグ付けされたコードのコンストラクトごとに、ID 文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="11590-104">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="11590-105">(コードをタグ付けする方法については、[XML ドキュメント コメントのタグ](../../language-reference/xmldoc/index.md)に関する記事をご覧ください。)ID 文字列によって、コンストラクトは一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="11590-105">(For information on how to tag your code, see [XML Comment Tags](../../language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="11590-106">XML ファイルを処理するプログラムでは、ID 文字列を使用して、対応する .NET Framework のメタデータまたはリフレクション項目を識別できます。</span><span class="sxs-lookup"><span data-stu-id="11590-106">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.</span></span>  
  
 <span data-ttu-id="11590-107">XML ファイルは、コードの階層表現ではなく、要素ごとに生成された ID を持つフラット リストです。</span><span class="sxs-lookup"><span data-stu-id="11590-107">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="11590-108">コンパイラは、次の規則に基づいて ID 文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="11590-108">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
- <span data-ttu-id="11590-109">文字列に空白は配置されません。</span><span class="sxs-lookup"><span data-stu-id="11590-109">No white space is placed in the string.</span></span>  
  
- <span data-ttu-id="11590-110">ID 文字列の最初の部分は、単一の文字とそれに続くコロンで識別されるメンバーの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="11590-110">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="11590-111">次のメンバー型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="11590-111">The following member types are used.</span></span>  
  
|<span data-ttu-id="11590-112">文字</span><span class="sxs-lookup"><span data-stu-id="11590-112">Character</span></span>|<span data-ttu-id="11590-113">説明</span><span class="sxs-lookup"><span data-stu-id="11590-113">Description</span></span>|  
|---|---|  
|<span data-ttu-id="11590-114">N</span><span class="sxs-lookup"><span data-stu-id="11590-114">N</span></span>|<span data-ttu-id="11590-115">namespace</span><span class="sxs-lookup"><span data-stu-id="11590-115">namespace</span></span><br /><br /> <span data-ttu-id="11590-116">ドキュメント コメントを名前空間に追加することはできませんが、名前空間への CREF 参照は作成できます (サポートされている場合)。</span><span class="sxs-lookup"><span data-stu-id="11590-116">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="11590-117">T</span><span class="sxs-lookup"><span data-stu-id="11590-117">T</span></span>|<span data-ttu-id="11590-118">型: `Class`、`Module`、`Interface`、`Structure`、`Enum`、`Delegate`</span><span class="sxs-lookup"><span data-stu-id="11590-118">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="11590-119">F</span><span class="sxs-lookup"><span data-stu-id="11590-119">F</span></span>|<span data-ttu-id="11590-120">フィールド: `Dim`</span><span class="sxs-lookup"><span data-stu-id="11590-120">field: `Dim`</span></span>|  
|<span data-ttu-id="11590-121">P</span><span class="sxs-lookup"><span data-stu-id="11590-121">P</span></span>|<span data-ttu-id="11590-122">プロパティ: `Property` (既定のプロパティを含む)</span><span class="sxs-lookup"><span data-stu-id="11590-122">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="11590-123">M</span><span class="sxs-lookup"><span data-stu-id="11590-123">M</span></span>|<span data-ttu-id="11590-124">メソッド: `Sub`、`Function`、`Declare`、`Operator`</span><span class="sxs-lookup"><span data-stu-id="11590-124">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="11590-125">E</span><span class="sxs-lookup"><span data-stu-id="11590-125">E</span></span>|<span data-ttu-id="11590-126">イベント: `Event`</span><span class="sxs-lookup"><span data-stu-id="11590-126">event: `Event`</span></span>|  
|<span data-ttu-id="11590-127">!</span><span class="sxs-lookup"><span data-stu-id="11590-127">!</span></span>|<span data-ttu-id="11590-128">エラー文字列</span><span class="sxs-lookup"><span data-stu-id="11590-128">error string</span></span><br /><br /> <span data-ttu-id="11590-129">あとに続く文字列で、エラーの情報を示します。</span><span class="sxs-lookup"><span data-stu-id="11590-129">The rest of the string provides information about the error.</span></span> <span data-ttu-id="11590-130">Visual Basic コンパイラは、解決できないリンクのエラー情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="11590-130">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
- <span data-ttu-id="11590-131">`String` の 2 番目の部分は、名前空間のルートから始まる、項目の完全修飾名です。</span><span class="sxs-lookup"><span data-stu-id="11590-131">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="11590-132">項目の名前、それを囲む型、名前空間は、ピリオドで区切られます。</span><span class="sxs-lookup"><span data-stu-id="11590-132">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="11590-133">項目自体の名前にピリオドが含まれている場合、それらは番号記号 (#) に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="11590-133">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="11590-134">項目の名前に番号記号がないことが前提です。</span><span class="sxs-lookup"><span data-stu-id="11590-134">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="11590-135">たとえば、`String` コンストラクターの完全修飾名は `System.String.#ctor` になります。</span><span class="sxs-lookup"><span data-stu-id="11590-135">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
- <span data-ttu-id="11590-136">プロパティおよびメソッドについては、メソッドに引数がある場合は、引数のリストをかっこで囲み、メソッドに続けて指定します。</span><span class="sxs-lookup"><span data-stu-id="11590-136">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="11590-137">引数がない場合は、かっこはありません。</span><span class="sxs-lookup"><span data-stu-id="11590-137">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="11590-138">引数はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="11590-138">The arguments are separated by commas.</span></span> <span data-ttu-id="11590-139">各引数のエンコードは、.NET Framework のシグネチャでのエンコード方法にそのまま従います。</span><span class="sxs-lookup"><span data-stu-id="11590-139">The encoding of each argument follows directly how it is encoded in a .NET Framework signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11590-140">例</span><span class="sxs-lookup"><span data-stu-id="11590-140">Example</span></span>  

 <span data-ttu-id="11590-141">次のコードは、クラスとそのメンバーの ID 文字列を生成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="11590-141">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="11590-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="11590-142">See also</span></span>

- [<span data-ttu-id="11590-143">-doc</span><span class="sxs-lookup"><span data-stu-id="11590-143">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="11590-144">方法: XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="11590-144">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
