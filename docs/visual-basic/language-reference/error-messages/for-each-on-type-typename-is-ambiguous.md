---
description: "詳細情報: BC32096:型が、'System.Collections.Generic.IEnumerable(Of T)' の複数のインスタンス生成を実装するため、型 '<typename>' の 'For Each' は不適切です"
title: 型が、'System.Collections.Generic.IEnumerable(Of T)' の複数のインスタンス生成を実装するため、型 '<typename>' の 'For Each' は不適切です。
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: c96bab40d4f7216f90368cf4c5526c7b4e5532f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796211"
---
# <a name="bc32096-for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="eb841-103">BC32096:型が、'System.Collections.Generic.IEnumerable(Of T)' の複数のインスタンス生成を実装するため、型 '\<typename>' の 'For Each' は不適切です。</span><span class="sxs-lookup"><span data-stu-id="eb841-103">BC32096: 'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>

<span data-ttu-id="eb841-104">`For Each` ステートメントで、複数の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを含む反復子変数を指定しています。</span><span class="sxs-lookup"><span data-stu-id="eb841-104">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>

 <span data-ttu-id="eb841-105">反復子変数は、.NET Framework の `Collections` 名前空間のいずれかに <xref:System.Collections.IEnumerable?displayProperty=nameWithType> または <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> インターフェイスを実装する型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb841-105">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the .NET Framework.</span></span> <span data-ttu-id="eb841-106">1 つのクラスで複数の構築されたジェネリック インターフェイスを、それぞれの構築に異なる型引数を使用して実装することができます。</span><span class="sxs-lookup"><span data-stu-id="eb841-106">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="eb841-107">これを行うクラスが反復子変数に使用されている場合、その変数には複数の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="eb841-107">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="eb841-108">このような場合、Visual Basic で呼び出すメソッドを選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="eb841-108">In such a case, Visual Basic cannot choose which method to call.</span></span>

 <span data-ttu-id="eb841-109">**エラー ID:** BC32096</span><span class="sxs-lookup"><span data-stu-id="eb841-109">**Error ID:** BC32096</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="eb841-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="eb841-110">To correct this error</span></span>

- <span data-ttu-id="eb841-111">[DirectCast 演算子](../operators/directcast-operator.md)または [TryCast 演算子](../operators/trycast-operator.md)を使用して、反復子変数の型を、使用する <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを定義するインターフェイスにキャストします。</span><span class="sxs-lookup"><span data-stu-id="eb841-111">Use [DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb841-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb841-112">See also</span></span>

- [<span data-ttu-id="eb841-113">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="eb841-113">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="eb841-114">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb841-114">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
