---
title: <typeparam> - C# プログラミング ガイド
description: XML タグについて説明 <typeparam> します。 このタグは、型パラメーターを説明するために、ジェネリック型またはメソッドの宣言のコメントで使用します。
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 1b9d5d30c1a507e3bb7938ee0c036cdac3ef2f90
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477680"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="83293-105">\<typeparam> (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="83293-105">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="83293-106">構文</span><span class="sxs-lookup"><span data-stu-id="83293-106">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="83293-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83293-107">Parameters</span></span>

- `name`

  <span data-ttu-id="83293-108">型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="83293-108">The name of the type parameter.</span></span> <span data-ttu-id="83293-109">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="83293-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="83293-110">型パラメーターの説明。</span><span class="sxs-lookup"><span data-stu-id="83293-110">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="83293-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="83293-111">Remarks</span></span>

<span data-ttu-id="83293-112">`<typeparam>` タグは、型パラメーターを説明するためにジェネリック型またはメソッドの宣言のコメントで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83293-112">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="83293-113">ジェネリック型またはメソッドの型パラメーターごとにタグを追加します。</span><span class="sxs-lookup"><span data-stu-id="83293-113">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="83293-114">詳細については、「[ジェネリック](../generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83293-114">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="83293-115">`<typeparam>` タグのテキストは、IntelliSense、[オブジェクト ブラウザー ウィンドウ](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)、コード コメント Web レポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="83293-115">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="83293-116">コンパイル時に [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="83293-116">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="83293-117">例</span><span class="sxs-lookup"><span data-stu-id="83293-117">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="83293-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="83293-118">See also</span></span>

- [<span data-ttu-id="83293-119">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="83293-119">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="83293-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="83293-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="83293-121">ドキュメント コメント用の推奨タグ</span><span class="sxs-lookup"><span data-stu-id="83293-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
