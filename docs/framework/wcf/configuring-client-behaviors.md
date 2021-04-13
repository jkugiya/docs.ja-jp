---
title: クライアントの動作の構成
description: WCF によって動作が構成される 2 つの方法 (アプリケーション構成ファイル内で、または呼び出し元アプリケーションからプログラムによって) について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 34cbb9e31933debb5120eb30956c3a5f0be065ed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266715"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="ea2a6-103">クライアントの動作の構成</span><span class="sxs-lookup"><span data-stu-id="ea2a6-103">Configuring Client Behaviors</span></span>

<span data-ttu-id="ea2a6-104">Windows Communication Foundation (WCF) では 2 通りの方法で動作が構成されます。1 つは動作の構成を参照する方法で、これはクライアント アプリケーションの構成ファイルの `<behavior>` セクションで定義されます。もう 1 つは、呼び出し元アプリケーションでプログラムによって行う方法です。</span><span class="sxs-lookup"><span data-stu-id="ea2a6-104">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="ea2a6-105">このトピックでは、両方の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea2a6-105">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="ea2a6-106">構成ファイルを使用する場合、動作の構成には、構成設定の名前付きコレクションがあります。</span><span class="sxs-lookup"><span data-stu-id="ea2a6-106">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="ea2a6-107">各動作の構成には、一意の名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea2a6-107">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="ea2a6-108">この文字列をエンドポイントの構成の `behaviorConfiguration` 属性で使用し、エンドポイントと動作を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="ea2a6-108">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea2a6-109">例</span><span class="sxs-lookup"><span data-stu-id="ea2a6-109">Example</span></span>  

 <span data-ttu-id="ea2a6-110">`myBehavior` という動作を定義する構成コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="ea2a6-110">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="ea2a6-111">クライアント エンドポイントは、この動作を `behaviorConfiguration` 属性で参照します。</span><span class="sxs-lookup"><span data-stu-id="ea2a6-111">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="ea2a6-112">プログラムによる動作の使用</span><span class="sxs-lookup"><span data-stu-id="ea2a6-112">Using Behaviors Programmatically</span></span>  

 <span data-ttu-id="ea2a6-113">クライアントを開く前に、Windows Communication Foundation (WCF) クライアント オブジェクトまたはクライアント チャネル ファクトリ オブジェクト上の適切な `Behaviors` プロパティを見つけることで、動作をプログラムによって構成または挿入することもできます。</span><span class="sxs-lookup"><span data-stu-id="ea2a6-113">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea2a6-114">例</span><span class="sxs-lookup"><span data-stu-id="ea2a6-114">Example</span></span>  

 <span data-ttu-id="ea2a6-115">次のコード例は、チャネル オブジェクトの作成前に、<xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> プロパティから返される <xref:System.ServiceModel.Description.ServiceEndpoint> 上の <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> プロパティにアクセスすることで、プログラムでクライアント動作が挿入される方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ea2a6-115">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="ea2a6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea2a6-116">See also</span></span>

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
