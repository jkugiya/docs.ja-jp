---
description: '詳細については、「方法: 既存のサービスコントラクトを使用するワークフローサービスを作成する」を参照してください。'
title: '方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 0a31f0f4e205c72b857b59726437e896a7c68231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631256"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="c0050-103">方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="c0050-103">How to: Create a workflow service that consumes an existing service contract</span></span>

<span data-ttu-id="c0050-104">.NET Framework 4.5 では、コントラクト優先ワークフロー開発の形式で web サービスとワークフローの統合が強化されています。</span><span class="sxs-lookup"><span data-stu-id="c0050-104">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="c0050-105">コントラクト優先ワークフローの開発ツールでは、コードのコントラクトを先に設計できます。</span><span class="sxs-lookup"><span data-stu-id="c0050-105">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="c0050-106">その後、ツールボックス内に、コントラクト内の操作用のアクティビティ テンプレートが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="c0050-106">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0050-107">このトピックでは、コントラクト優先ワークフロー サービスを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="c0050-107">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="c0050-108">コントラクト優先ワークフローサービスの開発の詳細については、「 [コントラクトの最初のワークフローサービスの開発](contract-first-workflow-service-development.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0050-108">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="c0050-109">ワークフロー プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="c0050-109">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="c0050-110">Visual Studio で、**[ファイル]\*\*\*\*[新しいプロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="c0050-110">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="c0050-111">[**テンプレート**] ツリーで、[ **C#** ] ノードの下にある [ **wcf** ] ノードを選択し、[ **wcf ワークフローサービスアプリケーション**] テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="c0050-111">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="c0050-112">新しいプロジェクトに名前を指定し、 `ContractFirst` [ **Ok]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0050-112">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="c0050-113">サービス コントラクトの作成</span><span class="sxs-lookup"><span data-stu-id="c0050-113">Creating the service contract</span></span>  
  
1. <span data-ttu-id="c0050-114">**ソリューションエクスプローラー** でプロジェクトを右クリックし、[**追加**]、[**新しい項目**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="c0050-114">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="c0050-115">左側の [ **コード** ] ノードを選択し、右側の [ **クラス** ] テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="c0050-115">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="c0050-116">新しいクラスにという名前を指定し、 `IBookService` [ **Ok]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0050-116">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="c0050-117">表示されるコード ウィンドウの上部で、`System.Servicemodel` に対する Using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c0050-117">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="c0050-118">サンプルのクラス定義を次のインターフェイス定義に変更します。</span><span class="sxs-lookup"><span data-stu-id="c0050-118">Change the sample class definition to the following interface definition.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="c0050-119">**Ctrl + Shift + B** キーを押してプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c0050-119">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="c0050-120">サービス コントラクトのインポート</span><span class="sxs-lookup"><span data-stu-id="c0050-120">Importing the service contract</span></span>  
  
1. <span data-ttu-id="c0050-121">**ソリューションエクスプローラー** でプロジェクトを右クリックし、[**サービスコントラクトのインポート**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c0050-121">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="c0050-122">で **\<Current Project>** 、すべてのサブノードを開き、[ **Ibookservice**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c0050-122">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="c0050-123">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0050-123">Click **OK**.</span></span>  
  
2. <span data-ttu-id="c0050-124">ダイアログが表示され、操作が正常に完了したことと、プロジェクトをビルドすると、生成されたアクティビティがツールボックスに表示されることが示されます。</span><span class="sxs-lookup"><span data-stu-id="c0050-124">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="c0050-125">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0050-125">Click **OK**.</span></span>  
  
3. <span data-ttu-id="c0050-126">**Ctrl + Shift + B** キーを押してプロジェクトをビルドし、インポートされたアクティビティがツールボックスに表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="c0050-126">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="c0050-127">**ソリューションエクスプローラー** で、Service1 .xamlx を開きます。</span><span class="sxs-lookup"><span data-stu-id="c0050-127">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="c0050-128">ワークフロー サービスがデザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c0050-128">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="c0050-129">**Sequence** アクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="c0050-129">Select the **Sequence** activity.</span></span> <span data-ttu-id="c0050-130">[プロパティウィンドウで、[.. **.** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0050-130">In the Properties window, click the **…**</span></span> <span data-ttu-id="c0050-131">**ImplementedContract** プロパティのボタン。</span><span class="sxs-lookup"><span data-stu-id="c0050-131">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="c0050-132">[**型コレクションエディター** ] ウィンドウが表示されたら、[**種類**] ドロップダウンをクリックし、[**種類の参照**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c0050-132">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="c0050-133">] エントリを探してクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0050-133">entry.</span></span> <span data-ttu-id="c0050-134">[ **.Net 型の参照と選択** ] ダイアログボックスの [] で、 **\<Current Project>** すべてのサブノードを開き、[ **ibookservice**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c0050-134">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="c0050-135">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0050-135">Click **OK**.</span></span> <span data-ttu-id="c0050-136">[ **型コレクションエディター** ] ダイアログボックスで、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0050-136">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="c0050-137">**Receiverequest アクティビティ** アクティビティと **sendresponse** アクティビティを選択して削除します。</span><span class="sxs-lookup"><span data-stu-id="c0050-137">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="c0050-138">[ツールボックス] から、[ **Buy_ReceiveAndSendReply** と **Checkout_Receive** ] アクティビティを [ **シーケンシャルサービス** ] アクティビティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c0050-138">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
