---
title: WCF サービスの簡略化された構成
description: WCF を使用して、一般的なサービスおよびクライアントを実装し、構成する方法を説明します。 サービスの通信は、構成ファイルで指定されたエンドポイントを使用して行われます。
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 087618d603ea1c7df75ab5383f6c95b781dca847
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290024"
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF サービスの簡略化された構成

このサンプルでは、Windows Communication Foundation (WCF) を使用して一般的なサービスとクライアントを実装および構成する方法を示します。 このサンプルは、他のすべての基本的な技術サンプルの基礎になります。  
  
 このサービスにより、サービスとの通信に使用する単一エンドポイントが公開されており、.NET Framework 4 の簡略化された構成が使用されています。 .NET Framework 4 より前は、次の構成コード例に示すように、エンドポイントは通常、構成ファイル (Web.config) で定義されています。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 .NET Framework 4 では、`<service>` 要素は省略可能です。 サービスでエンドポイントが定義されていない場合、各ベース アドレスのエンドポイントと実装されたコントラクトがサービスに追加されます。 このベース アドレスがコントラクト名に追加されてエンドポイントが決定され、バインドがアドレス スキームで決定されます。 次のコード例は、簡略化された構成ファイルを示しています。 構成のとおり、サービスには、同じコンピューター上のクライアントから `http://localhost/servicemodelsamples/service.svc` でアクセスできます。 リモート コンピューター上のクライアントがサービスにアクセスするには、localhost の代わりに完全修飾ドメイン名を指定する必要があります。 既定では、サービスはメタデータを公開しません。 そのため、サービスは <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 動作を有効にします。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1. [Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。  
  
2. ソリューションをビルドするには、「[Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。  
  
3. 次の手順に従ってサンプルを実行します。  
  
    1. **Service** プロジェクトを右クリックして **[スタートアップ プロジェクトに設定]** を選択し、**Ctrl+F5** キーを押します。  
  
    2. コンソール出力でサービスが動作していることが確認されるまで待機します。  
  
    3. **Client** プロジェクトを右クリックして **[スタートアップ プロジェクトに設定]** を選択し、**Ctrl+F5** キーを押します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](https://www.microsoft.com/download/details.aspx?id=21459)」にアクセスして、Windows Communication Foundation (WCF) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の管理のサンプル](/previous-versions/appfabric/ff383405(v=azure.10))
- [簡略化された構成](../simplified-configuration.md)
