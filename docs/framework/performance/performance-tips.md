---
title: .NET のパフォーマンスに関するヒント
description: .NET でのプログラムの実行速度を向上させるためのパフォーマンスのヒントについて説明します。 ボックス化、ボックス化解除、文字列、およびデストラクターに関するヒントをご覧ください。
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 526dd0d42b82dd4987e446382e7639f322e063aa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281704"
---
# <a name="net-performance-tips"></a><span data-ttu-id="7ecc9-104">.NET のパフォーマンスに関するヒント</span><span class="sxs-lookup"><span data-stu-id="7ecc9-104">.NET Performance Tips</span></span>

<span data-ttu-id="7ecc9-105">*パフォーマンス* という用語は、プログラムの実行速度を表す一般的な用語です。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-105">The term *performance* generally refers to the execution speed of a program.</span></span> <span data-ttu-id="7ecc9-106">ソース コード内で特定の基本規則に従うことにより、実行速度を上げることができることもあります。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-106">You can sometimes increase execution speed by following certain basic rules in your source code.</span></span> <span data-ttu-id="7ecc9-107">プログラムによっては、コードを綿密に調べることが重要で、プロファイラーを使用して、可能な限り速く実行しているかどうかを確認することが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-107">In some programs, it is important to examine code closely and use profilers to make sure that it is running as fast as possible.</span></span> <span data-ttu-id="7ecc9-108">一方、記述どおりに許容可能な速度でコードが実行されているため、このような最適化が必要ないプログラムもあります。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-108">In other programs, you do not have to perform such optimization because the code is running acceptably fast as it is written.</span></span> <span data-ttu-id="7ecc9-109">ここでは、パフォーマンスの低下が発生する一般的な状況と、パフォーマンスを向上させるためのヒント、およびパフォーマンスに関する追加のトピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-109">This article lists some common areas where performance can suffer and tips for improving it as well as links to additional performance topics.</span></span> <span data-ttu-id="7ecc9-110">パフォーマンスの計画と計測の詳細については、「[Performance](index.md)」(パフォーマンス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-110">For more information about planning and measuring for performance, see [Performance](index.md)</span></span>  
  
