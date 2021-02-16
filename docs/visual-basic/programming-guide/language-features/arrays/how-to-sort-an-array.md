---
description: '詳細情報: Visual Basic で配列を並べ替える'
title: '方法: 配列を並べ替える'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: ea030b63dbbb5f5ea1d6160757afe2e9b58f7c21
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462764"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="dada8-103">Visual Basic で配列を並べ替える</span><span class="sxs-lookup"><span data-stu-id="dada8-103">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="dada8-104">この記事では、Visual Basic で文字列の配列を並べ替える方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="dada8-104">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="dada8-105">例</span><span class="sxs-lookup"><span data-stu-id="dada8-105">Example</span></span>

<span data-ttu-id="dada8-106">この例では、`zooAnimals` という名前の `String` オブジェクトの配列を宣言し、値を設定して、アルファベット順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="dada8-106">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="dada8-107">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="dada8-107">Robust programming</span></span>

<span data-ttu-id="dada8-108">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dada8-108">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="dada8-109">配列が空である (<xref:System.ArgumentNullException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="dada8-109">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="dada8-110">多次元配列である (<xref:System.RankException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="dada8-110">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="dada8-111">配列の 1 つ以上の要素で <xref:System.IComparable> インターフェイス (<xref:System.InvalidOperationException> クラス) が実装されていない。</span><span class="sxs-lookup"><span data-stu-id="dada8-111">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="dada8-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="dada8-112">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="dada8-113">配列</span><span class="sxs-lookup"><span data-stu-id="dada8-113">Arrays</span></span>](index.md)
- [<span data-ttu-id="dada8-114">配列のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="dada8-114">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="dada8-115">コレクション</span><span class="sxs-lookup"><span data-stu-id="dada8-115">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="dada8-116">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="dada8-116">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
