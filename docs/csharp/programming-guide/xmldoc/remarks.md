---
title: <remarks> - C# プログラミング ガイド
description: XML タグについて説明 <remarks> します。 このタグを使用して型の情報を追加し、指定された情報を補足します <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 2227dd8bd4d81f5fda8cf529e18c7a613cca6b8e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477827"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="b6dde-106">\<remarks> (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b6dde-106">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b6dde-107">構文</span><span class="sxs-lookup"><span data-stu-id="b6dde-107">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="b6dde-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6dde-108">Parameters</span></span>

- `Description`

  <span data-ttu-id="b6dde-109">メンバーの説明。</span><span class="sxs-lookup"><span data-stu-id="b6dde-109">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6dde-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="b6dde-110">Remarks</span></span>

<span data-ttu-id="b6dde-111">`<remarks>` タグを使用して、型の情報を追加し、[\<summary>](./summary.md) で指定された情報を補足します。</span><span class="sxs-lookup"><span data-stu-id="b6dde-111">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="b6dde-112">この情報はオブジェクト ブラウザー ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6dde-112">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="b6dde-113">コンパイル時に [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="b6dde-113">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b6dde-114">例</span><span class="sxs-lookup"><span data-stu-id="b6dde-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="b6dde-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6dde-115">See also</span></span>

- [<span data-ttu-id="b6dde-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b6dde-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b6dde-117">ドキュメント コメント用の推奨タグ</span><span class="sxs-lookup"><span data-stu-id="b6dde-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
