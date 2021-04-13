---
title: '方法: 構成でクライアント バインディングを指定する'
description: 構成ファイル内で WCF クライアントのバインドを宣言によって指定する方法について説明します。 この例では、サービスがクライアントによってアクセスされます。
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: e8a552211b28c1323b2afd595c5b060db6b2824a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236508"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>方法: 構成でクライアント バインディングを指定する

この例では、電卓サービスを使用するためのクライアント コンソール アプリケーションを作成し、そのクライアントのバインディングを構成で宣言によって指定します。 クライアントは `CalculatorService` にアクセスします。これにより、`ICalculator` インターフェイスが実装され、サービスとクライアントの両方で <xref:System.ServiceModel.BasicHttpBinding> クラスが使用されます。  
  
 ここで説明する手順は、電卓サービスが実行されていることを前提とします。 サービスを構築する方法の詳細については、「[方法: 構成でサービス バインディングを指定する](how-to-specify-a-service-binding-in-configuration.md)」を参照してください。 また、Windows Communication Foundation (WCF) によって提供される [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、クライアント コンポーネントが自動的に生成されます。 このツールにより、サービスにアクセスするためのクライアント コードと構成が生成されます。  
  
 クライアントは 2 つの部分で構成されます。 Svcutil.exe によって、`ClientCalculator` インターフェイスを実装する `ICalculator` が生成されます。 次に、`ClientCalculator` のインスタンスを作成することで、クライアント アプリケーションを作成します。  
  
 通常、ベスト プラクティスは、コードで命令として記述するよりも、構成でバインディングを指定して情報を明示的にアドレス指定することです。 設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。 一般的に、バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。  
  
 次のすべての構成ステップは、[構成エディター ツール (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) を使用して実行できます。  
  
 この例のソースのコピーについては、「[BasicBinding](./samples/basicbinding.md)」のサンプルを参照してください。  
  
### <a name="specifying-a-client-binding-in-configuration"></a>構成を使用したクライアント バインディングの指定  
  
1. コマンド ラインから Svcutil.exe を実行して、サービス メタデータからコードを生成します。  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. 生成されたクライアントには、クライアントの実装時に満たされなければならないサービス コントラクトを定義する `ICalculator` インターフェイスが含まれます。  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. 生成されたクライアントは `ClientCalculator` も実装します。  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <xref:System.ServiceModel.BasicHttpBinding> クラスを使用するクライアントの構成も、Svcutil.exe により生成されます。 Visual Studio を使用する場合、このファイルに App.config という名前を付けます。このサービスの実装では、アドレスおよびバインディング情報が指定されないことに注意してください。 同様に、コードは構成ファイルから情報を取得する必要はありません。  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. クライアントをコンパイルして実行します。  
  
## <a name="see-also"></a>関連項目

- [サービスとクライアントを構成するためのバインディングの使用](using-bindings-to-configure-services-and-clients.md)
