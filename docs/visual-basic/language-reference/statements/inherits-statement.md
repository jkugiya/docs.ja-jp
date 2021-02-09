---
description: '詳細情報: Inherits Statement'
title: Inherits Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: fba574ec207b384c1e7219341526a4a89c8a619c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768923"
---
# <a name="inherits-statement"></a><span data-ttu-id="c7bd1-103">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="c7bd1-103">Inherits Statement</span></span>

<span data-ttu-id="c7bd1-104">現在のクラスまたはインターフェイスで、属性、変数、プロパティ、プロシージャ、およびイベントを別のクラスまたは一連のインターフェイスから継承させます。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-104">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7bd1-105">構文</span><span class="sxs-lookup"><span data-stu-id="c7bd1-105">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="c7bd1-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="c7bd1-106">Parts</span></span>  
  
|<span data-ttu-id="c7bd1-107">用語</span><span class="sxs-lookup"><span data-stu-id="c7bd1-107">Term</span></span>|<span data-ttu-id="c7bd1-108">定義</span><span class="sxs-lookup"><span data-stu-id="c7bd1-108">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="c7bd1-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-109">Required.</span></span> <span data-ttu-id="c7bd1-110">このクラスの派生元のクラスの名前です。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-110">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="c7bd1-111">\- または -</span><span class="sxs-lookup"><span data-stu-id="c7bd1-111">-or-</span></span><br /><br /> <span data-ttu-id="c7bd1-112">このインターフェイスの派生元のインターフェイスの名前です。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-112">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="c7bd1-113">複数の名前を区切るには、コンマを使用します。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-113">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7bd1-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="c7bd1-114">Remarks</span></span>  

 <span data-ttu-id="c7bd1-115">使用した場合、`Inherits` ステートメントが、クラスまたはインターフェイス定義の最初の空行でもコメント行でもない行に記述されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-115">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="c7bd1-116">それは、`Class` または `Interface` ステートメントの直後に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-116">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="c7bd1-117">`Inherits` は、クラスまたはインターフェイスでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-117">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="c7bd1-118">つまり、継承の宣言コンテキストは、ソース ファイル、名前空間、構造体、モジュール、プロシージャ、ブロックにすることができません。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-118">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c7bd1-119">ルール</span><span class="sxs-lookup"><span data-stu-id="c7bd1-119">Rules</span></span>  
  
- <span data-ttu-id="c7bd1-120">**クラスの継承。**</span><span class="sxs-lookup"><span data-stu-id="c7bd1-120">**Class Inheritance.**</span></span> <span data-ttu-id="c7bd1-121">クラスで `Inherits` ステートメントを使用する場合、指定できる基底クラスは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-121">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="c7bd1-122">クラスは、その中の入れ子にされたクラスから継承できません。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-122">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="c7bd1-123">**インターフェイスの継承。**</span><span class="sxs-lookup"><span data-stu-id="c7bd1-123">**Interface Inheritance.**</span></span> <span data-ttu-id="c7bd1-124">インターフェイスで `Inherits` ステートメントを使用している場合、1 つまたは複数の基底インターフェイスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-124">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="c7bd1-125">それぞれが同じ名前のメンバーを定義している場合でも、2 つのインターフェイスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-125">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="c7bd1-126">その場合、実装するコードでは、実装するメンバーを指定するために名前の修飾を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-126">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="c7bd1-127">インターフェイスは、より制限の厳しいアクセス レベルの別のインターフェイスから継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-127">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="c7bd1-128">たとえば、`Public` インターフェイスは、`Friend` インターフェイスから継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-128">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="c7bd1-129">インターフェイスは、その中に入れ子にされたインターフェイスから継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-129">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="c7bd1-130">.NET Framework でのクラス継承の例として、<xref:System.SystemException> クラスから継承する <xref:System.ArgumentException> クラスがあります。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-130">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="c7bd1-131">これにより、<xref:System.ArgumentException> に、<xref:System.Exception.Message%2A> プロパティや <xref:System.Exception.ToString%2A> メソッドなど、システム例外に必要なすべての定義済みプロパティとプロシージャを提供できます。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-131">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="c7bd1-132">.NET Framework でのインターフェイスの継承の例として、<xref:System.Collections.IEnumerable> インターフェイスから継承する <xref:System.Collections.ICollection> インターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-132">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="c7bd1-133">これにより、<xref:System.Collections.ICollection> で、コレクションを走査するために必要な列挙子の定義が継承されます。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-133">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7bd1-134">例</span><span class="sxs-lookup"><span data-stu-id="c7bd1-134">Example</span></span>  

 <span data-ttu-id="c7bd1-135">次の例では、`Inherits` ステートメントを使用して、`thisClass` という名前のクラスで `anotherClass` という名前の基底クラスのすべてのメンバーを継承する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-135">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="c7bd1-136">例</span><span class="sxs-lookup"><span data-stu-id="c7bd1-136">Example</span></span>  

 <span data-ttu-id="c7bd1-137">次の例では、複数インターフェイスの継承を示しています。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-137">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="c7bd1-138">`thisInterface` という名前のインターフェイスに、<xref:System.IComparable>、<xref:System.IDisposable>、および <xref:System.IFormattable> インターフェイスのすべての定義が含まれるようになりました。継承されたメンバーではそれぞれ、2 つのオブジェクトの型固有の比較、割り当てられたリソースの解放、および `String` としてのオブジェクトの値の表現が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-138">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="c7bd1-139">`thisInterface` を実装するクラスでは、すべての基底インターフェイスのすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7bd1-139">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7bd1-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7bd1-140">See also</span></span>

- [<span data-ttu-id="c7bd1-141">MustInherit</span><span class="sxs-lookup"><span data-stu-id="c7bd1-141">MustInherit</span></span>](../modifiers/mustinherit.md)
- [<span data-ttu-id="c7bd1-142">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="c7bd1-142">NotInheritable</span></span>](../modifiers/notinheritable.md)
- [<span data-ttu-id="c7bd1-143">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="c7bd1-143">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="c7bd1-144">継承の基本</span><span class="sxs-lookup"><span data-stu-id="c7bd1-144">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="c7bd1-145">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7bd1-145">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
