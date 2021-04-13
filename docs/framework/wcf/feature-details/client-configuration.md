---
title: クライアント構成
description: WCF クライアント構成を使用して、サービスへの接続に使用されるエンドポイントのアドレス、バインディング、動作、およびコントラクトを指定する方法について説明します。
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: af9101be0067311fb1a3c0e6e575f186e8ccf161
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265974"
---
# <a name="client-configuration"></a>クライアント構成

Windows Communication Foundation (WCF) クライアント構成を使用して、クライアント エンドポイントのアドレス (Address)、バインディング (Binding)、動作 (Behavior)、およびコントラクト (Contract) (頭文字を取って "ABC" プロパティと呼ばれます) を指定できます。これらは、クライアントがサービス エンドポイントに接続するために使用されます。 [\<client>](../../configure-apps/file-schema/wcf/client.md) 要素には [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) 要素があり、その属性はエンドポイントの ABC を構成するために使用されます。 これらの属性については、[「エンドポイントの構成」](#configuring-endpoints)セクションで説明します。  
  
 また、[\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) 要素には、メタデータのインポートおよびエクスポート設定を指定するために使用される [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) 要素、カスタムのアドレス ヘッダーのコレクションを格納する [\<headers>](../../configure-apps/file-schema/wcf/headers.md) 要素、およびメッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 要素も含まれます。 [\<headers>](../../configure-apps/file-schema/wcf/headers.md) および [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 要素は <xref:System.ServiceModel.EndpointAddress> の一部であり、[アドレス](endpoint-addresses.md)に関する記事で説明されています。 メタデータ拡張の使用法を説明しているトピックへのリンクは、「[メタデータの構成](#configuring-metadata)」セクションにあります。  
  
## <a name="configuring-endpoints"></a>エンドポイントの構成  

 クライアント構成は、クライアントがエンドポイントを 1 つ以上指定できるように設計されます。それぞれが、独自の名前、アドレス、およびコントラクトを持ち、そのエンドポイントを構成するために使用されるクライアント構成の [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) および [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 要素を参照します。 クライアント構成ファイルには、"App.config" という名前を付ける必要があります。これは、WCF ランタイムが想定している名前です。 クライアント構成ファイルの例を次に示します。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
            <!-- Add another endpoint by adding another <endpoint> element. -->
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"
                 bypassProxyOnLocal="false"
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
          <!-- Configure this binding here. -->  
        </binding>  
          </wsHttpBinding>  
     </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 省略可能な `name` 属性は、特定のコントラクトのエンドポイントを一意に識別します。 この属性は、サービスへのチャネルの作成時に、クライアント構成のどのエンドポイントをターゲットとし、読み込む必要があるかを指定するために、<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> または <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> が使用します。 エンドポイント構成名としてワイルドカード "\*" を使用できます。これは、ファイル内に使用できるエンドポイント構成が 1 つだけ存在する場合にそれを読み込み、それ以外の場合は例外をスローするように <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> メソッドに指示します。 この属性が省略されている場合、指定されたコントラクトの種類に関連する既定のエンドポイントとして、対応するエンドポイントが使用されます。 `name` 属性の既定値は、他の名前と同様に一致する空の文字列です。  
  
 すべてのエンドポイントには、エンドポイントを検索および識別するために、アドレスが関連付けられている必要があります。 `address` 属性は、エンドポイントの場所を示す URL を指定するために使用できます。 ただし、サービス エンドポイントのアドレスは、コードで指定することもできます。その場合は、URI (Uniform Resource Identifier) を作成し、<xref:System.ServiceModel.ServiceHost> メソッドのいずれかを使用して、この URI を <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> に追加します。 詳細については、[アドレス](endpoint-addresses.md)に関する記事を参照してください。 最初に説明したように、[\<headers>](../../configure-apps/file-schema/wcf/headers.md) および [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 要素は <xref:System.ServiceModel.EndpointAddress> の一部であるため、これらについては[アドレス](endpoint-addresses.md)に関する記事でも説明されています。  
  
 `binding` 属性は、エンドポイントがサービスに接続する際に使用するバインディングの種類を示します。 参照できるようにするには、種類は登録された構成セクションを持っている必要があります。 上の例では、[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) セクションがこれであり、エンドポイントによって <xref:System.ServiceModel.WSHttpBinding> が使用されることを示しています。 ただし、エンドポイントが使用できる、指定された種類のバインディングが複数存在することもあります。 これらは、それぞれ (バインディングの) 種類を表す要素内に独自の [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 要素を持ちます。 `bindingconfiguration` 属性は、同じ種類のバインディングを識別するために使用されます。 この値は、[\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 要素の `name` 属性と一致します。 構成を使用してクライアント バインディングを構成する方法の詳細については、「[方法: 構成でクライアント バインディングを指定する](../how-to-specify-a-client-binding-in-configuration.md)」を参照してください。  
  
 `behaviorConfiguration` 属性は、エンドポイントで使用する必要がある [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) の [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) を指定するために使用されます。 この値は、[\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 要素の `name` 属性と一致します。 構成を使用してクライアントの動作を指定する例については、「[クライアントの動作の構成](../configuring-client-behaviors.md)」を参照してください。  
  
 `contract` 属性は、エンドポイントが公開するコントラクトを指定します。 この値は、<xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> の <xref:System.ServiceModel.ServiceContractAttribute> にマップされます。 既定値は、サービスを実装するクラスの完全な型名です。  
  
### <a name="configuring-metadata"></a>メタデータの構成  

 [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) 要素は、メタデータのインポート拡張を登録するための設定を指定するために使用されます。 メタデータ システムの拡張の詳細については、「[メタデータ システムの拡張](../extending/extending-the-metadata-system.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [エンドポイント:アドレス、バインディング、およびコントラクト](endpoints-addresses-bindings-and-contracts.md)
- [クライアントの動作の構成](../configuring-client-behaviors.md)
