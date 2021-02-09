---
description: '詳細情報: 方法:EntityCommand を使用してパラメーター化されたストアド プロシージャを実行する'
title: '方法: EntityCommand を使用してパラメーター化されたストアド プロシージャを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: a45c9a276cc33037a4d353e05d1174c9748aab82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650691"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="e28d4-103">方法: EntityCommand を使用してパラメーター化されたストアド プロシージャを実行する</span><span class="sxs-lookup"><span data-stu-id="e28d4-103">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>

<span data-ttu-id="e28d4-104">このトピックでは、<xref:System.Data.EntityClient.EntityCommand> クラスを使用して、パラメーター化されたストアド プロシージャを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e28d4-104">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="e28d4-105">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="e28d4-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="e28d4-106">[School モデル](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="e28d4-106">Add the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="e28d4-107">詳細については、[Entity Data Model ウィザードを使用する](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e28d4-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="e28d4-108">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="e28d4-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="e28d4-109">`GetStudentGrades` ストアド プロシージャをインポートし、戻り値の型として `CourseGrade` エンティティを指定します。</span><span class="sxs-lookup"><span data-stu-id="e28d4-109">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="e28d4-110">ストアド プロシージャのインポート方法については、「[方法: ストアド プロシージャをインポートする](/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e28d4-110">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e28d4-111">例</span><span class="sxs-lookup"><span data-stu-id="e28d4-111">Example</span></span>  

 <span data-ttu-id="e28d4-112">次のコードでは、`GetStudentGrades` ストアド プロシージャが実行されます。`StudentId` は必須パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="e28d4-112">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="e28d4-113">結果は <xref:System.Data.EntityClient.EntityDataReader> によって読み取られます。</span><span class="sxs-lookup"><span data-stu-id="e28d4-113">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="e28d4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e28d4-114">See also</span></span>

- [<span data-ttu-id="e28d4-115">Entity Framework 用の EntityClient プロバイダー</span><span class="sxs-lookup"><span data-stu-id="e28d4-115">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
