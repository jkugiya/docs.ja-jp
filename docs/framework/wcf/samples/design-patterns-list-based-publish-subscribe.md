---
description: '詳細については、「デザインパターン: List-Based Publish-Subscribe」を参照してください。'
title: デザイン パターン:リストに基づく公開/定期受信
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: b615da2afa4e6452b62eacae2cc6b61e4c4363dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726742"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="7e4da-103">デザイン パターン:リストに基づく公開/定期受信</span><span class="sxs-lookup"><span data-stu-id="7e4da-103">Design Patterns: List-Based Publish-Subscribe</span></span>

<span data-ttu-id="7e4da-104">このサンプルは、Windows Communication Foundation (WCF) プログラムとして実装されているリストベースの Publish-Subscribe パターンを示しています。</span><span class="sxs-lookup"><span data-stu-id="7e4da-104">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e4da-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e4da-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7e4da-106">リストベースの Publish-Subscribe 設計パターンについては、Microsoft のパターン & プラクティスの発行、 [統合パターン](/previous-versions/msp-n-p/ff647309(v=pandp.10))に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e4da-106">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="7e4da-107">公開/定期受信パターンは、情報トピックを定期受信する受信者のコレクションに情報を渡します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-107">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="7e4da-108">リストに基づく公開/定期受信では、サブスクライバのリストが保持されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-108">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="7e4da-109">共有情報が存在する場合は、コピーがリスト上の各サブスクライバに送信されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-109">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="7e4da-110">このサンプルでは、動的なリストに基づく公開/定期受信パターンを示します。これにより、クライアントは必要に応じて何度でも定期受信または定期受信の解除ができます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-110">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="7e4da-111">リストに基づく公開/定期受信のサンプルは、クライアント、サービス、およびデータ ソース プログラムで構成されています。</span><span class="sxs-lookup"><span data-stu-id="7e4da-111">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="7e4da-112">クライアントとデータ ソース プログラムは、複数を実行できます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-112">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="7e4da-113">クライアントはサービスを定期受信し、通知を受信して、定期受信を解除します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-113">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="7e4da-114">データ ソース プログラムはサービスに情報を送信し、現在のすべてのサブスクライバでその情報が共有されるようにします。</span><span class="sxs-lookup"><span data-stu-id="7e4da-114">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="7e4da-115">このサンプルでは、クライアントとデータ ソースはコンソール プログラム (.exe ファイル) で、サービスはインターネット インフォメーション サービス (IIS) でホストされるライブラリ (.dll) です。</span><span class="sxs-lookup"><span data-stu-id="7e4da-115">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="7e4da-116">クライアントとデータ ソースのアクティビティは、デスクトップに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-116">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="7e4da-117">サービスは、双方向通信を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-117">The service uses duplex communication.</span></span> <span data-ttu-id="7e4da-118">`ISampleContract` サービス コントラクトは `ISampleClientCallback` コールバック コントラクトと対になっています。</span><span class="sxs-lookup"><span data-stu-id="7e4da-118">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="7e4da-119">サービスは Subscribe および Unsubscribe サービス操作を実装します。クライアントはこれらのサービス操作を使用してサブスクライバのリストに参加またはリストへの参加を解除します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-119">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="7e4da-120">サービスは、さらに `PublishPriceChange` サービス操作も実装します。データ ソース プログラムはこれを呼び出して、新しい情報をサービスに提供します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-120">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="7e4da-121">クライアント プログラムは `PriceChange` サービス操作を実装します。サービスはこれを呼び出して、すべてのサブスクライバに価格の変更を通知します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-121">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```csharp  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 <span data-ttu-id="7e4da-122">サービスは、すべてのサブスクライバに新しい情報を通知する機構として、.NET Framework イベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-122">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="7e4da-123">クライアントが Subscribe を呼び出してサービスに参加すると、イベント ハンドラが提供されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-123">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="7e4da-124">クライアントがサービスへの参加を解除すると、イベントからイベント ハンドラの定期受信が解除されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-124">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="7e4da-125">データ ソースが価格の変更を報告するサービスを呼び出すと、サービスはイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-125">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="7e4da-126">これにより、サービスの各インスタンスが呼び出されます。このサービスは定期受信した各クライアントのサービスで、この呼び出しによって各インスタンスのイベント ハンドラが実行されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-126">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="7e4da-127">各イベント ハンドラは、コールバック関数を使用してクライアントに情報を渡します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-127">Each event handler passes the information to its client through its callback function.</span></span>  
  
