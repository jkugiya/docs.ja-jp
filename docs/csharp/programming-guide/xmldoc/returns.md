---
title: <returns> - C# プログラミング ガイド
description: XML タグについて説明 <returns> します。 このタグは、メソッド宣言のコメントで戻り値を記述するために使用されます。
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 6a098208a51ca31fe2278b7c696deb15a13f8e1e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477811"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="f3445-105">\<returns> (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f3445-105">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f3445-106">構文</span><span class="sxs-lookup"><span data-stu-id="f3445-106">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="f3445-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3445-107">Parameters</span></span>

- `description`

  <span data-ttu-id="f3445-108">戻り値の説明。</span><span class="sxs-lookup"><span data-stu-id="f3445-108">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="f3445-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="f3445-109">Remarks</span></span>

<span data-ttu-id="f3445-110">`<returns>` タグは、戻り値を説明するためにメソッドの宣言のコメントで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3445-110">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="f3445-111">コンパイル時に [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="f3445-111">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="f3445-112">例</span><span class="sxs-lookup"><span data-stu-id="f3445-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="f3445-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3445-113">See also</span></span>

- [<span data-ttu-id="f3445-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f3445-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f3445-115">ドキュメント コメント用の推奨タグ</span><span class="sxs-lookup"><span data-stu-id="f3445-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
