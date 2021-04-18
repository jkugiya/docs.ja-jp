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
ms.openlocfilehash: 351dd2e4c7dbc76efa2edbed708fb342c553ce70
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494858"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="c3606-104">\<see> (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c3606-104">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3606-105">構文</span><span class="sxs-lookup"><span data-stu-id="c3606-105">Syntax</span></span>

```csharp
/// <see cref="member"/>
// or
/// <see href="link">Link Text</see>
// or
/// <see langword="keyword"/>
```

## <a name="parameters"></a><span data-ttu-id="c3606-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c3606-106">Parameters</span></span>

- `cref="member"`

  <span data-ttu-id="c3606-107">現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。</span><span class="sxs-lookup"><span data-stu-id="c3606-107">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="c3606-108">コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。</span><span class="sxs-lookup"><span data-stu-id="c3606-108">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="c3606-109">*メンバー* は二重引用符 (" ") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3606-109">Place *member* within double quotation marks (" ").</span></span>

- `href="link"`

  <span data-ttu-id="c3606-110">特定の URL へのクリック可能なリンク。</span><span class="sxs-lookup"><span data-stu-id="c3606-110">A clickable link to a given URL.</span></span> <span data-ttu-id="c3606-111">たとえば、`<see href="https://github.com">GitHub</see>` によって生成されるクリック可能なリンクには、`https://github.com` にリンクされたテキスト :::no-loc text="GitHub"::: が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c3606-111">For example, `<see href="https://github.com">GitHub</see>` produces a clickable link with text :::no-loc text="GitHub"::: that links to `https://github.com`.</span></span>

- `langword="keyword"`

  <span data-ttu-id="c3606-112">`true` などの言語キーワード。</span><span class="sxs-lookup"><span data-stu-id="c3606-112">A language keyword, such as `true`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3606-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="c3606-113">Remarks</span></span>

<span data-ttu-id="c3606-114">`<see>` タグを使用すると、テキスト内からリンクを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c3606-114">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="c3606-115">テキストが「関連項目」セクションに配置されていることを示すには、[\<seealso>](./seealso.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c3606-115">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="c3606-116">コード要素のドキュメント ページへの内部ハイパーリンクを作成するには、[cref 属性](./cref-attribute.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="c3606-116">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="c3606-117">また、``href`` はハイパーリンクとして機能する有効な属性です。</span><span class="sxs-lookup"><span data-stu-id="c3606-117">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="c3606-118">コンパイル時に [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="c3606-118">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

<span data-ttu-id="c3606-119">次の例では、「概要」セクション内の `<see>` タグを示しています。</span><span class="sxs-lookup"><span data-stu-id="c3606-119">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="c3606-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3606-120">See also</span></span>

- [<span data-ttu-id="c3606-121">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c3606-121">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="c3606-122">ドキュメント コメント用の推奨タグ</span><span class="sxs-lookup"><span data-stu-id="c3606-122">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
