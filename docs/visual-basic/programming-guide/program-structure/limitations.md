---
description: '詳細情報: Visual Basic の制限事項'
title: 制限事項
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 9182c5fe475e4350cb17ed3e4b734e3924bb9f7b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432846"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="11de7-103">Visual Basic の制限事項</span><span class="sxs-lookup"><span data-stu-id="11de7-103">Visual Basic Limitations</span></span>

<span data-ttu-id="11de7-104">以前のバージョンの Visual Basic では、変数名の長さ、モジュールで許可される変数の数、モジュール サイズなど、コードに上限が適用されていました。</span><span class="sxs-lookup"><span data-stu-id="11de7-104">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="11de7-105">Visual Basic .NET では、これらの制限が緩和され、コードをより自由に記述および配置できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="11de7-105">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="11de7-106">物理的な制限は、コンパイル時の考慮事項よりも実行時のメモリに大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="11de7-106">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="11de7-107">慎重なプログラミング プラクティスを使用し、大規模なアプリケーションを複数のクラスやモジュールに分割すれば、Visual Basic の内部的な制限が発生する可能性はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="11de7-107">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="11de7-108">極端な場合に発生する可能性があるいくつかの制限を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="11de7-108">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
- <span data-ttu-id="11de7-109">**名前の長さ:**</span><span class="sxs-lookup"><span data-stu-id="11de7-109">**Name Length.**</span></span> <span data-ttu-id="11de7-110">宣言されるすべてのプログラミング要素の名前には最大文字数があります。</span><span class="sxs-lookup"><span data-stu-id="11de7-110">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="11de7-111">要素名が修飾されている場合、この最大数は修飾文字列全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="11de7-111">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="11de7-112">「 [Declared Element Names](../language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11de7-112">See [Declared Element Names](../language-features/declared-elements/declared-element-names.md).</span></span>  
  
- <span data-ttu-id="11de7-113">**行の長さ:**</span><span class="sxs-lookup"><span data-stu-id="11de7-113">**Line Length.**</span></span> <span data-ttu-id="11de7-114">ソース コードの物理的な行の最大文字数は 65535 文字です。</span><span class="sxs-lookup"><span data-stu-id="11de7-114">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="11de7-115">行連結文字を使用すると、論理的なソース コード行が長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11de7-115">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="11de7-116">「[方法:コード内でステートメントを分割および連結する](how-to-break-and-combine-statements-in-code.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11de7-116">See [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
- <span data-ttu-id="11de7-117">**配列の次元:**</span><span class="sxs-lookup"><span data-stu-id="11de7-117">**Array Dimensions.**</span></span> <span data-ttu-id="11de7-118">配列で宣言できる次元数には上限があります。</span><span class="sxs-lookup"><span data-stu-id="11de7-118">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="11de7-119">これにより、配列要素を指定する際に使用できるインデックスの数が制限されます。</span><span class="sxs-lookup"><span data-stu-id="11de7-119">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="11de7-120">「[Visual Basic における配列の次元](../language-features/arrays/array-dimensions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11de7-120">See [Array Dimensions in Visual Basic](../language-features/arrays/array-dimensions.md).</span></span>  
  
- <span data-ttu-id="11de7-121">**文字列の長さ:**</span><span class="sxs-lookup"><span data-stu-id="11de7-121">**String Length.**</span></span> <span data-ttu-id="11de7-122">1 つの文字列に格納できる Unicode 文字数には上限があります。</span><span class="sxs-lookup"><span data-stu-id="11de7-122">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="11de7-123">「[文字列型 (String)](../../language-reference/data-types/string-data-type.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11de7-123">See [String Data Type](../../language-reference/data-types/string-data-type.md).</span></span>  
  
- <span data-ttu-id="11de7-124">**環境文字列の長さ:**</span><span class="sxs-lookup"><span data-stu-id="11de7-124">**Environment String Length.**</span></span> <span data-ttu-id="11de7-125">コマンド ライン引数として使用される環境文字列の最大文字数は 32768 文字です。</span><span class="sxs-lookup"><span data-stu-id="11de7-125">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="11de7-126">この制限はすべてのプラットフォームに適用されます。</span><span class="sxs-lookup"><span data-stu-id="11de7-126">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11de7-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="11de7-127">See also</span></span>

- [<span data-ttu-id="11de7-128">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="11de7-128">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="11de7-129">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="11de7-129">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
