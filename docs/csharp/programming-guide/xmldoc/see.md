---
title: <see> - C# プログラミング ガイド
description: XML <see> タグについて説明します。 このタグを使用すると、たとえば cref 属性を使用して、テキスト内からリンクを指定できます。
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 154feca5e7e4f4d3f5313c4ae05cd991e69e298f
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477771"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="1734a-104">\<see> (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1734a-104">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1734a-105">構文</span><span class="sxs-lookup"><span data-stu-id="1734a-105">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="1734a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1734a-106">Parameters</span></span>

- <span data-ttu-id="1734a-107">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="1734a-107">cref = "`member`"</span></span>

  <span data-ttu-id="1734a-108">現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。</span><span class="sxs-lookup"><span data-stu-id="1734a-108">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="1734a-109">コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。</span><span class="sxs-lookup"><span data-stu-id="1734a-109">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="1734a-110">*メンバー* は二重引用符 (" ") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="1734a-110">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="1734a-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="1734a-111">Remarks</span></span>

<span data-ttu-id="1734a-112">`<see>` タグを使用すると、テキスト内からリンクを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1734a-112">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="1734a-113">テキストが「関連項目」セクションに配置されていることを示すには、[\<seealso>](./seealso.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="1734a-113">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="1734a-114">コード要素のドキュメント ページへの内部ハイパーリンクを作成するには、[cref 属性](./cref-attribute.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="1734a-114">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="1734a-115">また、``href`` はハイパーリンクとして機能する有効な属性です。</span><span class="sxs-lookup"><span data-stu-id="1734a-115">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="1734a-116">コンパイル時に [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="1734a-116">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

<span data-ttu-id="1734a-117">次の例では、「概要」セクション内の `<see>` タグを示しています。</span><span class="sxs-lookup"><span data-stu-id="1734a-117">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="1734a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1734a-118">See also</span></span>

- [<span data-ttu-id="1734a-119">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1734a-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1734a-120">ドキュメント コメント用の推奨タグ</span><span class="sxs-lookup"><span data-stu-id="1734a-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
