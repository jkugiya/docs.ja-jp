---
description: '詳細については、「方法: AJAX-Enabled WCF サービスと、サービスにアクセスする ASP.NET クライアントを作成する」を参照してください。'
title: Visual Studio で AJAX-Enabled WCF サービスと ASP.NET クライアントを作成する
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 59b0cab9b28dd68b27529b5d880138cc283144a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780350"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="21ea2-103">方法 : AJAX 対応 WCF サービスとこのサービスにアクセスする ASP.NET クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="21ea2-103">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="21ea2-104">このトピックでは、Visual Studio を使用して、AJAX 対応の Windows Communication Foundation (WCF) サービスと、サービスにアクセスする ASP.NET クライアントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-104">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="21ea2-105">ASP.NET Web アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="21ea2-105">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="21ea2-106">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="21ea2-106">Open Visual Studio.</span></span>

1. <span data-ttu-id="21ea2-107">[**ファイル**] メニューの [**新しい**  >  **プロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21ea2-107">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="21ea2-108">[**新しいプロジェクト**] ダイアログで、[**インストールされている**  >  **Visual C#**  >  **web** ] カテゴリを展開し、[ **ASP.NET Web Application (.NET Framework)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-108">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="21ea2-109">プロジェクトに **SandwichServices** という名前を指定し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21ea2-109">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="21ea2-110">**[新しい ASP.NET Web アプリケーション]** ダイアログで、 **[空]** を選択し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-110">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![ASP.NET Visual Studio の [web アプリの種類] ダイアログボックス](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="21ea2-112">Web フォームを追加する</span><span class="sxs-lookup"><span data-stu-id="21ea2-112">Add a web form</span></span>

1. <span data-ttu-id="21ea2-113">**ソリューションエクスプローラー** で SandwichServices プロジェクトを右クリックし、[   >  **新しい項目** の追加] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-113">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="21ea2-114">[**新しい項目の追加**] ダイアログで、[**インストールされている**  >  **Visual C#**]  >  **web** カテゴリを展開し、[ **web フォーム**] テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-114">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="21ea2-115">既定の名前 (**WebForm1**) をそのまま使用し、[ **追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-115">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="21ea2-116">**ソース** ビューで *WebForm1* が開きます。</span><span class="sxs-lookup"><span data-stu-id="21ea2-116">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="21ea2-117">タグ内に次のマークアップを追加し **\<body>** ます。</span><span class="sxs-lookup"><span data-stu-id="21ea2-117">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="21ea2-118">AJAX 対応 WCF サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="21ea2-118">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="21ea2-119">**ソリューションエクスプローラー** で SandwichServices プロジェクトを右クリックし、[   >  **新しい項目** の追加] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-119">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="21ea2-120">[**新しい項目の追加**] ダイアログで、[**インストールされている**  >  **Visual C#**]  >  **Web** カテゴリを展開し、[ **WCF サービス (AJAX 対応)** ] テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-120">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Visual Studio での WCF サービス (AJAX 対応) 項目テンプレート](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="21ea2-122">サービスにサービスの **名前を指定** し、[ **追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-122">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="21ea2-123">*CostService.svc.cs* がエディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="21ea2-123">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="21ea2-124">サービスに操作を実装します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-124">Implement the operation in the service.</span></span> <span data-ttu-id="21ea2-125">サンドイッチの数量のコストを計算するには、次のメソッドを cost Service クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-125">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="21ea2-126">サービスにアクセスするようにクライアントを構成する</span><span class="sxs-lookup"><span data-stu-id="21ea2-126">Configure the client to access the service</span></span>

1. <span data-ttu-id="21ea2-127">*WebForm1* ファイルを開き、[**デザイン**] ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-127">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="21ea2-128">[ **表示** ] メニューの [ **ツールボックス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21ea2-128">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="21ea2-129">[ **AJAX Extensions** ] ノードを展開し、 **ScriptManager** をフォームにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="21ea2-129">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="21ea2-130">**ソース** ビューに戻り、次のコードをタグの間に追加して、 **\<ScriptManager>** WCF サービスへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-130">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. <span data-ttu-id="21ea2-131">JavaScript 関数のコードを追加 `Calculate()` します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-131">Add the code for the JavaScript function `Calculate()`.</span></span> <span data-ttu-id="21ea2-132">次のコードを web フォームの **head** セクションに配置します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-132">Place the following code in the **head** section of the web form:</span></span>

    ```html
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   <span data-ttu-id="21ea2-133">このコードは、3つのサンドイッチの価格を計算するために、コストサービスのメソッドを呼び出し、 **additionResult** というスパンに結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-133">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="21ea2-134">プログラムの実行</span><span class="sxs-lookup"><span data-stu-id="21ea2-134">Run the program</span></span>

<span data-ttu-id="21ea2-135">*WebForm1* にフォーカスがあることを確認し、[**開始**] ボタンをクリックして web クライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-135">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="21ea2-136">ボタンには緑色の三角形が表示され、 **IIS Express (Microsoft Edge)** のようなものが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21ea2-136">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="21ea2-137">または、 <kbd>F5</kbd>キーを押します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-137">Or, you can press <kbd>F5</kbd>.</span></span> <span data-ttu-id="21ea2-138">[ **Price-3 サンドイッチ** ] ボタンをクリックして、予想される出力 "3.75" を生成します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-138">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example"></a><span data-ttu-id="21ea2-139">例</span><span class="sxs-lookup"><span data-stu-id="21ea2-139">Example</span></span>

<span data-ttu-id="21ea2-140">*CostService.svc.cs* ファイルの完全なコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-140">The following is the full code in the *CostService.svc.cs* file:</span></span>

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

<span data-ttu-id="21ea2-141">次に、 *WebForm1* ページの完全な内容を示します。</span><span class="sxs-lookup"><span data-stu-id="21ea2-141">The following is the full contents of the *WebForm1.aspx* page:</span></span>

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```
