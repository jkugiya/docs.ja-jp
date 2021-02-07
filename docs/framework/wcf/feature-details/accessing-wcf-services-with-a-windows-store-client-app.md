---
description: '詳細情報: Windows ストアクライアントアプリを使用した WCF サービスへのアクセス'
title: Windows ストア クライアント アプリを使用した WCF サービスへのアクセス
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: 6586b07e72749b0c136072474c27c264568ed3f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705409"
---
# <a name="access-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="ff6e0-103">Windows ストアクライアントアプリを使用して WCF サービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="ff6e0-103">Access WCF Services with a Windows Store Client App</span></span>

<span data-ttu-id="ff6e0-104">Windows 8 では、Windows ストア アプリケーションと呼ばれる新しい種類のアプリケーションが導入されています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-104">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="ff6e0-105">これらのアプリケーションはタッチ スクリーンのインターフェイスを念頭にデザインされています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-105">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="ff6e0-106">.NET Framework 4.5 により、Windows ストア アプリケーションから WCF サービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-106">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="ff6e0-107">Windows ストア アプリケーションでの WCF のサポート</span><span class="sxs-lookup"><span data-stu-id="ff6e0-107">WCF Support in Windows Store Applications</span></span>  

 <span data-ttu-id="ff6e0-108">WCF 機能の一部は、Windows ストア アプリケーション内から利用できます。詳細については、以降のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-108">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ff6e0-109">WCF で公開される API ではなく、WinRT 配信 API を使用してください。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-109">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="ff6e0-110">詳細については、「 [Windows.Web.Syndication 名前空間](xref:Windows.Web.Syndication)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-110">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ff6e0-111">Windows ランタイムコンポーネントに web サービス参照を追加するためのサービス参照の追加の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-111">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn't supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="ff6e0-112">サポートされているバインド</span><span class="sxs-lookup"><span data-stu-id="ff6e0-112">Supported Bindings</span></span>  

 <span data-ttu-id="ff6e0-113">Windows ストア アプリケーションでは、以下の WCF バインドがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-113">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="ff6e0-114">Windows ストア アプリケーションでは、以下のバインド要素がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-114">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="ff6e0-115">テキスト エンコードとバイナリ エンコードの両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-115">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="ff6e0-116">すべての WCF 転送モードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-116">All WCF transfer modes are supported.</span></span> <span data-ttu-id="ff6e0-117">詳細については、「 [Streaming Message Transfer](streaming-message-transfer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-117">For more information see, [Streaming Message Transfer](streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="ff6e0-118">サービス参照の追加</span><span class="sxs-lookup"><span data-stu-id="ff6e0-118">Add Service Reference</span></span>  

 <span data-ttu-id="ff6e0-119">WCF サービスを Windows ストア アプリケーションから呼び出すには、Visual Studio 2012 の "サービス参照の追加" 機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-119">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="ff6e0-120">Windows ストア アプリケーションでは、"サービス参照の追加" 機能にいくつかの変更が行われていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-120">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="ff6e0-121">まず、構成ファイルが生成されません。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-121">First no configuration file is generated.</span></span> <span data-ttu-id="ff6e0-122">Windows ストア アプリケーションでは構成ファイルが使用されないため、コードで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-122">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="ff6e0-123">この構成コードは、"サービス参照の追加" によって生成される References.cs ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-123">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="ff6e0-124">このファイルを表示するには、ソリューションエクスプローラーで [すべてのファイルを表示] を選択してください。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-124">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="ff6e0-125">このファイルは、[サービス参照] の下のプロジェクト内の Reference.svcmap ノードにあります。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-125">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="ff6e0-126">Windows ストア アプリケーション内で WCF サービスに対して生成されるすべての操作は非同期で、タスク ベースの非同期パターンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-126">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="ff6e0-127">詳細については、「 [非同期タスク-タスクを使用した非同期プログラミングの簡素化](/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-127">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="ff6e0-128">構成がコードで生成されるようになったため、サービス参照を更新するたびに、Reference.cs ファイルで行ったすべての変更が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-128">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="ff6e0-129">この状況に対処するために、構成コードは部分メソッド内に生成され、これをクライアント プロキシ クラスで実装できます。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-129">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="ff6e0-130">部分メソッドは次のように宣言されています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-130">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="ff6e0-131">その後、この部分メソッドを実装し、次のように、クライアント プロキシ クラスのバインドまたはエンドポイントを変更できます。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-131">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a><span data-ttu-id="ff6e0-132">シリアル化</span><span class="sxs-lookup"><span data-stu-id="ff6e0-132">Serialization</span></span>  

 <span data-ttu-id="ff6e0-133">Windows ストア アプリケーションでは、次のシリアライザーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-133">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="ff6e0-134">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="ff6e0-134">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="ff6e0-135">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="ff6e0-135">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="ff6e0-136">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="ff6e0-136">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ff6e0-137">XmlDictionaryWriter.Write(DateTime) は、DateTime オブジェクトを文字列として出力するようになりました。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-137">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="ff6e0-138">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ff6e0-138">Security</span></span>  

<span data-ttu-id="ff6e0-139">Windows ストアアプリケーションでは、次のセキュリティモードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-139">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="ff6e0-140">Windows ストアアプリケーションでは、次のクライアント資格情報の種類がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-140">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="ff6e0-141">なし</span><span class="sxs-lookup"><span data-stu-id="ff6e0-141">None</span></span>  
  
2. <span data-ttu-id="ff6e0-142">Basic</span><span class="sxs-lookup"><span data-stu-id="ff6e0-142">Basic</span></span>  
  
3. <span data-ttu-id="ff6e0-143">ダイジェスト</span><span class="sxs-lookup"><span data-stu-id="ff6e0-143">Digest</span></span>  
  
4. <span data-ttu-id="ff6e0-144">ネゴシエート</span><span class="sxs-lookup"><span data-stu-id="ff6e0-144">Negotiate</span></span>  
  
5. <span data-ttu-id="ff6e0-145">NTLM</span><span class="sxs-lookup"><span data-stu-id="ff6e0-145">NTLM</span></span>  
  
6. <span data-ttu-id="ff6e0-146">Windows</span><span class="sxs-lookup"><span data-stu-id="ff6e0-146">Windows</span></span>  
  
7. <span data-ttu-id="ff6e0-147">ユーザー名 (メッセージ セキュリティ)</span><span class="sxs-lookup"><span data-stu-id="ff6e0-147">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="ff6e0-148">Windows (トランスポート セキュリティ)</span><span class="sxs-lookup"><span data-stu-id="ff6e0-148">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="ff6e0-149">Windows ストア アプリケーションから既定の Windows 資格情報にアクセスして送信するためには、Package.appmanifest ファイル内でこの機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-149">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="ff6e0-150">このファイルを開き、[機能] タブを選択し、[既定の Windows 資格情報] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-150">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="ff6e0-151">これにより、ドメイン資格情報を必要とするイントラネット リソースにアプリケーションが接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-151">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ff6e0-152">Windows ストアアプリケーションでコンピューター間の呼び出しを行うには、"ホーム/社内ネットワーク" と呼ばれる別の機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-152">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="ff6e0-153">この設定は、[機能] タブの下にある appmanifest.xaml ファイルにもあります。[ホーム/社内ネットワーク] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-153">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="ff6e0-154">これにより、アプリケーションは、自宅や職場など、ユーザーの信頼できる場所のネットワークへの受信および送信アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-154">This gives your application inbound and outbound access to the networks of the user's trusted places like home and work.</span></span> <span data-ttu-id="ff6e0-155">着信方向の重要なポートは常にブロックされます。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-155">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="ff6e0-156">また、インターネット上のサービスにアクセスするには、インターネット (クライアント) の機能も有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-156">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="ff6e0-157">その他</span><span class="sxs-lookup"><span data-stu-id="ff6e0-157">Misc</span></span>  

 <span data-ttu-id="ff6e0-158">Windows ストア アプリケーションでは、次のクラスの使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-158">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="ff6e0-159">サービス コントラクトの定義</span><span class="sxs-lookup"><span data-stu-id="ff6e0-159">Defining Service Contracts</span></span>  

 <span data-ttu-id="ff6e0-160">非同期サービス操作の定義には、タスク ベースの非同期パターンのみを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-160">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="ff6e0-161">これにより、サービス操作の呼び出し中も、Windows ストア アプリケーションの応答が維持されます。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-161">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ff6e0-162">同期操作を定義した場合でも例外はスローされませんが、非同期操作のみを定義することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-162">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="ff6e0-163">Windows ストア アプリケーションからの WCF サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="ff6e0-163">Calling WCF Services from Windows Store Applications</span></span>  

 <span data-ttu-id="ff6e0-164">既に説明したように、すべての構成は、生成されたプロキシ クラスの GetBindingForEndpoint メソッドのコード内で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-164">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="ff6e0-165">次のコードに示すように、サービス操作の呼び出しは、タスク ベースの非同期メソッドの呼び出しと同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-165">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 <span data-ttu-id="ff6e0-166">非同期呼び出しを行うメソッドでは async キーワード、非同期メソッドの呼び出し時には await キーワードが使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ff6e0-166">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6e0-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff6e0-167">See also</span></span>

- [<span data-ttu-id="ff6e0-168">WCF セキュリティのプログラミング</span><span class="sxs-lookup"><span data-stu-id="ff6e0-168">Programming WCF Security</span></span>](programming-wcf-security.md)
- [<span data-ttu-id="ff6e0-169">バインド</span><span class="sxs-lookup"><span data-stu-id="ff6e0-169">Bindings</span></span>](../bindings.md)
