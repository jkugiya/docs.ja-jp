---
description: '詳細については、「方法: MEX 以外のバインディングを介してメタデータを取得する」を参照してください。'
title: '方法: MEX 以外のバインディングを介してメタデータを取得する'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 521e48d90e9dbed2e0ded61c60af59d063d2b3dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644217"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="7185a-103">方法: MEX 以外のバインディングを介してメタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="7185a-103">How to: Retrieve Metadata Over a non-MEX Binding</span></span>

<span data-ttu-id="7185a-104">ここでは、MEX 以外のバインディングを介して MEX エンドポイントからメタデータを取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="7185a-104">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="7185a-105">このサンプルのコードは、 [カスタムセキュアメタデータエンドポイント](../samples/custom-secure-metadata-endpoint.md) のサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="7185a-105">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="7185a-106">MEX 以外のバインディングを介してメタデータを取得するには</span><span class="sxs-lookup"><span data-stu-id="7185a-106">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="7185a-107">MEX エンドポイントで使用されているバインディングを特定します。</span><span class="sxs-lookup"><span data-stu-id="7185a-107">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="7185a-108">Windows Communication Foundation (WCF) サービスの場合は、サービスの構成ファイルにアクセスすることにより、MEX バインドを特定できます。</span><span class="sxs-lookup"><span data-stu-id="7185a-108">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="7185a-109">この場合、MEX バインディングは、次のサービス構成で定義されています。</span><span class="sxs-lookup"><span data-stu-id="7185a-109">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2. <span data-ttu-id="7185a-110">クライアント構成ファイルで、同じカスタム バインドを構成します。</span><span class="sxs-lookup"><span data-stu-id="7185a-110">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="7185a-111">ここでクライアントは `clientCredentials` 動作も定義して、MEX エンドポイントからメタデータを要求するときに、サービスに対する認証で使用する証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="7185a-111">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="7185a-112">カスタム バインドを介してメタデータを要求するときに Svcutil.exe を使用する場合は、Svcutil.exe の構成ファイル (Svcutil.exe.config) に MEX エンドポイント構成を追加する必要があります。また、エンドポイント構成の名前が、次のコードに示すように、MEX エンドポイントのアドレスの URI スキームと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7185a-112">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>
    </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="7185a-113">`MetadataExchangeClient` を作成して `GetMetadata` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7185a-113">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="7185a-114">これを行うには、次の例に示すように、構成でカスタム バインドを指定する方法と、コードでカスタム バインドを指定する方法の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="7185a-114">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
    ```csharp
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. <span data-ttu-id="7185a-115">次のコードに示すように、`WsdlImporter` を作成して `ImportAllEndpoints` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7185a-115">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="7185a-116">この時点で、サービス エンドポイントのコレクションが取得されます。</span><span class="sxs-lookup"><span data-stu-id="7185a-116">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="7185a-117">メタデータのインポートの詳細については、「 [方法: メタデータをサービスエンドポイントにインポートする](../feature-details/how-to-import-metadata-into-service-endpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7185a-117">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7185a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7185a-118">See also</span></span>

- [<span data-ttu-id="7185a-119">Metadata</span><span class="sxs-lookup"><span data-stu-id="7185a-119">Metadata</span></span>](../feature-details/metadata.md)
