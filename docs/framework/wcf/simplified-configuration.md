---
title: 簡略化された構成
description: WCF サービスの簡略化された構成について説明します。 .NET Framework 4.6.1 には、サービス構成の規模と複雑さを軽減する手段が用意されています。
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 248fe05e5854dbbec1a66b046c4def3d11d30327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235949"
---
# <a name="simplified-configuration"></a>簡略化された構成

Windows Communication Foundation (WCF) サービスの構成は複雑な作業になる場合があります。 さまざまなオプションがあり、どの設定が必要であるかをいつでも簡単に判断できるとは限りません。 構成ファイルは、使用すると WCF サービスの柔軟性が高まりますが、発見しにくい問題の多くの根源でもあります。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] では、このような問題に対応し、サービス構成の規模と複雑さを軽減する手段を提供しています。  
  
## <a name="simplified-configuration"></a>簡略化された構成  

 WCF のサービス構成ファイルでは、<`system.serviceModel`> セクションに、ホストされる各サービスの <`service`> 要素が含まれます。 <`service`> 要素には、各サービスに対して公開されるエンドポイントと、必要に応じて一連のサービス動作を指定する <`endpoint`> 要素のコレクションが含まれます。 <`endpoint`> 要素では、エンドポイントによって公開されるアドレス、バインド、およびコントラクトと、必要に応じてバインド構成およびエンドポイントの動作が指定されます。 <`system.serviceModel`> セクションには、サービスまたはエンドポイントの動作を指定できる <`behaviors`> 要素も含まれます。 構成ファイルの <`system.serviceModel`> セクションの例を次に示します。  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] では、<`service`> 要素の要件を廃止することで、WCF サービスの構成を簡略化しています。 <`service`> セクションを追加したり、<`service`> セクションにエンドポイントを追加したりせず、サービスによってエンドポイントがプログラムを使用して定義されない場合は、一連の既定のエンドポイント (各サービスのベース アドレスに対して 1 つ、サービスによって実装される各コントラクトに対して 1 つ) がサービスに自動的に追加されます。 これらの各エンドポイントでは、エンドポイント アドレスがベース アドレスに対応し、バインドがベース アドレス スキームで決定されます。また、コントラクトは、サービスによって実装されるコントラクトになります。 エンドポイントまたはサービスの動作を指定する必要も、バインド設定を変更する必要もない場合、サービス構成ファイルを指定する必要はありません。 サービスが 2 つのコントラクトを実装し、ホストが HTTP トランスポートと TCP トランスポートの両方を有効にしている場合、サービス ホストは、それぞれのトランスポートを使用する各コントラクトに対して 1 つずつ、合計 4 つの既定のエンドポイントを作成します。 既定のエンドポイントを作成するには、使用するバインドをサービス ホストに伝える必要があります。 これらの設定は、<`system.serviceModel`> セクション内の <`protocolMappings`> セクションに指定します。 <`protocolMappings`> セクションには、バインドの型にマップされたトランスポート プロトコル スキームの一覧が設定されます。 サービス ホストは、渡されたベース アドレスを使用して、使用するバインドを決定します。 次の例では、<`protocolMappings`> 要素を使用しています。  
  
> [!WARNING]
> バインディングまたは動作のような既定の構成要素を変更すると、構成階層の下のレベルで定義されたサービスはこれらの既定のバインディングおよび動作を使用している可能性があるため、影響を受けることがあります。 したがって、既定のバインディングおよび動作を変更する場合は、これらの変更が階層の他のサービスに影響を与える可能性があることに注意する必要があります。  
  
> [!NOTE]
> インターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) にホストされるサービスは、仮想ディレクトリをベース アドレスとして使用します。  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 前の例では、"http" スキームで始まるベース アドレスのエンドポイントは、<xref:System.ServiceModel.BasicHttpBinding> を使用します。 "net.tcp" スキームで始まるベース アドレスのエンドポイントは、<xref:System.ServiceModel.NetTcpBinding> を使用します。 ローカルの App.config または Web.config ファイルの設定はオーバーライドできます。  
  
 <`protocolMappings`> セクション内の各要素では、スキームとバインドを指定する必要があります。 必要に応じて、構成ファイルの <`bindings`> セクション内で、バインド構成を指定する `bindingConfiguration` 属性を指定できます。 `bindingConfiguration` が指定されていない場合は、適切なバインド型の匿名バインド構成が使用されます。  
  
 既定のエンドポイントでは、<`serviceBehaviors`> セクション内の匿名の <`behavior`> セクションを使用して、サービスの動作が構成されます。 サービスの動作の構成には、<`serviceBehaviors`> 内の、名前が付けられていない <`behavior`> 要素が使用されます。 たとえば、次の構成ファイルでは、ホスト内のすべてのサービスで、サービス メタデータの公開が有効になります。  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 エンドポイントの動作は、<`serviceBehaviors`> セクション内の匿名の <`behavior`> セクションを使用して構成されます。  
  
 以下は、このトピックの最初にある例と同じ内容ですが、簡略化された構成モデルを使用している構成ファイルの例です。  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> この機能は、WCF サービス構成にのみ適用され、クライアント構成には適用されません。 ほとんどの場合、WCF クライアント構成は、svcutil.exe などのツールを使用したり、Visual Studio からサービス参照を追加したりすることで生成されます。 手動で WCF クライアントを構成する場合は、構成に \<client> 要素を追加し、呼び出すエンドポイントを指定する必要があります。  
  
## <a name="see-also"></a>関連項目

- [構成ファイルを使用してサービスを構成する方法](configuring-services-using-configuration-files.md)
- [サービスのバインディングの構成](configuring-bindings-for-wcf-services.md)
- [システムが提供するバインディングの構成](./feature-details/configuring-system-provided-bindings.md)
- [サービスの構成](configuring-services.md)
- [WCF サービスの構成](configuring-services.md)
- [コード内での WCF サービスの構成](configuring-wcf-services-in-code.md)
