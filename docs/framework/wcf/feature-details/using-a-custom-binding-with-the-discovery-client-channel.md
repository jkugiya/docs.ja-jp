---
description: 詳細については、「探索クライアントチャネルでカスタムバインドを使用する」を参照してください。
title: カスタム バインドを探索クライアント チャネルと共に使用する
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: a4dd823aed01785aab4127e4323cdc0a0a6d952a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632374"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="b6e15-103">カスタム バインドを探索クライアント チャネルと共に使用する</span><span class="sxs-lookup"><span data-stu-id="b6e15-103">Using a Custom Binding with the Discovery Client Channel</span></span>

<span data-ttu-id="b6e15-104">カスタム バインドを <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> と共に使用する場合は、<xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> インスタンスを作成する <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6e15-104">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="b6e15-105">DiscoveryEndpointProvider の作成</span><span class="sxs-lookup"><span data-stu-id="b6e15-105">Creating a DiscoveryEndpointProvider</span></span>  

 <span data-ttu-id="b6e15-106"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>は、 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 必要に応じてインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6e15-106">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="b6e15-107">探索エンドポイント プロバイダーを定義するには、<xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> からクラスを派生させ、<xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> メソッドをオーバーライドし、新しい探索エンドポイントを返します。</span><span class="sxs-lookup"><span data-stu-id="b6e15-107">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="b6e15-108">次の例は、探索エンドポイント プロバイダーを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b6e15-108">The following example shows how to create a discovery endpoint provider.</span></span>  
  
```csharp
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
// to the DiscoveryClientBindingElement. The Discovery ClientChannel
// uses this endpoint to send Probe message.  
public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
{  
   public override DiscoveryEndpoint GetDiscoveryEndpoint()  
   {  
      return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
   }  
}  
```  
  
 <span data-ttu-id="b6e15-109">探索エンドポイント プロバイダーを定義したら、次の例に示すように、カスタム バインディングを作成し、その探索エンドポイント プロバイダーを参照する <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> を追加できます。</span><span class="sxs-lookup"><span data-stu-id="b6e15-109">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
```csharp
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 <span data-ttu-id="b6e15-110">探索クライアントチャネルの使用方法の詳細については、「 [探索クライアントチャネルの使用](using-the-discovery-client-channel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6e15-110">For more information about using the discovery client channel, see [Using the Discovery Client Channel](using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b6e15-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6e15-111">See also</span></span>

- [<span data-ttu-id="b6e15-112">WCF Discovery の概要</span><span class="sxs-lookup"><span data-stu-id="b6e15-112">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="b6e15-113">探索クライアント チャネルの使用</span><span class="sxs-lookup"><span data-stu-id="b6e15-113">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)
