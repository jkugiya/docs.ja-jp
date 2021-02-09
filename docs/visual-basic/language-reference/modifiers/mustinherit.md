---
description: '詳細情報: MustInherit (Visual Basic)'
title: MustInherit
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 6ca11dd3fee8240f39ea1a3d278870d167d283d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701041"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="097fd-103">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="097fd-103">MustInherit (Visual Basic)</span></span>

<span data-ttu-id="097fd-104">クラスが基底クラスとしてのみ使用でき、オブジェクトを直接作成できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="097fd-104">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="097fd-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="097fd-105">Remarks</span></span>  

 <span data-ttu-id="097fd-106">*基底クラス* (*抽象クラス* とも呼ばれます) の目的は、このクラスから派生したすべてのクラスに共通の機能を定義することです。</span><span class="sxs-lookup"><span data-stu-id="097fd-106">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="097fd-107">これにより、派生クラスで共通の要素を再定義する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="097fd-107">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="097fd-108">場合によっては、この共通機能は使用可能なオブジェクトを作成するのに十分ではなく、各派生クラスで不足している機能が定義されます。</span><span class="sxs-lookup"><span data-stu-id="097fd-108">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="097fd-109">このような場合は、使用しているコードで派生クラスからのみオブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="097fd-109">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="097fd-110">これを適用するには、基底クラスで `MustInherit` を使用します。</span><span class="sxs-lookup"><span data-stu-id="097fd-110">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="097fd-111">`MustInherit` クラスのもう 1 つの用途は、変数を関連するクラスのセットに制限することです。</span><span class="sxs-lookup"><span data-stu-id="097fd-111">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="097fd-112">基底クラスを定義し、そこから関連するすべてのクラスを派生させることができます。</span><span class="sxs-lookup"><span data-stu-id="097fd-112">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="097fd-113">基底クラスがすべての派生クラスに共通する機能を提供する必要はありませんが、変数に値を代入するためのフィルターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="097fd-113">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="097fd-114">使用しているコードが変数を基底クラスとして宣言している場合は、Visual Basic によって、派生クラスのいずれかからその変数にオブジェクトのみを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="097fd-114">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="097fd-115">.NET Framework は、<xref:System.Array>、<xref:System.Enum>、<xref:System.ValueType> などのいくつかの `MustInherit` クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="097fd-115">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="097fd-116"><xref:System.ValueType> は、変数を制限する基底クラスの例です。</span><span class="sxs-lookup"><span data-stu-id="097fd-116"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="097fd-117">すべての値の型は <xref:System.ValueType> から派生します。</span><span class="sxs-lookup"><span data-stu-id="097fd-117">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="097fd-118">変数を <xref:System.ValueType> として宣言する場合は、その変数に値の型のみを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="097fd-118">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="097fd-119">ルール</span><span class="sxs-lookup"><span data-stu-id="097fd-119">Rules</span></span>  
  
- <span data-ttu-id="097fd-120">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="097fd-120">**Declaration Context.**</span></span> <span data-ttu-id="097fd-121">`Class` ステートメントでは `MustInherit` のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="097fd-121">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="097fd-122">**結合された修飾子。**</span><span class="sxs-lookup"><span data-stu-id="097fd-122">**Combined Modifiers.**</span></span> <span data-ttu-id="097fd-123">同じ宣言内で `MustInherit` を `NotInheritable` と共に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="097fd-123">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="097fd-124">例</span><span class="sxs-lookup"><span data-stu-id="097fd-124">Example</span></span>  

 <span data-ttu-id="097fd-125">継承の強制とオーバーライドの強制の両方の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="097fd-125">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="097fd-126">基底クラス `shape` は `acrossLine` 変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="097fd-126">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="097fd-127">クラス `circle` および `square` は `shape` から派生します。</span><span class="sxs-lookup"><span data-stu-id="097fd-127">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="097fd-128">これらは `acrossLine` の定義を継承しますが、その計算は図形の種類ごとに異なるため、関数 `area` を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="097fd-128">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="097fd-129">`shape1` と `shape2` を型 `shape` として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="097fd-129">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="097fd-130">ただし、`shape` からオブジェクトを作成することはできません。これには関数 `area` の機能がなく、`MustInherit` としてマークされているためです。</span><span class="sxs-lookup"><span data-stu-id="097fd-130">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="097fd-131">これらは `shape` として宣言されているため、変数 `shape1` および `shape2` は、派生クラス `circle` および `square` のオブジェクトに制限されます。</span><span class="sxs-lookup"><span data-stu-id="097fd-131">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="097fd-132">Visual Basic では、これらの変数に他のオブジェクトを割り当てることはできません。これにより、高いレベルのタイプ セーフが実現します。</span><span class="sxs-lookup"><span data-stu-id="097fd-132">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="097fd-133">使用方法</span><span class="sxs-lookup"><span data-stu-id="097fd-133">Usage</span></span>  

 <span data-ttu-id="097fd-134">`MustInherit` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="097fd-134">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="097fd-135">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="097fd-135">Class Statement</span></span>](../statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="097fd-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="097fd-136">See also</span></span>

- [<span data-ttu-id="097fd-137">Inherits ステートメント</span><span class="sxs-lookup"><span data-stu-id="097fd-137">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="097fd-138">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="097fd-138">NotInheritable</span></span>](notinheritable.md)
- [<span data-ttu-id="097fd-139">キーワード</span><span class="sxs-lookup"><span data-stu-id="097fd-139">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="097fd-140">継承の基本</span><span class="sxs-lookup"><span data-stu-id="097fd-140">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
