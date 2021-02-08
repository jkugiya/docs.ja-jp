---
description: '詳細については、「方法: ポート共有を使用するように Windows Communication Foundation サービスを構成する」を参照してください。'
title: '方法 : ポート共有を使用するように Windows Communication Foundation サービスを構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 53fe3449ece5a5e545d7add5c4e6c7feebe5a8ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780103"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="b6dd0-103">方法 : ポート共有を使用するように Windows Communication Foundation サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="b6dd0-103">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>

<span data-ttu-id="b6dd0-104">Windows Communication Foundation (WCF) アプリケーションで net.tcp://ポート共有を使用する最も簡単な方法は、を使用してサービスを公開することです <xref:System.ServiceModel.NetTcpBinding> 。</span><span class="sxs-lookup"><span data-stu-id="b6dd0-104">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="b6dd0-105">このバインディングは、<xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> プロパティを提供します。このプロパティは、このバインディングを使用して構成されるサービスに対して net.tcp:// ポート共有を有効にするかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="b6dd0-105">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="b6dd0-106">以下の手順では、<xref:System.ServiceModel.NetTcpBinding> クラスを使用して URI (Uniform Resource Identifier)、net.tcp://localhost/MyService にあるエンドポイントを開く方法を示します。最初にコードを使用する場合の手順を示し、次に構成要素を使用する場合の手順を示します。</span><span class="sxs-lookup"><span data-stu-id="b6dd0-106">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="b6dd0-107">コードで NetTcpBinding の net.tcp:// ポート共有を有効にするには</span><span class="sxs-lookup"><span data-stu-id="b6dd0-107">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="b6dd0-108">というコントラクトを実装するサービスを作成し、という名前 `IMyService` `MyService` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b6dd0-108">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="b6dd0-109"><xref:System.ServiceModel.NetTcpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b6dd0-109">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="b6dd0-110"><xref:System.ServiceModel.ServiceHost> を作成し、ポート共有を有効にした `MyService` を使用し、エンドポイント アドレス URI "net.tcp://localhost/MyService" をリッスンする <xref:System.ServiceModel.NetTcpBinding> のサービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6dd0-110">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > <span data-ttu-id="b6dd0-111">このエンドポイント アドレス URI は異なるポート番号を指定しないため、この例では既定の TCP ポートである 808 を使用します。</span><span class="sxs-lookup"><span data-stu-id="b6dd0-111">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="b6dd0-112">トランスポート バインディングでポート共有が明示的に有効になっているため、このサービスはポート 808 を他のプロセスの他のサービスと共有できます。</span><span class="sxs-lookup"><span data-stu-id="b6dd0-112">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="b6dd0-113">ポート共有が許可されておらず、既に別のアプリケーションがポート 808 を使用している場合は、このサービスを開こうとすると <xref:System.ServiceModel.AddressAlreadyInUseException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b6dd0-113">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="b6dd0-114">構成で NetTcpBinding の net.tcp:// ポート共有を有効にするには</span><span class="sxs-lookup"><span data-stu-id="b6dd0-114">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="b6dd0-115">次の例では、構成要素を使用してポート共有を有効にし、サービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6dd0-115">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6dd0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6dd0-116">See also</span></span>

- [<span data-ttu-id="b6dd0-117">Net.TCP ポート共有</span><span class="sxs-lookup"><span data-stu-id="b6dd0-117">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="b6dd0-118">方法: Net.TCP ポート共有サービスを有効にする</span><span class="sxs-lookup"><span data-stu-id="b6dd0-118">How to: Enable the Net.TCP Port Sharing Service</span></span>](how-to-enable-the-net-tcp-port-sharing-service.md)
