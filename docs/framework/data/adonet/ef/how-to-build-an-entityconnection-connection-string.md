---
description: '詳細情報: 方法:EntityConnection の接続文字列を作成する'
title: '方法: EntityConnection の接続文字列を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
ms.openlocfilehash: 760ed9d1f362e08135586a56a6b900afcd2b13bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650834"
---
# <a name="how-to-build-an-entityconnection-connection-string"></a><span data-ttu-id="0702b-103">方法: EntityConnection の接続文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="0702b-103">How to: Build an EntityConnection Connection String</span></span>

<span data-ttu-id="0702b-104">このトピックでは、<xref:System.Data.EntityClient.EntityConnection> を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0702b-104">This topic provides an example of how to build an <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="0702b-105">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="0702b-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="0702b-106">[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="0702b-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="0702b-107">詳細については、[Entity Data Model ウィザードを使用する](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0702b-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="0702b-108">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="0702b-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="0702b-109">例</span><span class="sxs-lookup"><span data-stu-id="0702b-109">Example</span></span>  

 <span data-ttu-id="0702b-110">次の例では、基になるプロバイダーの <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> を初期化した後、<xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> オブジェクトを初期化して、このオブジェクトを <xref:System.Data.EntityClient.EntityConnection> のコンストラクターに渡しています。</span><span class="sxs-lookup"><span data-stu-id="0702b-110">The following example initializes the <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> for the underlying provider, then initializes the <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> object and passes this object to the constructor of the <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="0702b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0702b-111">See also</span></span>

- <span data-ttu-id="0702b-112">[方法: オブジェクト コンテキストで EntityConnection を使用する](/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))」</span><span class="sxs-lookup"><span data-stu-id="0702b-112">[How to: Use EntityConnection with an Object Context](/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))</span></span>
- [<span data-ttu-id="0702b-113">Entity Framework 用の EntityClient プロバイダー</span><span class="sxs-lookup"><span data-stu-id="0702b-113">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
