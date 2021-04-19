---
title: '方法: コード内にサービス エンドポイントを作成する'
description: クラス内でサービスを実装し、そのエンドポイントをプログラムで定義する方法について説明します。 WCF では、エンドポイントは通常、構成ファイル内で定義されます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 6f5e06154ff19129da0bce77dd70736037c2dc92
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294418"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a>方法: コード内にサービス エンドポイントを作成する

この例では、電卓サービスに `ICalculator` コントラクトを定義し、そのサービスを `CalculatorService` クラスに実装し、コード内でサービス エンドポイントを定義します。このエンドポイントでは、サービスが <xref:System.ServiceModel.BasicHttpBinding> クラスを使用するように指定します。  
  
 通常、ベスト プラクティスは、コードで命令として記述するよりも、構成でバインディングを指定して情報を明示的にアドレス指定することです。 設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。 一般的に、バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。  
  
#### <a name="to-create-a-service-endpoint-in-code"></a>コード内にサービス エンドポイントを作成するには  
  
1. サービス コントラクトを定義するインターフェイスを作成します。  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. 手順 1. で定義したサービス コントラクトを実装します。  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. アプリケーションをホストする場合は、サービスで使用するサービスとバインディングのベース アドレスを作成します。  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. ホストを作成し、<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> または他のオーバーロードの 1 つを呼び出して、ホストのサービス エンドポイントを追加します。  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     コード内ではバインディングを指定するものの、ランタイムによって提供された既定のエンドポイントを使用する場合は、<xref:System.ServiceModel.ServiceHost> の作成時にベース アドレスをコンストラクターに渡します。<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType> は呼び出さないでください。  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     既定のエンドポイントの詳細については、「[簡易構成](../simplified-configuration.md)」と「[WCF サービスの簡易構成](../samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [方法: コード内でサービス バインディングを指定する](../how-to-specify-a-service-binding-in-code.md)
