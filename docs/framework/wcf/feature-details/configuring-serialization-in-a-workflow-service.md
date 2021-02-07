---
description: 詳細については、「ワークフローサービスでのシリアル化の構成」を参照してください。
title: ワークフロー サービス内でのシリアル化の構成
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: e268f82fc3c1f65086e3c6b112e481ad8abed070
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743240"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="78ab6-103">ワークフロー サービス内でのシリアル化の構成</span><span class="sxs-lookup"><span data-stu-id="78ab6-103">Configuring Serialization in a Workflow Service</span></span>

<span data-ttu-id="78ab6-104">ワークフローサービスは Windows Communication Foundation (WCF) サービスであるため、 <xref:System.Runtime.Serialization.DataContractSerializer> (既定値) またはを使用することも <xref:System.Xml.Serialization.XmlSerializer> できます。</span><span class="sxs-lookup"><span data-stu-id="78ab6-104">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="78ab6-105">ワークフロー以外のサービスを記述する場合、使用するシリアライザーの型はサービスまたは操作コントラクトで指定されます。</span><span class="sxs-lookup"><span data-stu-id="78ab6-105">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="78ab6-106">WCF ワークフローサービスを作成する場合、これらのコントラクトはコードで指定せずに、コントラクト推論によって実行時に生成されます。</span><span class="sxs-lookup"><span data-stu-id="78ab6-106">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="78ab6-107">コントラクト推論の詳細については、「  [ワークフローでのコントラクトの使用](using-contracts-in-workflow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ab6-107">For more information about contract inference, see  [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="78ab6-108">シリアライザーは、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> プロパティを使用して指定されます。</span><span class="sxs-lookup"><span data-stu-id="78ab6-108">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="78ab6-109">これは、次の図に示すようにデザイナーで設定できます。</span><span class="sxs-lookup"><span data-stu-id="78ab6-109">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![[プロパティ] ウィンドウで SerializerOption プロパティを設定します。](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="78ab6-111">シリアライザーは、次の例に示すようにコードで設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="78ab6-111">The serializer can also be set in code as shown in the following example,</span></span>  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
  <span data-ttu-id="78ab6-112">ワークフロー サービスにも既知の型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="78ab6-112">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="78ab6-113">既知の型の詳細については、「 [データコントラクトの既知の型](data-contract-known-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ab6-113">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="78ab6-114">既知の型は、デザイナーまたはコードで指定できます。</span><span class="sxs-lookup"><span data-stu-id="78ab6-114">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="78ab6-115">デザイナーで既知の型を指定するには、次の図に示すように、アクティビティの [ **プロパティ] ウィンドウ** で knowntypes プロパティの横にある省略記号ボタンをクリックし <xref:System.ServiceModel.Activities.Receive> ます。</span><span class="sxs-lookup"><span data-stu-id="78ab6-115">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![KnownTypes プロパティダイアログボックスのスクリーンショット。](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="78ab6-117">これにより、既知の型を検索して指定するための型コレクションエディターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="78ab6-117">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![型コレクションエディターのスクリーンショット。](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="78ab6-119">[ **新しい型の追加** ] リンクをクリックし、ドロップダウンを使用して、既知の型のコレクションに追加する型を選択または検索します。</span><span class="sxs-lookup"><span data-stu-id="78ab6-119">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="78ab6-120">既知の型をコードで指定するには、次の例に示すように <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="78ab6-120">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
```csharp
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```
