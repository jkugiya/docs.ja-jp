---
description: 詳細については、「COM クライアントでの WCF モニカーの使用」を参照してください。
title: WCF モニカーの COM クライアントと組み合わせての使用
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: c2888224e36a473773ef6d7fbd72dbae7420fab0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755760"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="04f5d-103">WCF モニカーの COM クライアントと組み合わせての使用</span><span class="sxs-lookup"><span data-stu-id="04f5d-103">Using the WCF Moniker with COM Clients</span></span>

<span data-ttu-id="04f5d-104">このサンプルでは、Windows Communication Foundation (WCF) サービスモニカーを使用して、Microsoft Office Visual Basic for Applications (Office VBA) や Visual Basic 6.0 などの COM ベースの開発環境に Web サービスを統合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-104">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="04f5d-105">このサンプルは、Windows スクリプト ホストのクライアント (.vbs)、サポート クライアント ライブラリ (.dll)、およびインターネット インフォメーション サービス (IIS) でホストされるサービス ライブラリ (.dll) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="04f5d-105">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="04f5d-106">このサービスは電卓サービスの 1 つであり、COM クライアントはサービスの算術演算 (Add、Subtract、Multiply、および Divide) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-106">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="04f5d-107">クライアント アクティビティは、メッセージ ボックス ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-107">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04f5d-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04f5d-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="04f5d-109">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="04f5d-110">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="04f5d-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="04f5d-111">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="04f5d-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="04f5d-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="04f5d-113">サービスは、次に示すコード例で定義される `ICalculator` コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-113">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="04f5d-114">このサンプルでは、モニカーを使用するための次の 3 つの代替方法を示します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-114">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="04f5d-115">型指定のあるコントラクト - クライアント コンピューターで COM から参照できる型として登録されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-115">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="04f5d-116">WSDL コントラクト - WSDL ドキュメントという形で供給されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-116">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="04f5d-117">Metadata Exchange コントラクト – 実行時に Metadata Exchange (MEX) エンドポイントから取得されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-117">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="04f5d-118">型指定のあるコントラクト</span><span class="sxs-lookup"><span data-stu-id="04f5d-118">Typed Contract</span></span>  

 <span data-ttu-id="04f5d-119">型指定のあるコントラクトと共にモニカーを使用するには、属性が適切に設定されているサービス コントラクトの型を COM に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-119">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="04f5d-120">まず、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用してクライアントを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-120">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="04f5d-121">次のコマンドをクライアント ディレクトリでコマンド プロンプトから実行して、型指定のあるプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-121">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="04f5d-122">このクラスはプロジェクトに含まれている必要があり、そのプロジェクトは、COM から参照できる署名付きのアセンブリをコンパイル時に生成するように構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-122">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="04f5d-123">AssemblyInfo.cs ファイルには次の属性を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-123">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="04f5d-124">プロジェクトをビルドしたら、次の例で示すように `regasm` を使用して、COM から参照できる型を登録します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-124">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="04f5d-125">作成されたアセンブリは、グローバル アセンブリ キャッシュに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-125">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="04f5d-126">必要性は強くありませんが、これによってアセンブリを検索するランタイムのプロセスが簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-126">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="04f5d-127">グローバル アセンブリ キャッシュにアセンブリを追加するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-127">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="04f5d-128">サービス モニカーで必要なのは型の登録だけであり、サービスと通信するためのプロキシは使用されません。</span><span class="sxs-lookup"><span data-stu-id="04f5d-128">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="04f5d-129">ComCalcClient.vbs クライアント アプリケーションは、サービス モニカーの構文を使用してサービスのアドレス、バインディング、およびコントラクトを指定し、`GetObject` 関数を使用してサービスのプロキシを構築します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-129">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="04f5d-130">モニカーが使用するパラメーターでの指定: </span><span class="sxs-lookup"><span data-stu-id="04f5d-130">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="04f5d-131">サービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="04f5d-131">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="04f5d-132">エンドポイントとの接続にクライアントが使用する必要のあるバインディング。</span><span class="sxs-lookup"><span data-stu-id="04f5d-132">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="04f5d-133">クライアントの構成ファイルにはカスタム バインドを定義できますが、この場合はシステム定義の wsHttpBinding を使用します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-133">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="04f5d-134">Windows スクリプト ホストで使用する場合、カスタム バインディングは、Cscript.exe と同じディレクトリにある Cscript.exe.config で定義されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-134">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="04f5d-135">エンドポイントでサポートされるコントラクトの型。</span><span class="sxs-lookup"><span data-stu-id="04f5d-135">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="04f5d-136">これは上の手順で生成され、登録された型です。</span><span class="sxs-lookup"><span data-stu-id="04f5d-136">This is the type that was generated and registered above.</span></span> <span data-ttu-id="04f5d-137">Visual Basic スクリプトには厳密に型指定された COM 環境が用意されていないため、コントラクトの識別子を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-137">Because Visual Basic script does not provide a strongly typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="04f5d-138">この GUID は CalcProxy.tlb からの `interfaceID` で、OLE/COM オブジェクト ビューアー (OleView.exe) などの COM ツールを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-138">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="04f5d-139">Office VBA や Visual Basic 6.0 などの厳密に型指定された環境では、タイプライブラリへの明示的な参照を追加してから、プロキシオブジェクトの型を宣言して、コントラクトパラメーターの代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-139">For strongly typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="04f5d-140">これにより、クライアント アプリケーションの開発中に IntelliSense のサポートも提供されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-140">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="04f5d-141">サービス モニカーを使用してプロキシ インスタンスを構築しておくと、クライアント アプリケーションはプロキシでメソッドを呼び出すことができます。これにより、対応するサービス操作を呼び出すサービス モニカー インフラストラクチャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-141">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 サンプルを実行すると、操作の応答が Windows スクリプト ホストのメッセージ ボックス ウィンドウに表示されます。 これは、型指定されたモニカーを使用して COM 呼び出しを行い、WCF サービスと通信する COM クライアントを示しています。 <span data-ttu-id="04f5d-144">クライアント アプリケーションでは COM が使用されますが、サービスとの通信は Web サービス呼び出しのみで構成されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-144">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="04f5d-145">WSDL コントラクト</span><span class="sxs-lookup"><span data-stu-id="04f5d-145">WSDL Contract</span></span>  

 <span data-ttu-id="04f5d-146">WSDL コントラクトと共にモニカーを使用するには、クライアント ライブラリを登録する必要はありません。ただし、ブラウサを使用してサービスの WSDL エンドポイントにアクセスするなど、帯域外機構を通じてサービスの WSDL コントラクトを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-146">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="04f5d-147">これにより、モニカーは実行時にそのコントラクトにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-147">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="04f5d-148">ComCalcClient.vbs クライアント アプリケーションは、次のように `FileSystemObject` を使用してローカルに保存されている WSDL ファイルにアクセスし、その後 `GetObject` 関数を再度使用してサービスのプロキシを構築します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-148">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 <span data-ttu-id="04f5d-149">モニカーが使用するパラメーターでの指定: </span><span class="sxs-lookup"><span data-stu-id="04f5d-149">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="04f5d-150">サービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="04f5d-150">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="04f5d-151">そのエンドポイントと接続するためにクライアントが使用する必要があるバインディングと、そのバインディングが定義されている名前空間。</span><span class="sxs-lookup"><span data-stu-id="04f5d-151">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="04f5d-152">この場合、`wsHttpBinding_ICalculator` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-152">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="04f5d-153">コントラクトを定義する WSDL。</span><span class="sxs-lookup"><span data-stu-id="04f5d-153">The WSDL that defines the contract.</span></span> <span data-ttu-id="04f5d-154">この場合は、サービスの Wsdl.xml ファイルから読み取られた文字列です。</span><span class="sxs-lookup"><span data-stu-id="04f5d-154">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="04f5d-155">コントラクトの名前と名前空間。</span><span class="sxs-lookup"><span data-stu-id="04f5d-155">The name and namespace of the contract.</span></span> <span data-ttu-id="04f5d-156">WSDL に複数のコントラクトが含まれている場合があるので、識別情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="04f5d-156">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="04f5d-157">既定では、WCF サービスは、使用する名前空間ごとに個別の WSDL ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-157">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="04f5d-158">これらのファイルは、WSDL インポート コンストラクターを使用してリンクされます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-158">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="04f5d-159">モニカーでは単一の WSDL 定義が想定されているので、サービスはこのサンプルで示すように単一の名前空間を使用するか、または別のファイルを手動でマージする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-159">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="04f5d-160">サービス モニカーを使用してプロキシ インスタンスを構築しておくと、クライアント アプリケーションはプロキシでメソッドを呼び出すことができます。これにより、対応するサービス操作を呼び出すサービス モニカー インフラストラクチャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-160">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 サンプルを実行すると、操作の応答が Windows スクリプト ホストのメッセージ ボックス ウィンドウに表示されます。 <span data-ttu-id="04f5d-162">これは、com クライアントが、モニカーと WSDL コントラクトを使用して WCF サービスと通信する com クライアントを示しています。</span><span class="sxs-lookup"><span data-stu-id="04f5d-162">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="04f5d-163">Metadata Exchange コントラクト</span><span class="sxs-lookup"><span data-stu-id="04f5d-163">Metadata Exchange Contract</span></span>  

 <span data-ttu-id="04f5d-164">MEX コントラクトと共にモニカーを使用するには、WSDL コントラクトと同様、クライアント登録は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="04f5d-164">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="04f5d-165">サービスのコントラクトは、実行時に Metadata Exchange を内部使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-165">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="04f5d-166">ComCalcClient.vbs クライアント アプリケーションは次のように `GetObject` 関数を再度使用して、サービスのプロキシを構築します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-166">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="04f5d-167">モニカーが使用するパラメーターでの指定: </span><span class="sxs-lookup"><span data-stu-id="04f5d-167">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="04f5d-168">サービスの Metadata Exchange エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="04f5d-168">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="04f5d-169">サービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="04f5d-169">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="04f5d-170">そのエンドポイントと接続するためにクライアントが使用する必要があるバインディングと、そのバインディングが定義されている名前空間。</span><span class="sxs-lookup"><span data-stu-id="04f5d-170">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="04f5d-171">この場合、`wsHttpBinding_ICalculator` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-171">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="04f5d-172">コントラクトの名前と名前空間。</span><span class="sxs-lookup"><span data-stu-id="04f5d-172">The name and namespace of the contract.</span></span> <span data-ttu-id="04f5d-173">WSDL に複数のコントラクトが含まれている場合があるので、識別情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="04f5d-173">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="04f5d-174">サービス モニカーを使用してプロキシ インスタンスを構築しておくと、クライアント アプリケーションはプロキシでメソッドを呼び出すことができます。これにより、対応するサービス操作を呼び出すサービス モニカー インフラストラクチャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="04f5d-174">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 サンプルを実行すると、操作の応答が Windows スクリプト ホストのメッセージ ボックス ウィンドウに表示されます。 <span data-ttu-id="04f5d-176">これは、com クライアントが、モニカーを使用して COM 呼び出しを行い、MEX コントラクトを使用して WCF サービスと通信する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="04f5d-176">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="04f5d-177">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="04f5d-177">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="04f5d-178">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-178">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="04f5d-179">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="04f5d-179">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="04f5d-180">Visual Studio の開発者コマンドプロンプトで、言語固有のフォルダーの下にある \ client\bin フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-180">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="04f5d-181">Windows Vista、Windows Server 2008、Windows 7、または Windows Server 2008 R2 を使用している場合は、管理者特権でコマンドプロンプトを実行してください。</span><span class="sxs-lookup"><span data-stu-id="04f5d-181">If you are using Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="04f5d-182">「」と入力 `tlbexp.exe client.dll /out:CalcProxy.tlb` して、dll を tlb ファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="04f5d-182">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="04f5d-183">"タイプ ライブラリ エクスポーターの警告" が表示されることが予想されますが、ジェネリック型は不要なので問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="04f5d-183">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="04f5d-184">型を `regasm.exe /tlb:CalcProxy.tlb client.dll` COM に登録するには、「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-184">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="04f5d-185">"タイプ ライブラリ エクスポーターの警告" が表示されることが予想されますが、ジェネリック型は不要なので問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="04f5d-185">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="04f5d-186">アセンブリを `gacutil.exe /i client.dll` グローバルアセンブリキャッシュに追加するには、「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-186">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="04f5d-187">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="04f5d-187">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="04f5d-188">次のアドレスを入力して、ブラウザーを使用してサービスにアクセスできることをテスト `http://localhost/servicemodelsamples/service.svc` します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-188">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="04f5d-189">これに応答して、確認ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-189">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="04f5d-190">言語固有のフォルダーの下の \client にある ComCalcClient.vbs を実行します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-190">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="04f5d-191">クライアント アクティビティがメッセージ ボックス ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-191">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="04f5d-192">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04f5d-192">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="04f5d-193">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="04f5d-193">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="04f5d-194">サービス コンピューターで、ServiceModelSamples という仮想ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-194">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="04f5d-195">サンプルに含まれている Setupvroot.bat スクリプトを使用して、ディスク ディレクトリと仮想ディレクトリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-195">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="04f5d-196">サービス プログラム ファイルを %SystemDrive%\Inetpub\wwwroot\servicemodelsamples からサービス コンピューターの ServiceModelSamples 仮想ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="04f5d-196">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="04f5d-197">\bin ディレクトリのファイルが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="04f5d-197">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="04f5d-198">クライアント スクリプト ファイルを、言語固有のフォルダーにある \client フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="04f5d-198">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="04f5d-199">このスクリプト ファイルで、エンドポイント定義のアドレス値をサービスの新しいアドレスに変更します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-199">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="04f5d-200">アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-200">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="04f5d-201">WSDL ファイルをクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="04f5d-201">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="04f5d-202">WSDL ファイルのサービスの Wsdl.xml で、アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-202">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="04f5d-203">Client.dll ライブラリを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターのディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="04f5d-203">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="04f5d-204">コマンド プロンプトで、クライアント コンピューターのコピー先ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-204">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="04f5d-205">Windows Vista または Windows Server 2008 を使用している場合は、管理者としてコマンドプロンプトを実行してください。</span><span class="sxs-lookup"><span data-stu-id="04f5d-205">If using Windows Vista or Windows Server 2008, make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="04f5d-206">「」と入力 `tlbexp.exe client.dll /out:CalcProxy.tlb` して、dll を tlb ファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="04f5d-206">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="04f5d-207">"タイプ ライブラリ エクスポーターの警告" が表示されることが予想されますが、ジェネリック型は不要なので問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="04f5d-207">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="04f5d-208">型を `regasm.exe /tlb:CalcProxy.tlb client.dll` COM に登録するには、「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-208">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="04f5d-209">コマンドを実行する前に、パスがに含まれるフォルダーに設定されていることを確認し `regasm.exe` ます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-209">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="04f5d-210">アセンブリを `gacutil.exe /i client.dll` グローバルアセンブリキャッシュに追加するには、「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-210">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="04f5d-211">コマンドを実行する前に、パスがに含まれるフォルダーに設定されていることを確認し `gacutil.exe` ます。</span><span class="sxs-lookup"><span data-stu-id="04f5d-211">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="04f5d-212">ブラウザーを使用して、サービスにクライアント コンピューターからアクセスできるかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="04f5d-212">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="04f5d-213">クライアント コンピューターで ComCalcClient.vbs を起動します。</span><span class="sxs-lookup"><span data-stu-id="04f5d-213">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="04f5d-214">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="04f5d-214">To clean up after the sample</span></span>  
  
- <span data-ttu-id="04f5d-215">セキュリティの目的で、サンプルの使用が終わったら、このセットアップで付与された仮想ディレクトリの定義とアクセス許可を削除してください。</span><span class="sxs-lookup"><span data-stu-id="04f5d-215">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>
