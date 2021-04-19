---
title: '方法: 構成にサービス エンドポイントを作成する'
description: 相対および絶対の両方のアドレスを含む構成ファイルを使用して、WCF サービスのエンドポイントを追加する方法について説明します。
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: aa8dce18a39b44c2c56d072a81699d1bc1e7d7da
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286423"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="97590-103">方法: 構成にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="97590-103">How to: Create a Service Endpoint in Configuration</span></span>

<span data-ttu-id="97590-104">エンドポイントにより、クライアントは Windows Communication Foundation (WCF) サービスによって提供される機能にアクセス権できるようになります。</span><span class="sxs-lookup"><span data-stu-id="97590-104">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="97590-105">エンドポイントの相対アドレスと絶対アドレスを組み合わせてサービスのエンドポイントを 1 つ以上定義できます。または、サービス エンドポイントを定義しない場合、ランタイムは既定で一部を提供します。</span><span class="sxs-lookup"><span data-stu-id="97590-105">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="97590-106">このトピックでは、相対アドレスと絶対アドレスの両方を含んでいる構成ファイルを使用したエンドポイントの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="97590-106">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97590-107">例</span><span class="sxs-lookup"><span data-stu-id="97590-107">Example</span></span>  

 <span data-ttu-id="97590-108">次のサービス構成では、1 つのベース アドレスと 5 つのエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="97590-108">The following service configuration specifies a base address and five endpoints.</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced in .NET Framework 4. -->  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="97590-109">例</span><span class="sxs-lookup"><span data-stu-id="97590-109">Example</span></span>  

 <span data-ttu-id="97590-110">ベース アドレスは、次のサンプルのように `add` 要素を使用して service/host/baseAddresses の下に指定します。</span><span class="sxs-lookup"><span data-stu-id="97590-110">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="97590-111">例</span><span class="sxs-lookup"><span data-stu-id="97590-111">Example</span></span>  

 <span data-ttu-id="97590-112">次のサンプルの最初のエンドポイント定義では、相対アドレスを指定します。つまり、エンドポイント アドレスは、ベース アドレスと URI (Uniform Resource Identifier) 構造の規則に従った相対アドレスの組み合わせということを意味します。</span><span class="sxs-lookup"><span data-stu-id="97590-112">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="97590-113">相対アドレスが空 ("") のため、エンドポイント アドレスはベース アドレスと同じになります。</span><span class="sxs-lookup"><span data-stu-id="97590-113">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="97590-114">実際のエンドポイント アドレスは `http://localhost:8000/servicemodelsamples/service` です。</span><span class="sxs-lookup"><span data-stu-id="97590-114">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="97590-115">例</span><span class="sxs-lookup"><span data-stu-id="97590-115">Example</span></span>  

 <span data-ttu-id="97590-116">2 番目のエンドポイント定義でも、相対アドレスを指定します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97590-116">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="97590-117">相対アドレス "test" がベース アドレスの末尾に追加されています。</span><span class="sxs-lookup"><span data-stu-id="97590-117">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="97590-118">実際のエンドポイント アドレスは `http://localhost:8000/servicemodelsamples/service/test` です。</span><span class="sxs-lookup"><span data-stu-id="97590-118">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="97590-119">例</span><span class="sxs-lookup"><span data-stu-id="97590-119">Example</span></span>  

 <span data-ttu-id="97590-120">3 番目のエンドポイント定義では、絶対アドレスを指定します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97590-120">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="97590-121">このアドレスでは、ベース アドレスは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="97590-121">The base address plays no role in the address.</span></span> <span data-ttu-id="97590-122">実際のエンドポイント アドレスは `http://localhost:8001/hello/servicemodelsamples` です。</span><span class="sxs-lookup"><span data-stu-id="97590-122">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="97590-123">例</span><span class="sxs-lookup"><span data-stu-id="97590-123">Example</span></span>  

 <span data-ttu-id="97590-124">4 番目のエンドポイント アドレスは、絶対アドレスと別のトランスポート (ここでは TCP) を指定しています。</span><span class="sxs-lookup"><span data-stu-id="97590-124">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="97590-125">このアドレスでは、ベース アドレスは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="97590-125">The base address plays no role in the address.</span></span> <span data-ttu-id="97590-126">具体的には net.tcp://localhost:9000/servicemodelsamples/service です。</span><span class="sxs-lookup"><span data-stu-id="97590-126">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="97590-127">例</span><span class="sxs-lookup"><span data-stu-id="97590-127">Example</span></span>  

 <span data-ttu-id="97590-128">ランタイムによって提供された既定のエンドポイントを使用するには、コードまたは構成ファイルでサービス エンドポイントを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="97590-128">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="97590-129">次の例では、サービスを開くときに、ランタイムは既定のエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="97590-129">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="97590-130">既定のエンドポイントについては、「[Simplified Configuration](../simplified-configuration.md)」 (簡易構成) と「[Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md)」 (WCF サービスの簡易構成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97590-130">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```
