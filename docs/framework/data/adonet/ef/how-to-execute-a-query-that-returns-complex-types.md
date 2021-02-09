---
description: '詳細情報: 方法:複合型を返すクエリを実行する'
title: '方法: 複合型を返すクエリを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 9a7fb3ea695115529b69def9f95281bac7f33273
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650678"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="60b98-103">方法: 複合型を返すクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="60b98-103">How to: Execute a Query that Returns Complex Types</span></span>

<span data-ttu-id="60b98-104">このトピックでは、複合型プロパティを含むエンティティ型オブジェクトを返す [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="60b98-104">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="60b98-105">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="60b98-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="60b98-106">[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="60b98-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="60b98-107">詳細については、[Entity Data Model ウィザードを使用する](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60b98-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="60b98-108">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="60b98-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="60b98-109">.edmx ファイルをダブルクリックして、エンティティ デザイナーの [[モデル ブラウザー] ウィンドウ](/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100))にモデルを表示します。</span><span class="sxs-lookup"><span data-stu-id="60b98-109">Double click the .edmx file to display the model in the [Model Browser window](/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) of the Entity Designer.</span></span> <span data-ttu-id="60b98-110">エンティティ デザイナー画面で、`Contact` エンティティ型の `Email` プロパティと `Phone` プロパティを選択し、右クリックして **[新しい複合型へのリファクター]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="60b98-110">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4. <span data-ttu-id="60b98-111">選択した `Email` プロパティと `Phone` プロパティの新しい複合型が **モデル ブラウザー** に追加されます。</span><span class="sxs-lookup"><span data-stu-id="60b98-111">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="60b98-112">複合型には既定の名前が設定されます。 **[プロパティ]** ウィンドウで型の名前を `EmailPhone` に変更します。</span><span class="sxs-lookup"><span data-stu-id="60b98-112">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="60b98-113">また、新しい `ComplexProperty` プロパティが `Contact` エンティティ型に追加されます。</span><span class="sxs-lookup"><span data-stu-id="60b98-113">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="60b98-114">プロパティの名前を `EmailPhoneComplexType.` に変更します。</span><span class="sxs-lookup"><span data-stu-id="60b98-114">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="60b98-115">Entity Data Model ウィザードを使用した複合型の作成と変更について詳しくは、「[方法: 既存のプロパティを複合型プロパティにリファクタリングする](/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100))」および「[方法: 複合型を作成および変更する](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="60b98-115">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) and [How to: Create and Modify Complex Types](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60b98-116">例</span><span class="sxs-lookup"><span data-stu-id="60b98-116">Example</span></span>  

 <span data-ttu-id="60b98-117">次の例では、`Contact` オブジェクトのコレクションを返し、`Contact` オブジェクトの 2 つのプロパティである `ContactID` と `EmailPhoneComplexType` 複合型の値を表示するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="60b98-117">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
