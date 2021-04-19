---
title: '方法: 構成でサービス バインディングを指定する'
description: 構成ファイルで WCF サービスのエンドポイントを構成する方法について説明します。 コントラクトは、サービスに対して定義され、クラスに実装されます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 06b1cd009d28f854ec73286efa29d42f0f557314
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293690"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>方法: 構成でサービス バインディングを指定する

この例では、簡単な電卓サービス用に `ICalculator` コントラクトを定義し、そのサービスを `CalculatorService` クラスで実装し、そのエンドポイントを Web.config ファイルで構成します。このファイルでは、サービスが <xref:System.ServiceModel.BasicHttpBinding> を使用するように指定します。 構成の代わりにコードを使用してこのサービスを構成する方法については、「[方法: コード内でサービス バインディングを指定する](how-to-specify-a-service-binding-in-code.md)」を参照してください。  
  
 通常、ベスト プラクティスは、コードで命令として記述するよりも、構成でバインディングを指定して情報を明示的にアドレス指定することです。 設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。 一般的に、バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。  
  
 次のすべての構成ステップは、[構成エディター ツール (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) を使用して実行できます。  
  
 この例のソースのコピーについては、「[BasicBinding](./samples/basicbinding.md)」を参照してください。  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>サービスの構成で BasicHttpBinding が使用されるように指定するには  
  
1. サービスの種類にサービス コントラクトを定義します。  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. サービス クラスにサービス コントラクトを実装します。  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > アドレス情報とバインディング情報は、サービスの実装内では指定されません。 また、構成ファイルからこの情報をフェッチするためのコードを記述する必要もありません。  
  
3. `CalculatorService` を使用する <xref:System.ServiceModel.WSHttpBinding> のエンドポイントを構成する Web.config ファイルを作成します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. 次の行を含む Service.svc ファイルを作成し、インターネット インフォメーション サービス (IIS: Internet Information Services) 仮想ディレクトリに配置します。  
  
    ```aspx-csharp
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a>バインディング プロパティの既定値を変更するには  
  
1. <xref:System.ServiceModel.WSHttpBinding> の既定のプロパティ値の 1 つを変更するには、[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) 要素内に `<binding name="Binding1">` という新しいバインディング構成名を作成し、このバインド要素のバインディングの属性に新しい値を設定します。 たとえば、開く操作と閉じる操作の既定のタイムアウト値を 1 分から 2 分に変更するには、構成ファイルに以下を追加します。  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>関連項目

- [サービスとクライアントを構成するためのバインディングの使用](using-bindings-to-configure-services-and-clients.md)
- [エンドポイント アドレスの指定](specifying-an-endpoint-address.md)
