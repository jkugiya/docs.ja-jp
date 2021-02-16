---
description: '詳細情報: Visual Basic における文字列操作メソッドの種類'
title: 文字列操作メソッドの種類
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 02b127d5cd023a8bd73a3042a8bcec340ce63ed8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429755"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="148d6-103">Visual Basic における文字列操作メソッドの種類</span><span class="sxs-lookup"><span data-stu-id="148d6-103">Types of String Manipulation Methods in Visual Basic</span></span>

<span data-ttu-id="148d6-104">文字列を分析および操作するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="148d6-104">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="148d6-105">Visual Basic 言語の一部であるメソッドもあれば、`String` クラスに固有のメソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="148d6-105">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="148d6-106">Visual Basic 言語と .NET Framework</span><span class="sxs-lookup"><span data-stu-id="148d6-106">Visual Basic Language and the .NET Framework</span></span>  

 <span data-ttu-id="148d6-107">Visual Basic のメソッドは、この言語の固有の関数として使用されます。</span><span class="sxs-lookup"><span data-stu-id="148d6-107">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="148d6-108">これらはコード内で修飾なしで使用できます。</span><span class="sxs-lookup"><span data-stu-id="148d6-108">They may be used without qualification in your code.</span></span> <span data-ttu-id="148d6-109">次の例は、Visual Basic の文字列操作コマンドの一般的な使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="148d6-109">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="148d6-110">この例では、`Mid` 関数は `aString` に対して直接操作を実行し、値を `bString` に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="148d6-110">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="148d6-111">Visual Basic の文字列操作メソッドの一覧については、「[文字列操作の概要](../../../language-reference/keywords/string-manipulation-summary.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="148d6-111">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="148d6-112">共有メソッドとインスタンス メソッド</span><span class="sxs-lookup"><span data-stu-id="148d6-112">Shared Methods and Instance Methods</span></span>  

 <span data-ttu-id="148d6-113">`String` クラスのメソッドを使用して、文字列を操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="148d6-113">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="148d6-114">`String` には、"*共有*" メソッドと "*インスタンス*" メソッドの 2 種類のメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="148d6-114">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="148d6-115">共有メソッド</span><span class="sxs-lookup"><span data-stu-id="148d6-115">Shared Methods</span></span>  

 <span data-ttu-id="148d6-116">共有メソッドは、`String` クラス自体に由来するメソッドであり、このクラスのインスタンスが動作する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="148d6-116">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="148d6-117">これらのメソッドは、`String` クラスのインスタンスではなく、クラスの名前 (`String`) で修飾できます。</span><span class="sxs-lookup"><span data-stu-id="148d6-117">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="148d6-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="148d6-118">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="148d6-119">上記の例では、<xref:System.String.Copy%2A?displayProperty=nameWithType> メソッドは静的メソッドであり、指定されている式に対して動作し、結果の値を `bString` に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="148d6-119">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="148d6-120">インスタンス メソッド</span><span class="sxs-lookup"><span data-stu-id="148d6-120">Instance Methods</span></span>  

 <span data-ttu-id="148d6-121">インスタンス メソッドは、`String` の特定のインスタンスに由来し、インスタンス名で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="148d6-121">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="148d6-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="148d6-122">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="148d6-123">この例では、<xref:System.String.Substring%2A?displayProperty=nameWithType> メソッドは、`String` のインスタンス (つまり、`aString`) のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="148d6-123">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="148d6-124">`aString` に対して操作を実行し、その値を `bString` に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="148d6-124">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="148d6-125">詳細については、<xref:System.String> クラスのドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="148d6-125">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="148d6-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="148d6-126">See also</span></span>

- [<span data-ttu-id="148d6-127">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="148d6-127">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
