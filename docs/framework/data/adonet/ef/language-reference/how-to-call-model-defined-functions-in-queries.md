---
description: '詳細情報: 方法:クエリを使用してモデル定義関数を呼び出す'
title: '方法: クエリを使用してモデル定義関数を呼び出す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: d59ef6edeba1e4b00e0481f8578e9c04735831fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748649"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="a18c8-103">方法: クエリを使用してモデル定義関数を呼び出す</span><span class="sxs-lookup"><span data-stu-id="a18c8-103">How to: Call Model-Defined Functions in Queries</span></span>

<span data-ttu-id="a18c8-104">このトピックでは、概念モデルで定義されている関数を LINQ to Entities クエリから呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a18c8-104">This topic describes how to call functions that are defined in the conceptual model from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="a18c8-105">以下に示す手順は、モデル定義関数を LINQ to Entities クエリから呼び出す方法をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="a18c8-105">The procedure below provides a high-level outline for calling a model-defined function from within a LINQ to Entities query.</span></span> <span data-ttu-id="a18c8-106">各手順の詳しい説明は、その後の例で示します。</span><span class="sxs-lookup"><span data-stu-id="a18c8-106">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="a18c8-107">この手順では、関数を概念モデルで定義済みであると想定します。</span><span class="sxs-lookup"><span data-stu-id="a18c8-107">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="a18c8-108">詳細については、[概念モデルでカスタム関数を定義する](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a18c8-108">For more information, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="a18c8-109">概念モデルで定義された関数を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="a18c8-109">To call a function defined in the conceptual model</span></span>  
  
1. <span data-ttu-id="a18c8-110">概念モデルで定義された関数にマップされているアプリケーションに、共通言語ランタイム (CLR) メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="a18c8-110">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="a18c8-111">メソッドをマップするには、ユーザーが <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をメソッドに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a18c8-111">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="a18c8-112">属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間名と関数名であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a18c8-112">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="a18c8-113">LINQ の関数名解決では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="a18c8-113">Function name resolution for LINQ is case sensitive.</span></span>  
  
2. <span data-ttu-id="a18c8-114">LINQ to Entities クエリから関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a18c8-114">Call the function in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a18c8-115">例</span><span class="sxs-lookup"><span data-stu-id="a18c8-115">Example</span></span>  

 <span data-ttu-id="a18c8-116">次の例は、概念モデルで定義されている関数を LINQ to Entities クエリから呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a18c8-116">The following example demonstrates how to call a function that is defined in the conceptual model from within a LINQ to Entities query.</span></span> <span data-ttu-id="a18c8-117">この例では、School モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="a18c8-117">The example uses the School model.</span></span> <span data-ttu-id="a18c8-118">School モデルの詳細については、「[School サンプル データベースの作成](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))」と「[School .edmx ファイルの生成](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a18c8-118">For information about the School model, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="a18c8-119">次の概念モデル関数は、あるインストラクターが雇用されてから経過した年数を返します。</span><span class="sxs-lookup"><span data-stu-id="a18c8-119">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="a18c8-120">関数を概念モデルに追加する方法については、「[方法:概念モデルでカスタム関数を定義する](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))」を参照してください。)</span><span class="sxs-lookup"><span data-stu-id="a18c8-120">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="a18c8-121">例</span><span class="sxs-lookup"><span data-stu-id="a18c8-121">Example</span></span>  

 <span data-ttu-id="a18c8-122">次に、次のメソッドをアプリケーションに追加し、<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> を使用して概念モデル関数にマップします。</span><span class="sxs-lookup"><span data-stu-id="a18c8-122">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="a18c8-123">例</span><span class="sxs-lookup"><span data-stu-id="a18c8-123">Example</span></span>  

 <span data-ttu-id="a18c8-124">これで、LINQ to Entities クエリから概念モデル関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a18c8-124">Now you can call the conceptual model function from within a LINQ to Entities query.</span></span> <span data-ttu-id="a18c8-125">次のコードは、雇用年数が 10 年を超えるすべてのインストラクターを表示するメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a18c8-125">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a18c8-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a18c8-126">See also</span></span>

- <span data-ttu-id="a18c8-127">[.edmx ファイルの概要](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a18c8-127">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="a18c8-128">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="a18c8-128">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="a18c8-129">LINQ to Entities クエリ内の関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="a18c8-129">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="a18c8-130">方法: モデル定義関数をオブジェクト メソッドとして呼び出す</span><span class="sxs-lookup"><span data-stu-id="a18c8-130">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)
