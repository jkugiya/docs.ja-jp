---
description: '詳細情報: 方法:EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する'
title: '方法: EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: c3eb9fdfbad986d54104e94aa719a57edfa14b19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650782"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="e55a8-103">方法: EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="e55a8-103">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>

<span data-ttu-id="e55a8-104">このトピックでは、<xref:System.Data.EntityClient.EntityCommand> オブジェクトを使用して、パラメーターのある [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e55a8-104">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="e55a8-105">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="e55a8-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="e55a8-106">[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="e55a8-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="e55a8-107">詳細については、[Entity Data Model ウィザードを使用する](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e55a8-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="e55a8-108">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="e55a8-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="e55a8-109">例</span><span class="sxs-lookup"><span data-stu-id="e55a8-109">Example</span></span>  

 <span data-ttu-id="e55a8-110">次の例では、2 つのパラメーターを持つクエリ文字列を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e55a8-110">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="e55a8-111">次に、<xref:System.Data.EntityClient.EntityCommand> を作成した後、2 つのパラメーターを <xref:System.Data.EntityClient.EntityParameter> の <xref:System.Data.EntityClient.EntityCommand> コレクションに追加し、`Contact` アイテムのコレクションに対して反復処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="e55a8-111">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="e55a8-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e55a8-112">See also</span></span>

- <span data-ttu-id="e55a8-113">[方法: パラメーター化されたクエリを実行する](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e55a8-113">[How to: Execute a Parameterized Query](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>
- [<span data-ttu-id="e55a8-114">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="e55a8-114">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
