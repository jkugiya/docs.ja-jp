---
title: '方法: ChannelFactory を使用する'
description: WCF クライアントを使用してサービスにアクセスするために、チャネル ファクトリを作成して複数のチャネルを作成する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: dd767443fefb16ebc02300bffa4264357f12c3ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280586"
---
# <a name="how-to-use-the-channelfactory"></a>方法: ChannelFactory を使用する

<xref:System.ServiceModel.ChannelFactory%601> ジェネリック クラスは、複数チャネルの作成に使用できるチャネル ファクトリの作成を必要とする高度なシナリオで使用します。  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>ChannelFactory クラスの作成方法と使用方法  
  
1. Windows Communication Foundation (WCF) サービスを構築し、実行します。 詳細については、「[サービスの設計と実装](../designing-and-implementing-services.md)」、[サービスの構成](../configuring-services.md)に関する記事、および「[ホスティング サービス](../hosting-services.md)」を参照してください。  
  
2. [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、クライアントのコントラクト (インターフェイス) を生成します。  
  
3. クライアント コード内で、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して複数のエンドポイント リスナーを作成します。  
  
## <a name="example"></a>例  

 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
