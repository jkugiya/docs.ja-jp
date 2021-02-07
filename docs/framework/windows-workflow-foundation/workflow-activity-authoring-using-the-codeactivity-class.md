---
description: 詳細については、CodeActivity クラスを使用したワークフローアクティビティの作成に関するページを参照してください。
title: CodeActivity クラスを使用したワークフロー アクティビティの作成
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 393b6c586a88e876484f6888441d5bb82b4c0dad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754915"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="359dd-103">CodeActivity クラスを使用したワークフロー アクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="359dd-103">Workflow Activity Authoring Using the CodeActivity Class</span></span>

<span data-ttu-id="359dd-104"><xref:System.Activities.CodeActivity> を継承して作成されたアクティビティは、<xref:System.Activities.CodeActivity.Execute%2A> メソッドをオーバーライドすることで強制的な基本動作を実装できます。</span><span class="sxs-lookup"><span data-stu-id="359dd-104">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

## <a name="using-codeactivitycontext"></a><span data-ttu-id="359dd-105">CodeActivityContext の使用</span><span class="sxs-lookup"><span data-stu-id="359dd-105">Using CodeActivityContext</span></span>

 <span data-ttu-id="359dd-106">ワークフロー ランタイムの機能は、<xref:System.Activities.CodeActivity.Execute%2A> 型の `context` パラメーターを使用して、<xref:System.Activities.CodeActivityContext> メソッド内からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="359dd-106">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="359dd-107"><xref:System.Activities.CodeActivityContext> を介して、以下のような機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="359dd-107">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>

- <span data-ttu-id="359dd-108">変数と引数の値を取得および設定。</span><span class="sxs-lookup"><span data-stu-id="359dd-108">Getting and setting the values of variables and arguments.</span></span>

- <span data-ttu-id="359dd-109"><xref:System.Activities.CodeActivityContext.Track%2A> を使用したカスタムの追跡機能。</span><span class="sxs-lookup"><span data-stu-id="359dd-109">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="359dd-110"><xref:System.Activities.CodeActivityContext.GetProperty%2A> を使用したアクティビティの実行プロパティへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="359dd-110">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="359dd-111">CodeActivity を継承するカスタム アクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="359dd-111">To create a custom activity that inherits from CodeActivity</span></span>

1. <span data-ttu-id="359dd-112">Visual Studio 2010 を開きます。</span><span class="sxs-lookup"><span data-stu-id="359dd-112">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="359dd-113">[ **ファイル**]、[ **新規作成**]、[ **プロジェクト**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="359dd-113">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="359dd-114">[**プロジェクトの種類**] ウィンドウの [ **Visual C#** ] で [**ワークフロー 4.0** ] を選択し、[ **v2010** ] ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="359dd-114">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="359dd-115">[**テンプレート**] ウィンドウで [**アクティビティライブラリ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="359dd-115">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="359dd-116">新しいプロジェクトに HelloActivity という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="359dd-116">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="359dd-117">HelloActivity プロジェクトで Activity1 を右クリックし、[ **削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="359dd-117">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="359dd-118">HelloActivity プロジェクトを右クリックし、[ **追加** ]、[ **クラス**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="359dd-118">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="359dd-119">新しいクラスに HelloActivity.cs という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="359dd-119">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="359dd-120">HelloActivity.cs ファイルで、次の `using` ディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="359dd-120">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="359dd-121">クラス宣言に基本クラスを追加することにより、新しいクラスで <xref:System.Activities.CodeActivity> から継承します。</span><span class="sxs-lookup"><span data-stu-id="359dd-121">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. <span data-ttu-id="359dd-122"><xref:System.Activities.CodeActivity.Execute%2A> メソッドを追加して、このクラスに機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="359dd-122">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="359dd-123"><xref:System.Activities.CodeActivityContext> を使用して追跡レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="359dd-123">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
