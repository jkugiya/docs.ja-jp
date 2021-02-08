---
description: '詳細については、「方法: WCF Web HTTP プログラミングモデルを使用して任意のデータを返すサービスを作成する」を参照してください。'
title: '方法: WCF Web HTTP プログラミング モデルを使用して任意のデータを返すサービスを作成する'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: aeb03e0dad6c63c463db419027f5556922b2f160
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793533"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="52c4e-103">方法: WCF Web HTTP プログラミング モデルを使用して任意のデータを返すサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="52c4e-103">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>

<span data-ttu-id="52c4e-104">開発者は、データがサービス操作から返される流れを完全に制御する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="52c4e-104">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="52c4e-105">これは、サービス操作が WCF でサポートされていない形式でデータを返す必要がある場合に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="52c4e-105">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="52c4e-106">このトピックでは、WCF WEB HTTP プログラミングモデルを使用してこのようなサービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="52c4e-106">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="52c4e-107">ストリームを返す操作を 1 つ持つサービスを例に取ります。</span><span class="sxs-lookup"><span data-stu-id="52c4e-107">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="52c4e-108">サービス コントラクトを実装するには</span><span class="sxs-lookup"><span data-stu-id="52c4e-108">To implement the service contract</span></span>  
  
1. <span data-ttu-id="52c4e-109">サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="52c4e-109">Define the service contract.</span></span> <span data-ttu-id="52c4e-110">コントラクトは `IImageServer` と呼ばれ、`GetImage` を返す <xref:System.IO.Stream> というメソッドが入っています。</span><span class="sxs-lookup"><span data-stu-id="52c4e-110">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="52c4e-111">メソッドはを返すため <xref:System.IO.Stream> 、WCF は、操作がサービス操作から返されたバイトを完全に制御し、返されるデータに書式設定を適用しないことを前提としています。</span><span class="sxs-lookup"><span data-stu-id="52c4e-111">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="52c4e-112">サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="52c4e-112">Implement the service contract.</span></span> <span data-ttu-id="52c4e-113">コントラクトには 1 つの操作 (`GetImage`) しかありません。</span><span class="sxs-lookup"><span data-stu-id="52c4e-113">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="52c4e-114">このメソッドはビットマップを生成して、それを <xref:System.IO.MemoryStream> に .jpg 形式で保存します。</span><span class="sxs-lookup"><span data-stu-id="52c4e-114">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="52c4e-115">操作はそのストリームを呼び出し元に戻します。</span><span class="sxs-lookup"><span data-stu-id="52c4e-115">The operation then returns that stream to the caller.</span></span>  
  
    ```csharp
    public class Service : IImageServer
    {
        public Stream GetImage(int width, int height)
        {
            Bitmap bitmap = new Bitmap(width, height);
            for (int i = 0; i < bitmap.Width; i++)
            {
                for (int j = 0; j < bitmap.Height; j++)
                {
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);
                }
            }
            MemoryStream ms = new MemoryStream();
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);
            ms.Position = 0;
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";
            return ms;
        }
    }
    ```  
  
     <span data-ttu-id="52c4e-116">コードの最後から 2 番目の行にある `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";` に注意してください。</span><span class="sxs-lookup"><span data-stu-id="52c4e-116">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="52c4e-117">これにより、コンテンツの種類のヘッダーがに設定され `"image/jpeg"` ます。</span><span class="sxs-lookup"><span data-stu-id="52c4e-117">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="52c4e-118">この例では .jpg ファイルを戻す方法を示していますが、必要に応じて、任意の種類のデータを任意の形式で戻すように変更できます。</span><span class="sxs-lookup"><span data-stu-id="52c4e-118">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="52c4e-119">操作はデータを生成または取得してそれをストリームに書き込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="52c4e-119">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="52c4e-120">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="52c4e-120">To host the service</span></span>  
  
1. <span data-ttu-id="52c4e-121">コンソール アプリケーションを作成し、サービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="52c4e-121">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. <span data-ttu-id="52c4e-122">変数を作成し、`Main` メソッド内のサービスに使用するベース アドレスを保持します。</span><span class="sxs-lookup"><span data-stu-id="52c4e-122">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="52c4e-123">サービス クラスとベース アドレスを指定するサービスの <xref:System.ServiceModel.ServiceHost> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="52c4e-123">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="52c4e-124"><xref:System.ServiceModel.WebHttpBinding> と <xref:System.ServiceModel.Description.WebHttpBehavior> を使用して、エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="52c4e-124">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="52c4e-125">サービス ホストを開きます。</span><span class="sxs-lookup"><span data-stu-id="52c4e-125">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="52c4e-126">サービスを終了するためにユーザーが Enter キーを押すのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="52c4e-126">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="52c4e-127">Internet Explorer を使用して生のサービスを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="52c4e-127">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="52c4e-128">サービスを実行します。サービスからの次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="52c4e-128">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="52c4e-129">Internet Explorer を開き「`http://localhost:8000/Service/GetImage?width=50&height=40`」と入力します。黄色い長方形とその中心を通る青い斜線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="52c4e-129">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52c4e-130">例</span><span class="sxs-lookup"><span data-stu-id="52c4e-130">Example</span></span>  

 <span data-ttu-id="52c4e-131">この例で使用されているコードの全容を次に示します。</span><span class="sxs-lookup"><span data-stu-id="52c4e-131">The following is a complete listing of the code for this topic.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="52c4e-132">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="52c4e-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="52c4e-133">コード例のコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll を参照します。</span><span class="sxs-lookup"><span data-stu-id="52c4e-133">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c4e-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="52c4e-134">See also</span></span>

- [<span data-ttu-id="52c4e-135">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="52c4e-135">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
