---
description: 詳細については、以下をご覧ください。 <include> (Visual Basic)
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 8207b74ed74bd529f2da865777e287320b23d293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787462"
---
# <a name="include-visual-basic"></a><span data-ttu-id="b9d48-103">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9d48-103">\<include> (Visual Basic)</span></span>

<span data-ttu-id="b9d48-104">ソース コード内の型とメンバーを記述する別のファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="b9d48-104">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d48-105">構文</span><span class="sxs-lookup"><span data-stu-id="b9d48-105">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9d48-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b9d48-106">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="b9d48-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="b9d48-107">Required.</span></span> <span data-ttu-id="b9d48-108">文書を含むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="b9d48-108">The name of the file containing the documentation.</span></span> <span data-ttu-id="b9d48-109">ファイル名をパスで修飾することができます。</span><span class="sxs-lookup"><span data-stu-id="b9d48-109">The file name can be qualified with a path.</span></span> <span data-ttu-id="b9d48-110">`filename` は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="b9d48-110">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="b9d48-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="b9d48-111">Required.</span></span> <span data-ttu-id="b9d48-112">タグ `name` につながる `filename` 内のタグのパス。</span><span class="sxs-lookup"><span data-stu-id="b9d48-112">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="b9d48-113">パスは二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="b9d48-113">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="b9d48-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="b9d48-114">Required.</span></span> <span data-ttu-id="b9d48-115">コメントの前に配置するタグの名前指定子。</span><span class="sxs-lookup"><span data-stu-id="b9d48-115">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="b9d48-116">`Name` には `id` が指定されます。</span><span class="sxs-lookup"><span data-stu-id="b9d48-116">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="b9d48-117">必須です。</span><span class="sxs-lookup"><span data-stu-id="b9d48-117">Required.</span></span> <span data-ttu-id="b9d48-118">コメントの前に配置するタグの ID。</span><span class="sxs-lookup"><span data-stu-id="b9d48-118">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="b9d48-119">ID は単一引用符 (' ') で囲みます。</span><span class="sxs-lookup"><span data-stu-id="b9d48-119">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9d48-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9d48-120">Remarks</span></span>  

 <span data-ttu-id="b9d48-121">`<include>` タグを使用して、ソース コード内の型とメンバーを記述する別のファイル内のコメントを参照します。</span><span class="sxs-lookup"><span data-stu-id="b9d48-121">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="b9d48-122">これは文書化のコメントをソース コード ファイル内に直接配置する方法の代替です。</span><span class="sxs-lookup"><span data-stu-id="b9d48-122">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="b9d48-123">`<include>` タグでは、W3C XML Path Language (XPath) Version 1.0 勧告が使用されています。</span><span class="sxs-lookup"><span data-stu-id="b9d48-123">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="b9d48-124">`<include>` の使用をカスタマイズする方法の詳細については、「<https://www.w3.org/TR/xpath>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9d48-124">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9d48-125">例</span><span class="sxs-lookup"><span data-stu-id="b9d48-125">Example</span></span>  

 <span data-ttu-id="b9d48-126">この例では、`<include>` タグを使用して、`commentFile.xml` というファイルからメンバー ドキュメント コメントをインポートします。</span><span class="sxs-lookup"><span data-stu-id="b9d48-126">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="b9d48-127">`commentFile.xml` の形式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b9d48-127">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9d48-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9d48-128">See also</span></span>

- [<span data-ttu-id="b9d48-129">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="b9d48-129">XML Comment Tags</span></span>](index.md)
