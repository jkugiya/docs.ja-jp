---
title: <value> - C# プログラミング ガイド
description: XML タグについて説明 <value> します。 このタグを使用すると、プロパティが表す値を記述することができます。
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: c910a60a50e95621c1e3ad773000cbac0d43bb10
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477645"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="bb6fd-105">\<value> (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="bb6fd-105">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="bb6fd-106">構文</span><span class="sxs-lookup"><span data-stu-id="bb6fd-106">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="bb6fd-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb6fd-107">Parameters</span></span>

- `property-description`

  <span data-ttu-id="bb6fd-108">プロパティの説明。</span><span class="sxs-lookup"><span data-stu-id="bb6fd-108">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb6fd-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="bb6fd-109">Remarks</span></span>

<span data-ttu-id="bb6fd-110">`<value>` タグを使用して、プロパティが表す値を記述することができます。</span><span class="sxs-lookup"><span data-stu-id="bb6fd-110">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="bb6fd-111">Visual Studio .NET 開発環境では、コード ウィザードを使用してプロパティを追加するときに、新しいプロパティの [\<summary>](./summary.md) タグが追加されます。</span><span class="sxs-lookup"><span data-stu-id="bb6fd-111">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="bb6fd-112">その後、手動で `<value>` タグを追加してプロパティが表す値を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb6fd-112">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="bb6fd-113">コンパイル時に [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="bb6fd-113">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="bb6fd-114">例</span><span class="sxs-lookup"><span data-stu-id="bb6fd-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="bb6fd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb6fd-115">See also</span></span>

- [<span data-ttu-id="bb6fd-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="bb6fd-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="bb6fd-117">ドキュメント コメント用の推奨タグ</span><span class="sxs-lookup"><span data-stu-id="bb6fd-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
