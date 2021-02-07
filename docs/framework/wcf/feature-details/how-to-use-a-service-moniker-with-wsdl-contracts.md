---
description: '詳細については、「方法: WSDL コントラクトでサービスモニカーを使用する」を参照してください。'
title: '方法: WSDL コントラクトと共にサービス モニカーを使用する'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 70a8ef0258cd8490d8e14b6a80e8de0248fa0ae2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734374"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="1c0b6-103">方法: WSDL コントラクトと共にサービス モニカーを使用する</span><span class="sxs-lookup"><span data-stu-id="1c0b6-103">How to: Use a Service Moniker with WSDL Contracts</span></span>

<span data-ttu-id="1c0b6-104">完全に自己完結型である COM Interop クライアントの構築が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-104">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="1c0b6-105">呼び出そうとするサービスで MEX エンドポイントが公開されておらず、WCF クライアントの DLL が COM interop に登録されていないこともあります。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-105">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="1c0b6-106">このような場合、サービスを記述した WSDL ファイルを作成し、そのファイルを WCF サービス モニカーに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-106">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="1c0b6-107">ここでは、WCF WSDL モニカーを使用して、WCF の入門サンプルを呼び出す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-107">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="1c0b6-108">WSDL サービス モニカーの使用</span><span class="sxs-lookup"><span data-stu-id="1c0b6-108">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="1c0b6-109">入門サンプル ソリューションを開き、ビルドします。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-109">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="1c0b6-110">Internet Explorer を開き、に移動し `http://localhost/ServiceModelSamples/Service.svc` て、サービスが動作していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-110">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="1c0b6-111">Service.cs ファイルで、次の属性を CalculatorService クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-111">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="1c0b6-112">バインディング名前空間をサービスの App.config に追加します。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-112">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="1c0b6-113">アプリケーションが読み取る WSDL ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-113">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="1c0b6-114">名前空間は手順 3. と 4. で追加されたため、を参照して、IE を使用してサービスの WSDL 記述全体を照会でき `http://localhost/ServiceModelSamples/Service.svc?wsdl` ます。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-114">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="1c0b6-115">次に、そのファイルをサービスの WSDL.xml として Internet Explorer で保存できます。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-115">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="1c0b6-116">手順 3. と 4. で名前空間を指定しなかった場合、上記の URL を照会したときに返される WSDL ドキュメントは、完全な WSDL ではありません。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-116">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="1c0b6-117">返される WSDL ドキュメントには、他の WSDL ドキュメントをインポートするためのインポート ステートメントが追加されています。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-117">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="1c0b6-118">各インポート ステートメントを実行し、サービスから返された WSDL とインポートした WSDL を組み合わせることによって、完全な WSDL ドキュメントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-118">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="1c0b6-119">Visual Basic 6.0 を開き、新しい標準 .exe ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-119">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="1c0b6-120">フォームにボタンを追加し、追加したボタンをダブルクリックして次のコードをクリック ハンドラーに追加します。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-120">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    > モニカーの形式が正しくないか、`GetObject` を呼び出せない場合は、"構文が無効です" というメッセージが返されます。  <span data-ttu-id="1c0b6-122">このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-122">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="1c0b6-123">Visual Basic アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-123">Run the Visual Basic application.</span></span> <span data-ttu-id="1c0b6-124">メッセージ ボックスに、Subtract(145, 76.54) を呼び出した結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c0b6-124">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0b6-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c0b6-125">See also</span></span>

- [<span data-ttu-id="1c0b6-126">はじめに</span><span class="sxs-lookup"><span data-stu-id="1c0b6-126">Getting Started</span></span>](../samples/getting-started-sample.md)
- [<span data-ttu-id="1c0b6-127">COM アプリケーションとの統合の概要</span><span class="sxs-lookup"><span data-stu-id="1c0b6-127">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)
