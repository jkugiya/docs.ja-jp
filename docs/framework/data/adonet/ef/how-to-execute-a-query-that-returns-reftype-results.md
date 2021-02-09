---
description: '詳細情報: 方法:RefType 結果を返すクエリを実行する'
title: '方法: RefType 結果を返すクエリを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
ms.openlocfilehash: f62ea7ab3820ebbc63955c13e761726b58fad872
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650584"
---
# <a name="how-to-execute-a-query-that-returns-reftype-results"></a><span data-ttu-id="0071d-103">方法: RefType 結果を返すクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="0071d-103">How to: Execute a Query that Returns RefType Results</span></span>

<span data-ttu-id="0071d-104">このトピックでは、<xref:System.Data.EntityClient.EntityCommand> オブジェクトを使用して概念モデルに対してコマンドを実行する方法と、<xref:System.Data.Metadata.Edm.RefType> を使用して <xref:System.Data.EntityClient.EntityDataReader> の結果を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0071d-104">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="0071d-105">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="0071d-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="0071d-106">[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="0071d-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="0071d-107">詳細については、[Entity Data Model ウィザードを使用する](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0071d-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="0071d-108">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="0071d-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="0071d-109">例</span><span class="sxs-lookup"><span data-stu-id="0071d-109">Example</span></span>  

 <span data-ttu-id="0071d-110">この例は、<xref:System.Data.Metadata.Edm.RefType> の結果を返すクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="0071d-110">This example executes a query that returns <xref:System.Data.Metadata.Edm.RefType> results.</span></span> <span data-ttu-id="0071d-111">次のクエリを引数として `ExecuteRefTypeQuery` 関数に渡すと、関数はエンティティへの参照を返します。</span><span class="sxs-lookup"><span data-stu-id="0071d-111">If you pass the following query as an argument to the `ExecuteRefTypeQuery` function, the function returns a reference to the entity:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref2)]  
  
 <span data-ttu-id="0071d-112">パラメーター化されたクエリを渡す場合は、次のように、<xref:System.Data.EntityClient.EntityParameter> オブジェクトの <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> プロパティに <xref:System.Data.EntityClient.EntityCommand> オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="0071d-112">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## <a name="see-also"></a><span data-ttu-id="0071d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0071d-113">See also</span></span>

- [<span data-ttu-id="0071d-114">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="0071d-114">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="0071d-115">Entity Framework 用の EntityClient プロバイダー</span><span class="sxs-lookup"><span data-stu-id="0071d-115">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
