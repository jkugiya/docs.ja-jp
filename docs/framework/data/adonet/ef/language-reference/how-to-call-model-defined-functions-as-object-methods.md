---
description: '詳細情報: 方法:モデル定義関数をオブジェクト メソッドとして呼び出す'
title: '方法: モデル定義関数をオブジェクト メソッドとして呼び出す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 46f171d5785bf715382e87c3fb7dae932db0bb65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748675"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a><span data-ttu-id="a592d-103">方法: モデル定義関数をオブジェクト メソッドとして呼び出す</span><span class="sxs-lookup"><span data-stu-id="a592d-103">How to: Call Model-Defined Functions as Object Methods</span></span>

<span data-ttu-id="a592d-104">ここでは、モデル定義関数を <xref:System.Data.Objects.ObjectContext> オブジェクトのメソッドまたはカスタム クラスの静的メソッドとして呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a592d-104">This topic describes how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object or as a static method on a custom class.</span></span> <span data-ttu-id="a592d-105">*モデル定義関数* は、概念モデルで定義される関数です。</span><span class="sxs-lookup"><span data-stu-id="a592d-105">A *model-defined function* is a function that is defined in the conceptual model.</span></span> <span data-ttu-id="a592d-106">このトピックで説明する手順は、これらの関数を LINQ to Entities クエリから呼び出すのではなく、直接呼び出す方法を示すものです。</span><span class="sxs-lookup"><span data-stu-id="a592d-106">The procedures in the topic describe how to call these functions directly instead of calling them from LINQ to Entities queries.</span></span> <span data-ttu-id="a592d-107">モデル定義関数を LINQ to Entities クエリに呼び出す方法の詳細については、「[方法:クエリを使用してモデル定義関数を呼び出す](how-to-call-model-defined-functions-in-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a592d-107">For information about calling model-defined functions in LINQ to Entities queries, see [How to: Call Model-Defined Functions in Queries](how-to-call-model-defined-functions-in-queries.md).</span></span>  
  
 <span data-ttu-id="a592d-108">モデル定義関数を <xref:System.Data.Objects.ObjectContext> メソッドとして呼び出す場合も、カスタム クラスの静的メソッドとして呼び出す場合も、ます <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> でメソッドをモデル定義関数にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a592d-108">Whether you call a model-defined function as an <xref:System.Data.Objects.ObjectContext> method or as a static method on a custom class, you must first map the method to the model-defined function with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="a592d-109">ただし、<xref:System.Data.Objects.ObjectContext> クラスのメソッドを定義するときには、<xref:System.Data.Objects.ObjectContext.QueryProvider%2A> プロパティを使用して LINQ プロバイダーを公開する必要があります。それに対して、カスタム クラスの静的メソッドを定義するときには、<xref:System.Linq.IQueryable.Provider%2A> プロパティを使用して LINQ プロバイダーを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a592d-109">However, when you define a method on the <xref:System.Data.Objects.ObjectContext> class, you must use the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property to expose the LINQ provider, whereas when you define a static method on a custom class, you must use the <xref:System.Linq.IQueryable.Provider%2A> property to expose the LINQ provider.</span></span> <span data-ttu-id="a592d-110">詳細については、下の手順の後に示した例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a592d-110">For more information, see the examples that follow the procedures below.</span></span>  
  
 <span data-ttu-id="a592d-111">下の手順は、モデル定義関数を <xref:System.Data.Objects.ObjectContext> オブジェクトのメソッドおよびカスタム クラスの静的メソッドとして呼び出す方法の概要を示したものです。</span><span class="sxs-lookup"><span data-stu-id="a592d-111">The procedures below provide high-level outlines for calling a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object and as a static method on a custom class.</span></span> <span data-ttu-id="a592d-112">詳細な手順は、その後の例で示します。</span><span class="sxs-lookup"><span data-stu-id="a592d-112">The examples that follow provide more detail about the steps in the procedures.</span></span> <span data-ttu-id="a592d-113">この手順では、関数を概念モデルで定義済みであると想定します。</span><span class="sxs-lookup"><span data-stu-id="a592d-113">The procedures assume that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="a592d-114">詳細については、[概念モデルでカスタム関数を定義する](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a592d-114">For more information, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a><span data-ttu-id="a592d-115">モデル定義関数を ObjectContext オブジェクトのメソッドとして呼び出すには</span><span class="sxs-lookup"><span data-stu-id="a592d-115">To call a model-defined function as a method on an ObjectContext object</span></span>  
  
1. <span data-ttu-id="a592d-116">ソース ファイルを追加して、部分クラスを拡張します。このクラスは、<xref:System.Data.Objects.ObjectContext> クラスから派生したものであり、Entity Framework ツールによって自動生成されます。</span><span class="sxs-lookup"><span data-stu-id="a592d-116">Add a source file to extend the partial class derived from the <xref:System.Data.Objects.ObjectContext> class, auto-generated by the Entity Framework tools.</span></span> <span data-ttu-id="a592d-117">CLR スタブを別のソース ファイルで定義すると、ファイルを再生成しても変更内容が失われません。</span><span class="sxs-lookup"><span data-stu-id="a592d-117">Defining the CLR stub in a separate source file will prevent the changes from being lost when the file is regenerated.</span></span>  
  
2. <span data-ttu-id="a592d-118">共通言語ランタイム (CLR) メソッドを、次のことを行う <xref:System.Data.Objects.ObjectContext> クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="a592d-118">Add a common language runtime (CLR) method to your <xref:System.Data.Objects.ObjectContext> class that does the following:</span></span>  
  
    - <span data-ttu-id="a592d-119">概念モデルで定義された関数にマップします。</span><span class="sxs-lookup"><span data-stu-id="a592d-119">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="a592d-120">メソッドをマップするには、ユーザーが <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をメソッドに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a592d-120">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="a592d-121">属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間と概念モデルの関数名であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a592d-121">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span> <span data-ttu-id="a592d-122">LINQ の関数名解決では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="a592d-122">Function name resolution for LINQ is case sensitive.</span></span>  
  
    - <span data-ttu-id="a592d-123"><xref:System.Linq.IQueryProvider.Execute%2A> プロパティによって返される <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> メソッドの結果を返します。</span><span class="sxs-lookup"><span data-stu-id="a592d-123">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property.</span></span>  
  
3. <span data-ttu-id="a592d-124">メソッドを <xref:System.Data.Objects.ObjectContext> クラスのインスタンスのメンバーとして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a592d-124">Call the method as a member on an instance of the <xref:System.Data.Objects.ObjectContext> class.</span></span>  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a><span data-ttu-id="a592d-125">モデル定義関数をカスタム クラスの静的メソッドとして呼び出すには</span><span class="sxs-lookup"><span data-stu-id="a592d-125">To call a model-defined function as static method on a custom class</span></span>  
  
1. <span data-ttu-id="a592d-126">クラスを次のことを行う静的メソッドでアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="a592d-126">Add a class to your application with a static method that does the following:</span></span>  
  
    - <span data-ttu-id="a592d-127">概念モデルで定義された関数にマップします。</span><span class="sxs-lookup"><span data-stu-id="a592d-127">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="a592d-128">メソッドをマップするには、ユーザーが <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をメソッドに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a592d-128">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="a592d-129">属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間と概念モデルの関数名であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a592d-129">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span>  
  
    - <span data-ttu-id="a592d-130"><xref:System.Linq.IQueryable> 引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a592d-130">Accepts an <xref:System.Linq.IQueryable> argument.</span></span>  
  
    - <span data-ttu-id="a592d-131"><xref:System.Linq.IQueryProvider.Execute%2A> プロパティによって返される <xref:System.Linq.IQueryable.Provider%2A> メソッドの結果を返します。</span><span class="sxs-lookup"><span data-stu-id="a592d-131">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Linq.IQueryable.Provider%2A> property.</span></span>  
  
2. <span data-ttu-id="a592d-132">メソッドをカスタム クラスの静的メソッドのメンバーとして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a592d-132">Call the method as a member a static method on the custom class</span></span>  
  
## <a name="example"></a><span data-ttu-id="a592d-133">例</span><span class="sxs-lookup"><span data-stu-id="a592d-133">Example</span></span>  

 <span data-ttu-id="a592d-134">**モデル定義関数を ObjectContext オブジェクトのメソッドとして呼び出す**</span><span class="sxs-lookup"><span data-stu-id="a592d-134">**Calling a Model-Defined Function as a Method on an ObjectContext Object**</span></span>  
  
 <span data-ttu-id="a592d-135">次の例で、モデル定義関数を <xref:System.Data.Objects.ObjectContext> オブジェクトのメソッドとして呼び出す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a592d-135">The following example demonstrates how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object.</span></span> <span data-ttu-id="a592d-136">この例では、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を使用します。</span><span class="sxs-lookup"><span data-stu-id="a592d-136">The example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
 <span data-ttu-id="a592d-137">指定製品の製品収益を返す下の概念モデル関数について考察してください </span><span class="sxs-lookup"><span data-stu-id="a592d-137">Consider the conceptual model function below that returns product revenue for a specified product.</span></span> <span data-ttu-id="a592d-138">(関数を概念モデルに追加する方法については、「[方法:概念モデルでカスタム関数を定義する](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))」を参照してください。)</span><span class="sxs-lookup"><span data-stu-id="a592d-138">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a><span data-ttu-id="a592d-139">例</span><span class="sxs-lookup"><span data-stu-id="a592d-139">Example</span></span>  

 <span data-ttu-id="a592d-140">次のコードでは、メソッドを上の概念モデル関数にマップする `AdventureWorksEntities` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="a592d-140">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="a592d-141">例</span><span class="sxs-lookup"><span data-stu-id="a592d-141">Example</span></span>  

 <span data-ttu-id="a592d-142">次のコードでは、上のメソッドを呼び出して、指定製品の製品収益を表示します。</span><span class="sxs-lookup"><span data-stu-id="a592d-142">The following code calls the method above to display the product revenue for a specified product:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a592d-143">例</span><span class="sxs-lookup"><span data-stu-id="a592d-143">Example</span></span>  

 <span data-ttu-id="a592d-144">次の例で、コレクション (<xref:System.Linq.IQueryable%601> オブジェクトとして) を返すモデル定義関数を呼び出す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a592d-144">The following example demonstrates how to call a model-defined function that returns a collection (as an <xref:System.Linq.IQueryable%601> object).</span></span> <span data-ttu-id="a592d-145">指定された製品 ID に関して `SalesOrderDetails` をすべて返す下の概念モデル関数について考察してください。</span><span class="sxs-lookup"><span data-stu-id="a592d-145">Consider the conceptual model function below that returns all the `SalesOrderDetails` for a given product ID.</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a><span data-ttu-id="a592d-146">例</span><span class="sxs-lookup"><span data-stu-id="a592d-146">Example</span></span>  

 <span data-ttu-id="a592d-147">次のコードでは、メソッドを上の概念モデル関数にマップする `AdventureWorksEntities` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="a592d-147">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="a592d-148">例</span><span class="sxs-lookup"><span data-stu-id="a592d-148">Example</span></span>  

 <span data-ttu-id="a592d-149">次のコードは、メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a592d-149">The following code calls the method.</span></span> <span data-ttu-id="a592d-150">返された <xref:System.Linq.IQueryable%601> クエリがさらに絞り込まれて、各 `SalesOrderDetail` のライン合計を返すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a592d-150">Note that the returned <xref:System.Linq.IQueryable%601> query is further refined to return line totals for each `SalesOrderDetail`.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="a592d-151">例</span><span class="sxs-lookup"><span data-stu-id="a592d-151">Example</span></span>  

 <span data-ttu-id="a592d-152">**モデル定義関数をカスタム クラスの静的メソッドとして呼び出す**</span><span class="sxs-lookup"><span data-stu-id="a592d-152">**Calling a Model-Defined Function as a Static Method on a Custom Class**</span></span>  
  
 <span data-ttu-id="a592d-153">次の例で、モデル定義関数をカスタム クラスの静的メソッドとして呼び出す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a592d-153">The next example demonstrates how to call a model-defined function as a static method on a custom class.</span></span> <span data-ttu-id="a592d-154">この例では、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を使用します。</span><span class="sxs-lookup"><span data-stu-id="a592d-154">The example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a592d-155">ユーザーが、モデル定義関数をカスタム クラスの静的メソッドとして呼び出すときには、モデル定義関数はコレクションを受け取って、コレクションの値の集計結果を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a592d-155">When you call a model-defined function as a static method on a custom class, the model-defined function must accept a collection and return an aggregation of values in the collection.</span></span>  
  
 <span data-ttu-id="a592d-156">SalesOrderDetail コレクションの製品収益を返す下の概念モデル関数について考察してください </span><span class="sxs-lookup"><span data-stu-id="a592d-156">Consider the conceptual model function below that returns product revenue for a SalesOrderDetail collection.</span></span> <span data-ttu-id="a592d-157">(関数を概念モデルに追加する方法については、「[方法:概念モデルでカスタム関数を定義する](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="a592d-157">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).).</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="a592d-158">例</span><span class="sxs-lookup"><span data-stu-id="a592d-158">Example</span></span>  

 <span data-ttu-id="a592d-159">次のコードでは、上の概念モデル関数にマップする静的メソッドを持つアプリケーションにクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a592d-159">The following code adds a class to your application that contains a static method that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="a592d-160">例</span><span class="sxs-lookup"><span data-stu-id="a592d-160">Example</span></span>  

 <span data-ttu-id="a592d-161">次のコードでは、上のメソッドを呼び出して、SalesOrderDetail コレクションの製品収益を表示します。</span><span class="sxs-lookup"><span data-stu-id="a592d-161">The following code calls the method above to display the product revenue for a SalesOrderDetail collection:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a592d-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="a592d-162">See also</span></span>

- <span data-ttu-id="a592d-163">[.edmx ファイルの概要](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a592d-163">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="a592d-164">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="a592d-164">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="a592d-165">LINQ to Entities クエリ内の関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="a592d-165">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
