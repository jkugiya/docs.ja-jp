---
description: '詳細情報: ドキュメント コメントとして推奨される XML タグ (Visual Basic)'
title: ドキュメント コメントとして推奨される XML タグ
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 5d3451d98b66817de143cfbddbcb6121de57ca8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787449"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="905b0-103">ドキュメント コメントとして推奨される XML タグ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="905b0-103">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>

<span data-ttu-id="905b0-104">Visual Basic コンパイラでは、コード内のドキュメント コメントを処理し、XML ファイルに変換できます。</span><span class="sxs-lookup"><span data-stu-id="905b0-104">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="905b0-105">追加のツールを利用すれば、XML ファイルを処理してドキュメントに変換できます。</span><span class="sxs-lookup"><span data-stu-id="905b0-105">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="905b0-106">XML コメントは、型や型メンバーなどのコード コンストラクターで許可されます。</span><span class="sxs-lookup"><span data-stu-id="905b0-106">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="905b0-107">部分型の場合、そのメンバーに対するコメント作成に制限はありませんが、XML コメントを追加できる型の部分は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="905b0-107">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="905b0-108">ドキュメント コメントは、名前空間に適用できません。</span><span class="sxs-lookup"><span data-stu-id="905b0-108">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="905b0-109">その理由は、1 つの名前空間は複数のアセンブリにまたがることができて、かつ、すべてのアセンブリを同時に読み込む必要はないということにあります。</span><span class="sxs-lookup"><span data-stu-id="905b0-109">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="905b0-110">コンパイラは、有効な XML であるタグをすべて処理します。</span><span class="sxs-lookup"><span data-stu-id="905b0-110">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="905b0-111">次のタグによって、ユーザー ドキュメントで一般的に使用される機能が与えられます。</span><span class="sxs-lookup"><span data-stu-id="905b0-111">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|<span data-ttu-id="905b0-112">[\<exception>](exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="905b0-112">[\<exception>](exception.md) <sup>1</sup></span></span>|<span data-ttu-id="905b0-113">[\<include>](include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="905b0-113">[\<include>](include.md) <sup>1</sup></span></span>|[\<list>](list.md)|  
|[\<para>](para.md)|<span data-ttu-id="905b0-114">[\<param>](param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="905b0-114">[\<param>](param.md) <sup>1</sup></span></span>|[\<paramref>](paramref.md)|  
|<span data-ttu-id="905b0-115">[\<permission>](permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="905b0-115">[\<permission>](permission.md) <sup>1</sup></span></span>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|<span data-ttu-id="905b0-116">[\<see>](see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="905b0-116">[\<see>](see.md) <sup>1</sup></span></span>|<span data-ttu-id="905b0-117">[\<seealso>](seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="905b0-117">[\<seealso>](seealso.md) <sup>1</sup></span></span>|[\<summary>](summary.md)|  
|<span data-ttu-id="905b0-118">[\<typeparam>](typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="905b0-118">[\<typeparam>](typeparam.md) <sup>1</sup></span></span>|[\<value>](value.md)||  
  
 <span data-ttu-id="905b0-119">(<sup>1</sup> コンパイラによって構文が検証されます。)</span><span class="sxs-lookup"><span data-stu-id="905b0-119">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="905b0-120">ドキュメント コメントのテキストに山かっこを表示する場合は、`&lt;` と `&gt;` を使用します。</span><span class="sxs-lookup"><span data-stu-id="905b0-120">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="905b0-121">たとえば、文字列 `"&lt;text in angle brackets&gt;"` は `<text in angle brackets>` として表示されます。</span><span class="sxs-lookup"><span data-stu-id="905b0-121">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="905b0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="905b0-122">See also</span></span>

- [<span data-ttu-id="905b0-123">XML の使用によるコードのドキュメントの作成</span><span class="sxs-lookup"><span data-stu-id="905b0-123">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="905b0-124">-doc</span><span class="sxs-lookup"><span data-stu-id="905b0-124">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="905b0-125">方法: XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="905b0-125">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
