---
title: '方法: 非同期サービス操作を実装する'
description: WFC 内での非同期サービス操作の構造について説明します。 サービス操作は、非同期的または同期的に実装できます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 157311f29b203e0c26be21a89d2d5b560543094b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267833"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>方法: 非同期サービス操作を実装する

Windows Communication Foundation (WCF) アプリケーションでは、クライアントに呼び出し方法を指示することなく、サービス操作を非同期的または同期的に実装できます。 たとえば、非同期サービス操作を同期的に呼び出すことも、同期サービス操作を非同期的に呼び出すことも可能です。 クライアント アプリケーションから操作を非同期で呼び出す方法を示す例については、[サービス操作を非同期に呼び出す方法](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)に関する記事を参照してください。 同期および非同期操作の詳細については、「[サービス コントラクトの設計](designing-service-contracts.md)」および「[同期操作と非同期操作](synchronous-and-asynchronous-operations.md)」を参照してください。 このトピックでは、非同期サービス操作の基本構造について説明します。コードは部分的なコードです。 サービスとクライアントの両方の側の完全な例については、「[非同期](/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100))」を参照してください。  
  
### <a name="implement-a-service-operation-asynchronously"></a>非同期サービス操作の実装  
  
1. サービス コントラクトで、.NET 非同期デザイン ガイドラインに従って非同期メソッドのペアを宣言します。 `Begin` メソッドは、パラメーター、コールバック オブジェクト、状態オブジェクトを受け取って <xref:System.IAsyncResult?displayProperty=nameWithType> を返し、組になる `End` メソッドは <xref:System.IAsyncResult?displayProperty=nameWithType> を受け取って戻り値を返します。 非同期呼び出しの詳細については、「[非同期プログラミングのデザイン パターン](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)」を参照してください。  
  
2. 非同期メソッド ペアの `Begin` メソッドを <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> 属性を使用してマークし、<xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> プロパティを `true` に設定します。 たとえば、次のコード例では手順 1. と 2. を実行します。  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. 非同期デザインのガイドラインに従って、`Begin/End` メソッド ペアをサービス クラスに実装します。 たとえば、次のコード例では、非同期サービス操作の `Begin` および `End` の両方の部分の文字列がコンソールに書き出され、`End` 操作の戻り値がクライアントに返される実装を示します。 コード例全体については、「使用例」を参照してください。  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>例  

 このコード例では次のものが示されます。  
  
1. 次の操作とのサービス コントラクト インターフェイス  
  
    1. 同期 `SampleMethod` 操作  
  
    2. 非同期 `BeginSampleMethod` 操作  
  
    3. 非同期 `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` 操作のペア。  
  
2. <xref:System.IAsyncResult?displayProperty=nameWithType> オブジェクトを使用したサービスの実装  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [サービス コントラクトの設計](designing-service-contracts.md)
- [同期操作と非同期操作](synchronous-and-asynchronous-operations.md)
