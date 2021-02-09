---
description: '詳細情報: 方法:入れ子になったコレクションを返すクエリを実行する'
title: '方法: 入れ子になったコレクションを返すクエリを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 941b7471820c09224e6828fac6e17b92f70ff57e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650626"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="ac7b3-103">方法: 入れ子になったコレクションを返すクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="ac7b3-103">How to: Execute a Query that Returns Nested Collections</span></span>

<span data-ttu-id="ac7b3-104">ここでは、<xref:System.Data.EntityClient.EntityCommand> オブジェクトを使用して概念モデルに対してコマンドを実行する方法、および <xref:System.Data.EntityClient.EntityDataReader> を使用して入れ子になったコレクションの結果を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac7b3-104">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="ac7b3-105">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="ac7b3-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="ac7b3-106">[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="ac7b3-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="ac7b3-107">詳細については、[Entity Data Model ウィザードを使用する](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac7b3-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="ac7b3-108">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="ac7b3-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="ac7b3-109">例</span><span class="sxs-lookup"><span data-stu-id="ac7b3-109">Example</span></span>  

 <span data-ttu-id="ac7b3-110">"*入れ子になったコレクション*" とは、別のコレクションに含まれているコレクションのことです。</span><span class="sxs-lookup"><span data-stu-id="ac7b3-110">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="ac7b3-111">次に示すコードでは、`Contacts` のコレクションと、それぞれの `SalesOrderHeaders` に関連付けられている、`Contact` の入れ子になったコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="ac7b3-111">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="ac7b3-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac7b3-112">See also</span></span>

- [<span data-ttu-id="ac7b3-113">Entity Framework 用の EntityClient プロバイダー</span><span class="sxs-lookup"><span data-stu-id="ac7b3-113">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
