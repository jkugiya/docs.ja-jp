---
description: '詳細情報: ストアド プロシージャ'
title: ストアド プロシージャ
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 16157dc5a8d2da880deb2d43b649b872d19c73a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681436"
---
# <a name="stored-procedures"></a><span data-ttu-id="f705a-103">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f705a-103">Stored Procedures</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f705a-104">では、オブジェクト モデル内のメソッドを使用して、データベースのストアド プロシージャが表されます。</span><span class="sxs-lookup"><span data-stu-id="f705a-104">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="f705a-105"><xref:System.Data.Linq.Mapping.FunctionAttribute> 属性、および必要に応じて <xref:System.Data.Linq.Mapping.ParameterAttribute> 属性を適用することによって、メソッドをストアド プロシージャとして指定します。</span><span class="sxs-lookup"><span data-stu-id="f705a-105">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="f705a-106">詳しくは、「[LINQ to SQL オブジェクト モデル](the-linq-to-sql-object-model.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f705a-106">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="f705a-107">Visual Studio を使用している開発者は、通常、オブジェクト リレーショナル デザイナーを使用してストアド プロシージャを対応付けます。</span><span class="sxs-lookup"><span data-stu-id="f705a-107">Developers using Visual Studio would typically use the Object Relational Designer to map stored procedures.</span></span> <span data-ttu-id="f705a-108">このセクションのトピックでは、自分でコードを作成する場合に、アプリケーション内でこれらのメソッドを記述および呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f705a-108">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f705a-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f705a-109">In This Section</span></span>  

 [<span data-ttu-id="f705a-110">方法: 行セットを返す</span><span class="sxs-lookup"><span data-stu-id="f705a-110">How to: Return Rowsets</span></span>](how-to-return-rowsets.md)  
 <span data-ttu-id="f705a-111">データ行を返す方法および入力パラメーターの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f705a-111">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="f705a-112">方法: パラメーターを受け取るストアド プロシージャを使用する</span><span class="sxs-lookup"><span data-stu-id="f705a-112">How to: Use Stored Procedures that Take Parameters</span></span>](how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="f705a-113">入力パラメーターおよび出力パラメーターの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f705a-113">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="f705a-114">方法: 複数の結果形状が割り当てられたストアド プロシージャを使用する</span><span class="sxs-lookup"><span data-stu-id="f705a-114">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="f705a-115">同じストアド プロシージャで複数の形状の結果を返す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f705a-115">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="f705a-116">方法: シーケンシャルな結果形状が割り当てられたストアド プロシージャを使用する</span><span class="sxs-lookup"><span data-stu-id="f705a-116">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="f705a-117">リターン シーケンスが既知の場合に複数の形状を返す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f705a-117">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="f705a-118">ストアド プロシージャによる操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="f705a-118">Customizing Operations By Using Stored Procedures</span></span>](customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="f705a-119">ストアド プロシージャを使用して挿入、更新、および削除の操作を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f705a-119">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="f705a-120">ストアド プロシージャのみによる操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="f705a-120">Customizing Operations by Using Stored Procedures Exclusively</span></span>](customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="f705a-121">ストアド プロシージャのみを使用して挿入、更新、および削除の操作を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f705a-121">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f705a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="f705a-122">Related Sections</span></span>  

 [<span data-ttu-id="f705a-123">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f705a-123">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="f705a-124">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] オブジェクト モデルを作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f705a-124">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="f705a-125">チュートリアル: ストアド プロシージャのみの使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f705a-125">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="f705a-126">Visual Basic でストアド プロシージャを使用する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="f705a-126">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="f705a-127">チュートリアル: ストアド プロシージャのみを使用する (C#)</span><span class="sxs-lookup"><span data-stu-id="f705a-127">Walkthrough: Using Only Stored Procedures (C#)</span></span>](walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="f705a-128">C# でストアド プロシージャを使用する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="f705a-128">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
