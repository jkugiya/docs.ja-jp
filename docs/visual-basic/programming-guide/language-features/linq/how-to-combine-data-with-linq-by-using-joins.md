---
description: '詳細情報: 方法:LINQ の結合を使用してデータを結合する (Visual Basic)'
title: '方法: LINQ の結合を使用してデータを結合する'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 69cf0bcfb8d9241afdd0616621f35d7ca93bbb9e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422745"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="23315-103">方法: LINQ の結合を使用してデータを結合する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23315-103">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>

<span data-ttu-id="23315-104">Visual Basic では、コレクション間の共通値に基づいて複数のコレクションの内容を結合できるようにするための、`Join` および `Group Join` クエリ句が提供されます。</span><span class="sxs-lookup"><span data-stu-id="23315-104">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="23315-105">これらの値は "*キー*" 値と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="23315-105">These values are known as *key* values.</span></span> <span data-ttu-id="23315-106">リレーショナル データベースの概念をよく理解している開発者は、`Join` 句を内部結合として認識し、`Group Join` 句を実質的に左外部結合として認識します。</span><span class="sxs-lookup"><span data-stu-id="23315-106">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="23315-107">このトピックの例では、`Join` と `Group Join` のクエリ句を使用してデータを結合するいくつかの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="23315-107">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="23315-108">プロジェクトを作成してサンプル データを追加する</span><span class="sxs-lookup"><span data-stu-id="23315-108">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="23315-109">サンプルのデータと種類を含むプロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="23315-109">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="23315-110">このトピックのサンプルを実行するには、Visual Studio を開き、新しい Visual Basic コンソール アプリケーションのプロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="23315-110">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="23315-111">Visual Basic によって作成された Module1.vb ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="23315-111">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="23315-112">このトピックのサンプルでは、次のコード例の `Person` および `Pet` という種類とデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="23315-112">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="23315-113">Visual Basic によって作成された既定の `Module1` モジュールに、このコードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="23315-113">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="23315-114">Join 句を使用して内部結合を実行する</span><span class="sxs-lookup"><span data-stu-id="23315-114">Perform an Inner Join by Using the Join Clause</span></span>  

 <span data-ttu-id="23315-115">内部結合では、2 つのコレクションのデータを結合します。</span><span class="sxs-lookup"><span data-stu-id="23315-115">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="23315-116">指定されたキー値が一致する項目が含まれます。</span><span class="sxs-lookup"><span data-stu-id="23315-116">Items for which the specified key values match are included.</span></span> <span data-ttu-id="23315-117">いずれかのコレクションの項目のうち、他のコレクションに一致する項目がないものは除外されます。</span><span class="sxs-lookup"><span data-stu-id="23315-117">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="23315-118">Visual Basic では、LINQ で内部結合を実行するためのオプションとして、暗黙的な結合と明示的な結合という 2 つが提供されます。</span><span class="sxs-lookup"><span data-stu-id="23315-118">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="23315-119">暗黙的な結合では、`From` 句で結合されるコレクションを指定し、`Where` 句で一致するキー フィールドを識別します。</span><span class="sxs-lookup"><span data-stu-id="23315-119">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="23315-120">Visual Basic では、指定されたキー フィールドに基づいて、2 つのコレクションを暗黙的に結合します。</span><span class="sxs-lookup"><span data-stu-id="23315-120">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="23315-121">結合で使用するキー フィールドを特定する場合は、`Join` 句を使用して明示的な結合を指定できます。</span><span class="sxs-lookup"><span data-stu-id="23315-121">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="23315-122">この場合も、`Where` 句を使用してクエリ結果をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="23315-122">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="23315-123">Join 句を使用して内部結合を実行するには</span><span class="sxs-lookup"><span data-stu-id="23315-123">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="23315-124">次のコードをプロジェクトの `Module1` モジュールに追加して、暗黙的および明示的な内部結合の両方の例を確認します。</span><span class="sxs-lookup"><span data-stu-id="23315-124">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="23315-125">Group Join 句を使用して左外部結合を実行する</span><span class="sxs-lookup"><span data-stu-id="23315-125">Perform a Left Outer Join by Using the Group Join Clause</span></span>  

 <span data-ttu-id="23315-126">左外部結合には、結合の左側のコレクションのすべての項目と、結合の右側のコレクションで一致する値のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="23315-126">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="23315-127">左側のコレクションに一致する項目がない、結合の右側のコレクションの項目はすべて、クエリ結果から除外されます。</span><span class="sxs-lookup"><span data-stu-id="23315-127">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="23315-128">`Group Join` 句では、実際には左外部結合を実行します。</span><span class="sxs-lookup"><span data-stu-id="23315-128">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="23315-129">通常は左外部結合と呼ばれるものと、`Group Join` 句で返されるものの違いは、`Group Join` 句では、左側のコレクションの項目ごとに、結合の右側のコレクションからの結果がグループ化されることです。</span><span class="sxs-lookup"><span data-stu-id="23315-129">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="23315-130">リレーショナル データベースでは、左外部結合でグループ化されていない結果が返されます。この場合、クエリ結果の各項目には、結合の両方のコレクションの一致する項目が含まれます。</span><span class="sxs-lookup"><span data-stu-id="23315-130">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="23315-131">この場合、結合の左側のコレクションの項目が、右側のコレクションの一致する項目ごとに繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="23315-131">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="23315-132">次の手順を完了すると、このようになるのがわかります。</span><span class="sxs-lookup"><span data-stu-id="23315-132">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="23315-133">クエリを拡張してグループ化されたクエリ結果ごとに 1 つの項目を返すようにすることで、`Group Join` クエリの結果をグループ化されていない結果として取得できます。</span><span class="sxs-lookup"><span data-stu-id="23315-133">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="23315-134">そのためには、グループ化されたコレクションの `DefaultIfEmpty` メソッドに対してクエリを確実に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23315-134">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="23315-135">これにより、右側のコレクションに一致する結果がない場合でも、確実に結合の左側のコレクションの項目がクエリ結果に引き続き含まれるようになります。</span><span class="sxs-lookup"><span data-stu-id="23315-135">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="23315-136">結合の右側のコレクションに一致する値がない場合は、クエリにコードを追加して既定の結果値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="23315-136">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="23315-137">Group Join 句を使用して左外部結合を実行するには</span><span class="sxs-lookup"><span data-stu-id="23315-137">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="23315-138">次のコードをプロジェクトの `Module1` モジュールに追加して、グループ化された左外部結合とグループ化されていない左外部結合の両方の例を確認します。</span><span class="sxs-lookup"><span data-stu-id="23315-138">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="23315-139">複合キーを使用して結合を実行する</span><span class="sxs-lookup"><span data-stu-id="23315-139">Perform a Join by Using a Composite Key</span></span>  

 <span data-ttu-id="23315-140">`Join` または `Group Join` 句で `And` キーワードを使用すると、結合されるコレクションの値を照合するときに使用する複数のキー フィールドを識別できます。</span><span class="sxs-lookup"><span data-stu-id="23315-140">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="23315-141">`And` キーワードでは、結合される項目について、指定されたすべてのキー フィールドが一致する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="23315-141">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="23315-142">複合キーを使用して結合を実行するには</span><span class="sxs-lookup"><span data-stu-id="23315-142">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="23315-143">次のコードをプロジェクトの `Module1` モジュールに追加して、複合キーを使用する結合の例を確認します。</span><span class="sxs-lookup"><span data-stu-id="23315-143">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="23315-144">コードを実行する</span><span class="sxs-lookup"><span data-stu-id="23315-144">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="23315-145">例を実行するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="23315-145">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="23315-146">プロジェクトの `Module1` モジュールの `Sub Main` を次のコードに置き換えて、このトピックの例を実行します。</span><span class="sxs-lookup"><span data-stu-id="23315-146">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="23315-147">F5 キーを押して例を実行します。</span><span class="sxs-lookup"><span data-stu-id="23315-147">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23315-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="23315-148">See also</span></span>

- [<span data-ttu-id="23315-149">LINQ</span><span class="sxs-lookup"><span data-stu-id="23315-149">LINQ</span></span>](index.md)
- [<span data-ttu-id="23315-150">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="23315-150">Introduction to LINQ in Visual Basic</span></span>](introduction-to-linq.md)
- [<span data-ttu-id="23315-151">Join 句</span><span class="sxs-lookup"><span data-stu-id="23315-151">Join Clause</span></span>](../../../language-reference/queries/join-clause.md)
- [<span data-ttu-id="23315-152">Group Join 句</span><span class="sxs-lookup"><span data-stu-id="23315-152">Group Join Clause</span></span>](../../../language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="23315-153">From 句</span><span class="sxs-lookup"><span data-stu-id="23315-153">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="23315-154">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="23315-154">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="23315-155">クエリ</span><span class="sxs-lookup"><span data-stu-id="23315-155">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="23315-156">LINQ によるデータ変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="23315-156">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
