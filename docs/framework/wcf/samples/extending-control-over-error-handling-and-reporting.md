---
description: '詳細情報: エラー処理およびレポートに対する制御の拡張'
title: エラー処理およびレポートに対する制御の拡張
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 9b9dd7761757235b2381fce575021aca2be404f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752380"
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="c5a99-103">エラー処理およびレポートに対する制御の拡張</span><span class="sxs-lookup"><span data-stu-id="c5a99-103">Extending Control Over Error Handling and Reporting</span></span>

<span data-ttu-id="c5a99-104">このサンプルでは、インターフェイスを使用して、Windows Communication Foundation (WCF) サービスのエラー処理およびエラー報告に対する制御を拡張する方法を示し <xref:System.ServiceModel.Dispatcher.IErrorHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-104">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="c5a99-105">このサンプルは、エラーを処理するためにサービスに追加のコードが追加された [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="c5a99-105">The sample is based on the [Getting Started](getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="c5a99-106">クライアントは、強制的にエラーが発生する状態にされます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-106">The client forces several error conditions.</span></span> <span data-ttu-id="c5a99-107">サービスはエラーを途中受信して、ファイルに記録します。</span><span class="sxs-lookup"><span data-stu-id="c5a99-107">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5a99-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5a99-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c5a99-109">サービスは <xref:System.ServiceModel.Dispatcher.IErrorHandler> インターフェイスを使用して、エラーを途中受信して処理を実行し、エラーを報告する方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-109">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="c5a99-110">このインターフェイスには、<xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> と <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> の 2 つのメソッドを実装できます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-110">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="c5a99-111"><xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> メソッドを使用すると、例外に対して生成されるエラー メッセージを追加または変更したり、非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="c5a99-112"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> メソッドを使用すると、エラーの発生時にエラー処理を実行することができます。またこのメソッドは追加のエラー処理を実行するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="c5a99-112">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="c5a99-113">このサンプルでは、`CalculatorErrorHandler` 型は <xref:System.ServiceModel.Dispatcher.IErrorHandler> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="c5a99-113">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="c5a99-114">の</span><span class="sxs-lookup"><span data-stu-id="c5a99-114">In the</span></span>  
  
 <span data-ttu-id="c5a99-115"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> メソッドでは、`CalculatorErrorHandler` がエラーのログを c:\logs の Error.txt テキスト ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-115"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="c5a99-116">このサンプルではエラーを記録して表示します。このエラーの報告は、クライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-116">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
```csharp
public class CalculatorErrorHandler : IErrorHandler
{
    // Provide a fault. The Message fault parameter can be replaced, or set to
    // null to suppress reporting a fault.

    public void ProvideFault(Exception error, MessageVersion version, ref Message fault)
    {
    }

    // HandleError. Log an error, then allow the error to be handled as usual.
    // Return true if the error is considered as already handled

    public bool HandleError(Exception error)
    {
        using (TextWriter tw = File.AppendText(@"c:\logs\error.txt"))
        {
            if (error != null)
            {
                tw.WriteLine("Exception: " + error.GetType().Name + " - " + error.Message);
            }
            tw.Close();
        }
        return true;
    }
}  
```  
  
 <span data-ttu-id="c5a99-117">`ErrorBehaviorAttribute` は、エラー ハンドラをサービスに登録する機構として存在します。</span><span class="sxs-lookup"><span data-stu-id="c5a99-117">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="c5a99-118">この属性は、単一の型のパラメータを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c5a99-118">This attribute takes a single type parameter.</span></span> <span data-ttu-id="c5a99-119">この型は <xref:System.ServiceModel.Dispatcher.IErrorHandler> インターフェイスを実装し、空のパブリック コンストラクタを含む必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5a99-119">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="c5a99-120">この属性は、そのエラー ハンドラの型のインスタンスをインスタンス化し、サービスにインストールします。</span><span class="sxs-lookup"><span data-stu-id="c5a99-120">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="c5a99-121">これを行うには <xref:System.ServiceModel.Description.IServiceBehavior> インターフェイスを実装し、次に <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> メソッドを使用してエラー ハンドラのインスタンスをサービスに追加します。</span><span class="sxs-lookup"><span data-stu-id="c5a99-121">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
