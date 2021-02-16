---
description: '詳細情報: Visual Basic における配列の次元'
title: 配列の次元
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 055a3efc1410bf80daf3804453adc2c20266733c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486551"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="ef274-103">Visual Basic における配列の次元</span><span class="sxs-lookup"><span data-stu-id="ef274-103">Array Dimensions in Visual Basic</span></span>

<span data-ttu-id="ef274-104">1 つの "*次元*" は、配列の要素の指定を変更できる 1 つの方向です。</span><span class="sxs-lookup"><span data-stu-id="ef274-104">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="ef274-105">月の毎日の売上合計を保持する配列には、1 つの次元 (月の日付) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ef274-105">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="ef274-106">月の毎日の部門別売上合計を保持する配列には、2 つの次元 (部門番号と日付) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ef274-106">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="ef274-107">配列の次元数は、その次元の "*ランク*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ef274-107">The number of dimensions an array has is called its *rank*.</span></span>

> [!NOTE]
> <span data-ttu-id="ef274-108"><xref:System.Array.Rank%2A> プロパティを使用すると、配列の次元数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ef274-108">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>

## <a name="working-with-dimensions"></a><span data-ttu-id="ef274-109">次元の使用</span><span class="sxs-lookup"><span data-stu-id="ef274-109">Working with Dimensions</span></span>

<span data-ttu-id="ef274-110">配列の要素を指定するには、その次元ごとに "*インデックス*" つまり "*添字*" を指定します。</span><span class="sxs-lookup"><span data-stu-id="ef274-110">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="ef274-111">要素は、インデックス 0 からその次元の最大インデックスまで、各次元に沿って連続しています。</span><span class="sxs-lookup"><span data-stu-id="ef274-111">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>

<span data-ttu-id="ef274-112">次の図は、さまざまなランクの配列の概念的な構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="ef274-112">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="ef274-113">図の各要素は、その要素にアクセスするインデックス値を示しています。</span><span class="sxs-lookup"><span data-stu-id="ef274-113">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="ef274-114">たとえば、インデックス `(1, 0)` を指定すると、2 次元配列の 2 行目の最初の要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ef274-114">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>

![1 次元配列のダイアグラム。](./media/array-dimensions/one-dimensional-array.gif)

![2 次元配列のダイアグラム。](./media/array-dimensions/two-dimensional-array.gif)