```csharp
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 <span data-ttu-id="7e4da-128">このサンプルを実行すると、複数のクライアントが起動されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-128">When you run the sample, launch several clients.</span></span> <span data-ttu-id="7e4da-129">クライアントはサービスを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-129">The clients subscribe to the service.</span></span> <span data-ttu-id="7e4da-130">次にデータ ソース プログラムが実行され、サービスに情報が送信されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-130">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="7e4da-131">サービスは、すべてのサブスクライバに情報を渡します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-131">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="7e4da-132">各クライアント コンソールでアクティビティを表示し、情報が受信されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-132">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="7e4da-133">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-133">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="7e4da-134">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="7e4da-134">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="7e4da-135">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7e4da-136">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7e4da-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="7e4da-137">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="7e4da-137">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="7e4da-138">次のアドレスを入力して、ブラウザーを使用してサービスにアクセスできることをテストします。 `http://localhost/servicemodelsamples/service.svc`</span><span class="sxs-lookup"><span data-stu-id="7e4da-138">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="7e4da-139">これに応答して、確認ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-139">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="7e4da-140">\\言語固有のフォルダーの下から、\ client\bin から Client.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-140">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="7e4da-141">クライアント アクティビティがクライアント コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-141">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="7e4da-142">複数のクライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-142">Launch several clients.</span></span>  
  
3. <span data-ttu-id="7e4da-143">/Datasource\bin から \\ 、言語固有のフォルダーの下から Datasource.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-143">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="7e4da-144">データ ソース アクティビティがコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-144">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="7e4da-145">データ ソースがサービスに情報を送信すると、その情報は各クライアントに渡されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-145">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="7e4da-146">クライアント、データソース、およびサービスプログラムが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e4da-146">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="7e4da-147">サンプルを複数コンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="7e4da-147">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="7e4da-148">サービス コンピュータを設定します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-148">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="7e4da-149">サービス コンピューターで、ServiceModelSamples という仮想ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-149">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="7e4da-150">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)のバッチファイル Setupvroot.bat、ディスクディレクトリと仮想ディレクトリを作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-150">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="7e4da-151">サービス プログラム ファイルを %SystemDrive%\Inetpub\wwwroot\servicemodelsamples からサービス コンピューターの ServiceModelSamples 仮想ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7e4da-151">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="7e4da-152">\bin ディレクトリのファイルが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7e4da-152">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="7e4da-153">ブラウザーを使用して、サービスにクライアント コンピューターからアクセスできるかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="7e4da-153">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="7e4da-154">クライアント コンピュータを設定します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-154">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="7e4da-155">クライアント プログラム ファイルを、言語固有のフォルダにある \client\bin\ フォルダーからクライアント コンピュータにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7e4da-155">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="7e4da-156">各クライアントの構成ファイルで、エンドポイント定義のアドレス値をサービスの新しいアドレスに合わせて変更します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-156">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="7e4da-157">アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-157">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="7e4da-158">データ ソース コンピュータを設定します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-158">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="7e4da-159">データ ソース プログラム ファイルを、言語固有のフォルダーにある \datasource\bin\ フォルダーからデータ ソース コンピュータにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7e4da-159">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="7e4da-160">データ ソースの構成ファイルで、エンドポイント定義のアドレス値をサービスの新しいアドレスに合わせて変更します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-160">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="7e4da-161">アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-161">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="7e4da-162">クライアント コンピュータで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-162">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="7e4da-163">データ ソース コンピューターで、コマンド プロンプトから Datasource.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="7e4da-163">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7e4da-164">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e4da-164">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7e4da-165">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7e4da-165">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7e4da-166">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="7e4da-166">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7e4da-167">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7e4da-167">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`