```csharp
// This attribute can be used to install a custom error handler for a service.  
public class ErrorBehaviorAttribute : Attribute, IServiceBehavior  
{  
    Type errorHandlerType;  
  
    public ErrorBehaviorAttribute(Type errorHandlerType)  
    {  
        this.errorHandlerType = errorHandlerType;  
    }  
  
    void IServiceBehavior.Validate(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
    }  
  
    void IServiceBehavior.AddBindingParameters(ServiceDescription description, ServiceHostBase serviceHostBase, System.Collections.ObjectModel.Collection<ServiceEndpoint> endpoints, BindingParameterCollection parameters)  
    {  
    }  
  
    void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
        IErrorHandler errorHandler;  
  
        try  
        {  
            errorHandler = (IErrorHandler)Activator.CreateInstance(errorHandlerType);  
        }  
        catch (MissingMethodException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must have a public empty constructor.", e);  
        }  
        catch (InvalidCastException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must implement System.ServiceModel.Dispatcher.IErrorHandler.", e);  
        }  
  
        foreach (ChannelDispatcherBase channelDispatcherBase in serviceHostBase.ChannelDispatchers)  
        {  
            ChannelDispatcher channelDispatcher = channelDispatcherBase as ChannelDispatcher;  
            channelDispatcher.ErrorHandlers.Add(errorHandler);  
        }
    }  
}  
```  
  
 <span data-ttu-id="c5a99-122">このサンプルは、電卓サービスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="c5a99-122">The sample implements a calculator service.</span></span> <span data-ttu-id="c5a99-123">クライアントは、パラメータに無効な値を渡すことによって、サービスで意図的に 2 つのエラーを発生させます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-123">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="c5a99-124">`CalculatorErrorHandler` は <xref:System.ServiceModel.Dispatcher.IErrorHandler> インターフェイスを使用して、エラーをローカル ファイルに記録します。エラーの記録はその後、クライアントに報告されます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-124">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="c5a99-125">クライアントは強制的に 0 による除算を行い、引数を範囲外の状態にします。</span><span class="sxs-lookup"><span data-stu-id="c5a99-125">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
```csharp
try
{  
    Console.WriteLine("Forcing an error in Divide");  
    // Call the Divide service operation - trigger a divide by 0 error.  
    value1 = 22;  
    value2 = 0;  
    result = proxy.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
}  
catch (FaultException e)  
{  
    Console.WriteLine("FaultException: " + e.GetType().Name + " - " + e.Message);  
}  
catch (Exception e)  
{  
    Console.WriteLine("Exception: " + e.GetType().Name + " - " + e.Message);  
}  
```  
  
 <span data-ttu-id="c5a99-126">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-126">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c5a99-127">0 による除算が行われたことと引数が範囲外の状態であることが、エラーとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-127">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="c5a99-128">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c5a99-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="c5a99-129">ファイル c:\logs\errors.txt には、サービスによって記録されたエラーに関する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-129">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="c5a99-130">サービスがディレクトリに書き込むには、サービスを実行しているプロセス (通常は ASP.NET または Network Service) にディレクトリへの書き込みアクセス許可があることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5a99-130">Note that for the service to write to the directory you must make sure that the process under which the service is running (typically ASP.NET or Network Service) has permission to write to the directory.</span></span>  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c5a99-131">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="c5a99-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c5a99-132">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5a99-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c5a99-133">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c5a99-133">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c5a99-134">error.txt ファイル用に c:\logs ディレクトリを作成したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5a99-134">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="c5a99-135">または、`CalculatorErrorHandler.HandleError` で使用されるファイル名を変更します。</span><span class="sxs-lookup"><span data-stu-id="c5a99-135">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4. <span data-ttu-id="c5a99-136">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c5a99-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c5a99-137">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5a99-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c5a99-138">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c5a99-138">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c5a99-139">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="c5a99-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c5a99-140">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5a99-140">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
