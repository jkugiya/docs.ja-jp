---
description: '詳細情報: 境界ブロッキング機能をコレクションに追加する方法'
title: '方法: 境界ブロッキング機能をコレクションに追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: c44febe0a7b2155c61b12c280d830ad7b028d326
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676067"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>方法: 境界ブロッキング機能をコレクションに追加する

この例では、<xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> インターフェイスをクラスに実装し、クラスのインスタンスを <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> の内部ストレージ メカニズムとして使用することによって、カスタム コレクション クラスに境界ブロッキング機能を追加する方法を示します。 境界ブロッキングの詳細については、「[BlockingCollection の概要](blockingcollection-overview.md)」を参照してください。  
  
## <a name="example"></a>例  

 カスタム コレクション クラスは基本優先度キューであり、優先度レベルは <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> オブジェクトの配列として表されます。 各キュー内で他の順序付けは行われません。  
  
 クライアント コードでは、3 つのタスクが開始されます。 1 番目のタスクはキーボード入力のポーリングだけを行い、実行中にいつでもキャンセルできるようにします。 2 番目のタスクはプロデューサー スレッドであり、ブロッキング コレクションに新しい項目を追加し、ランダムな値に基づく優先度を各項目に割り当てます。 3 番目のタスクは、利用可能になった項目をコレクションから削除します。  
  
 1 つのスレッドが他より速く実行されるようにすることで、アプリケーションの動作を調整できます。 プロデューサーが高速に実行されると、コンストラクターで指定されている数の項目がコレクションに既に含まれる場合はブロッキング コレクションが項目の追加を防ぐので、境界機能が目立つようになります。 コンシューマーが高速に実行されると、コンシューマーは新しい項目が追加されるのを待機するので、ブロッキング機能が目立つようになります。  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 既定では、<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> の記憶域は <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> です。  
  
## <a name="see-also"></a>関連項目

- [スレッドセーフなコレクション](index.md)
