---
description: '詳細情報: 方法:Navigate 演算子でリレーションシップをナビゲートする'
title: '方法: Navigate 演算子でリレーションシップをナビゲートする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
ms.openlocfilehash: ff419a959c2ec895a238d37caeedcf1f06812050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697531"
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a><span data-ttu-id="09ac2-103">方法: Navigate 演算子でリレーションシップをナビゲートする</span><span class="sxs-lookup"><span data-stu-id="09ac2-103">How to: Navigate Relationships with the Navigate Operator</span></span>

<span data-ttu-id="09ac2-104">このトピックでは、<xref:System.Data.EntityClient.EntityCommand> オブジェクトを使用して概念モデルに対してコマンドを実行する方法と、<xref:System.Data.Metadata.Edm.RefType> を使用して <xref:System.Data.EntityClient.EntityDataReader> の結果を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09ac2-104">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="09ac2-105">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="09ac2-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="09ac2-106">[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="09ac2-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="09ac2-107">詳細については、[Entity Data Model ウィザードを使用する](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09ac2-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="09ac2-108">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="09ac2-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="09ac2-109">例</span><span class="sxs-lookup"><span data-stu-id="09ac2-109">Example</span></span>  

 <span data-ttu-id="09ac2-110">次の例では、[!INCLUDE[esql](../../../../../includes/esql-md.md)] で [NAVIGATE](./language-reference/navigate-entity-sql.md) 演算子を使用してリレーションシップをナビゲートする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09ac2-110">The following example shows how to navigate relationships in [!INCLUDE[esql](../../../../../includes/esql-md.md)] by using the [NAVIGATE](./language-reference/navigate-entity-sql.md) operator.</span></span> <span data-ttu-id="09ac2-111">`Navigate` 演算子は、エンティティのインスタンス、リレーションシップの種類、リレーションシップの終端エンティティ、および、リレーションシップの開始エンティティをパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="09ac2-111">The `Navigate` operator takes the following parameters: an instance of an entity, the relationship type, the end of the relationship, and the beginning of the relationship.</span></span> <span data-ttu-id="09ac2-112">必要に応じて、`Navigate` 演算子には、エンティティのインスタンスとリレーションシップの種類だけを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="09ac2-112">Optionally, you can pass only an instance of an entity and the relationship type to the `Navigate` operator.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="09ac2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="09ac2-113">See also</span></span>

- [<span data-ttu-id="09ac2-114">Entity Framework 用の EntityClient プロバイダー</span><span class="sxs-lookup"><span data-stu-id="09ac2-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="09ac2-115">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="09ac2-115">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