![3 次元配列のダイアグラム。](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a><span data-ttu-id="ef274-118">1 次元</span><span class="sxs-lookup"><span data-stu-id="ef274-118">One Dimension</span></span>

<span data-ttu-id="ef274-119">配列の多くには、各年齢の人数など、1 つの次元しか含まれません。</span><span class="sxs-lookup"><span data-stu-id="ef274-119">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="ef274-120">要素を指定するために必要なのは年齢のみで、その年齢の人数が要素に保持されています。</span><span class="sxs-lookup"><span data-stu-id="ef274-120">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="ef274-121">したがって、このような配列では 1 つのインデックスのみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ef274-121">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="ef274-122">次の例で宣言する変数には、0 から 120 までの年齢を示す "*1 次元配列*" が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ef274-122">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a><span data-ttu-id="ef274-123">2 次元</span><span class="sxs-lookup"><span data-stu-id="ef274-123">Two Dimensions</span></span>

<span data-ttu-id="ef274-124">配列の中には、キャンパスの各建物の各階にあるオフィスの数など、2 つの次元を持つものがあります。</span><span class="sxs-lookup"><span data-stu-id="ef274-124">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="ef274-125">要素を指定するには建物番号と階数の両方が必要で、各要素には、建物と階数の組み合わせに対応する数が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ef274-125">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="ef274-126">したがって、このような配列では 2 つのインデックスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ef274-126">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="ef274-127">次の例で宣言する変数には、建物 0 から建物 40 までの 0 階から 5 階にあるオフィス数を示す "*2 次元配列* "が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ef274-127">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>

```vb
Dim officeCounts(40, 5) As Byte
```

<span data-ttu-id="ef274-128">2 次元配列は "*矩形配列*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ef274-128">A two-dimensional array is also called a *rectangular array*.</span></span>

### <a name="three-dimensions"></a><span data-ttu-id="ef274-129">3 次元</span><span class="sxs-lookup"><span data-stu-id="ef274-129">Three Dimensions</span></span>

<span data-ttu-id="ef274-130">配列の中には、3 次元空間の値など、3 つの次元を持つものもあります。</span><span class="sxs-lookup"><span data-stu-id="ef274-130">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="ef274-131">このような配列では 3 つのインデックスが使用されます。ここでは、インデックスは物理空間の x、y、z 座標です。</span><span class="sxs-lookup"><span data-stu-id="ef274-131">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="ef274-132">次の例で宣言する変数には、3 次元ボリュームのさまざまなポイントの気温を示す "*3 次元配列*" が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ef274-132">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a><span data-ttu-id="ef274-133">多次元 (3 次元超)</span><span class="sxs-lookup"><span data-stu-id="ef274-133">More than Three Dimensions</span></span>

<span data-ttu-id="ef274-134">配列の次元は最大 32 次元ですが、3 次元を超えることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="ef274-134">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>

> [!NOTE]
> <span data-ttu-id="ef274-135">配列に次元を追加すると、配列に必要なストレージの合計が大幅に増えるので、多次元配列を使うときは気を付けてください。</span><span class="sxs-lookup"><span data-stu-id="ef274-135">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>

## <a name="using-different-dimensions"></a><span data-ttu-id="ef274-136">さまざまな次元の使用</span><span class="sxs-lookup"><span data-stu-id="ef274-136">Using Different Dimensions</span></span>

<span data-ttu-id="ef274-137">今月の毎日の売上高を追跡するとします。</span><span class="sxs-lookup"><span data-stu-id="ef274-137">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="ef274-138">次の例に示すように、31 の要素が含まれる 1 次元配列を宣言できます。各要素が 1 か月の毎日を示します。</span><span class="sxs-lookup"><span data-stu-id="ef274-138">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>

```vb
Dim salesAmounts(30) As Double
```

<span data-ttu-id="ef274-139">次に、1 か月の毎日だけでなく、1 年のすべての月の毎日についても同じ情報を追跡するとします。</span><span class="sxs-lookup"><span data-stu-id="ef274-139">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="ef274-140">次の例に示すように、12 行 (月)、31 列 (日) の 2 次元配列を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ef274-140">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>

```vb
Dim salesAmounts(11, 30) As Double
```

<span data-ttu-id="ef274-141">次は、複数年にわたる情報を配列で保持することにします。</span><span class="sxs-lookup"><span data-stu-id="ef274-141">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="ef274-142">5 年間の売上高を追跡する場合は、次の例に示すように、5 レイヤー、12 行、31 列の 3 次元配列を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ef274-142">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>

```vb
Dim salesAmounts(4, 11, 30) As Double
```

<span data-ttu-id="ef274-143">各インデックスは 0 から最大値の間で変化するため、`salesAmounts` の各次元は、その次元に必要な長さよりも 1 つ小さい値として宣言されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ef274-143">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="ef274-144">また、新しい次元ごとに配列のサイズが増加することにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="ef274-144">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="ef274-145">上記の例の 3 つのサイズは、それぞれ 31、372、および 1,860 要素です。</span><span class="sxs-lookup"><span data-stu-id="ef274-145">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="ef274-146">`Dim` ステートメントまたは `New` 句を 使用せずに、すべての配列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ef274-146">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="ef274-147">たとえば、<xref:System.Array.CreateInstance%2A> メソッドを呼び出すか、別のコンポーネントでこの方法で作成した配列をコードに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="ef274-147">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="ef274-148">このような配列には、0 以外の下限を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ef274-148">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="ef274-149"><xref:System.Array.GetLowerBound%2A> メソッドまたは `LBound` 関数を使用すると、次元の下限をいつでもテストできます。</span><span class="sxs-lookup"><span data-stu-id="ef274-149">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef274-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef274-150">See also</span></span>

- [<span data-ttu-id="ef274-151">配列</span><span class="sxs-lookup"><span data-stu-id="ef274-151">Arrays</span></span>](index.md)
- [<span data-ttu-id="ef274-152">配列のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ef274-152">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