## <a name="boxing-and-unboxing"></a><span data-ttu-id="7ecc9-111">ボックス化とボックス化解除</span><span class="sxs-lookup"><span data-stu-id="7ecc9-111">Boxing and Unboxing</span></span>  

 <span data-ttu-id="7ecc9-112">たとえば、<xref:System.Collections.ArrayList?displayProperty=nameWithType> などの非ジェネリック コレクション クラスで、頻繁に値型をボックス化する必要がある状況では、値型の使用を回避するのが最も適しています。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-112">It is best to avoid using value types in situations where they must be boxed a high number of times, for example in non-generic collections classes such as <xref:System.Collections.ArrayList?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ecc9-113"><xref:System.Collections.Generic.List%601?displayProperty=nameWithType> などのジェネリック コレクションを使用することで、値型のボックス化を回避できます。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-113">You can avoid boxing of value types by using generic collections such as <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ecc9-114">ボックス化とボックス化解除は、負荷の大きい処理です。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-114">Boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="7ecc9-115">値型をボックス化するときは、完全に新しいオブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-115">When a value type is boxed, an entirely new object must be created.</span></span> <span data-ttu-id="7ecc9-116">これには、単純な参照割り当てと比較して最大 20 倍もの時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-116">This can take up to 20 times longer than a simple reference assignment.</span></span> <span data-ttu-id="7ecc9-117">また、ボックス化を解除するときは、キャストのプロセスで代入の 4 倍の時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-117">When unboxing, the casting process can take four times as long as an assignment.</span></span> <span data-ttu-id="7ecc9-118">詳細については、「[ボックス化とボックス化解除](../../csharp/programming-guide/types/boxing-and-unboxing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-118">For more information, see [Boxing and Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="strings"></a><span data-ttu-id="7ecc9-119">文字列</span><span class="sxs-lookup"><span data-stu-id="7ecc9-119">Strings</span></span>  

 <span data-ttu-id="7ecc9-120">たとえば、短いループ内で多くの文字列変数を連結する場合は、C# の [+ 演算子](../../csharp/language-reference/operators/addition-operator.md)または Visual Basic の[連結演算子](../../visual-basic/language-reference/operators/concatenation-operators.md)ではなく、<xref:System.Text.StringBuilder?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-120">When you concatenate a large number of string variables, for example in a tight loop, use <xref:System.Text.StringBuilder?displayProperty=nameWithType> instead of the C# [+ operator](../../csharp/language-reference/operators/addition-operator.md) or the Visual Basic [Concatenation Operators](../../visual-basic/language-reference/operators/concatenation-operators.md).</span></span> <span data-ttu-id="7ecc9-121">詳細については、[複数の文字列を連結する方法](../../csharp/how-to/concatenate-multiple-strings.md)に関する記事と「[Visual Basic の連結演算子](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-121">For more information, see [How to concatenate multiple strings](../../csharp/how-to/concatenate-multiple-strings.md) and [Concatenation Operators in Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).</span></span>  
  
## <a name="destructors"></a><span data-ttu-id="7ecc9-122">デストラクター</span><span class="sxs-lookup"><span data-stu-id="7ecc9-122">Destructors</span></span>  

 <span data-ttu-id="7ecc9-123">空のデストラクターは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-123">Empty destructors should not be used.</span></span> <span data-ttu-id="7ecc9-124">デストラクターがクラスに存在するときは、エントリが終了キューで作成されます。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-124">When a class contains a destructor, an entry is created in the Finalize queue.</span></span> <span data-ttu-id="7ecc9-125">デストラクターを呼び出すと、ガベージ コレクターが呼び出され、このキューを処理します。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-125">When the destructor is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="7ecc9-126">デストラクターが空の場合は、これによってパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-126">If the destructor is empty, this simply results in a loss of performance.</span></span> <span data-ttu-id="7ecc9-127">詳細については、「[デストラクタ](../../csharp/programming-guide/classes-and-structs/destructors.md)」と「[Object Lifetime: How Objects Are Created and Destroyed](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)」(オブジェクトの有効期間 : オブジェクトの作成と破棄) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ecc9-127">For more information, see [Destructors](../../csharp/programming-guide/classes-and-structs/destructors.md) and [Object Lifetime: How Objects Are Created and Destroyed](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
## <a name="other-resources"></a><span data-ttu-id="7ecc9-128">その他の参照情報</span><span class="sxs-lookup"><span data-stu-id="7ecc9-128">Other Resources</span></span>  
  
- <span data-ttu-id="7ecc9-129">[高速なマネージド コードを書く: 何にコストがかかるのかを知る](/previous-versions/dotnet/articles/ms973852(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="7ecc9-129">[Writing Faster Managed Code: Know What Things Cost](/previous-versions/dotnet/articles/ms973852(v=msdn.10))</span></span>  
  
- <span data-ttu-id="7ecc9-130">[高パフォーマンスのマネージド アプリケーションを書く: 入門編](/previous-versions/dotnet/articles/ms973858(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="7ecc9-130">[Writing High-Performance Managed Applications: A Primer](/previous-versions/dotnet/articles/ms973858(v=msdn.10))</span></span>  
  
- <span data-ttu-id="7ecc9-131">[ガベージ コレクターの基本とパフォーマンスのヒント](/previous-versions/dotnet/articles/ms973837(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="7ecc9-131">[Garbage Collector Basics and Performance Hints](/previous-versions/dotnet/articles/ms973837(v=msdn.10))</span></span>  
  
- <span data-ttu-id="7ecc9-132">[.NET アプリケーションのパフォーマンス関連のヒントとトリック](/previous-versions/dotnet/articles/ms973839(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="7ecc9-132">[Performance Tips and Tricks in .NET Applications](/previous-versions/dotnet/articles/ms973839(v=msdn.10))</span></span>  

- [<span data-ttu-id="7ecc9-133">Rico Mariani が紹介するパフォーマンスに関するニュース</span><span class="sxs-lookup"><span data-stu-id="7ecc9-133">Rico Mariani's Performance Tidbits</span></span>](/archive/blogs/ricom/)  

- [<span data-ttu-id="7ecc9-134">Vance Morrison のブログ</span><span class="sxs-lookup"><span data-stu-id="7ecc9-134">Vance Morrison's Blog</span></span>](/archive/blogs/vancem/)
  
## <a name="see-also"></a><span data-ttu-id="7ecc9-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ecc9-135">See also</span></span>

- [<span data-ttu-id="7ecc9-136">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="7ecc9-136">Performance</span></span>](index.md)
- [<span data-ttu-id="7ecc9-137">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="7ecc9-137">Visual Basic Programming Guide</span></span>](../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="7ecc9-138">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="7ecc9-138">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)
