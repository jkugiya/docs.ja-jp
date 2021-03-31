---
description: '詳細情報: 静的パーティション分割用にパーティショナーを実装する方法'
title: 方法:静的パーティション分割用にパーティショナーを実装する
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 7636023dcc6036d91dcf76b34b0e445b87dfa8d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702003"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>方法:静的パーティション分割用にパーティショナーを実装する

次の例は、静的なパーティション分割を行う PLINQ 用の単純なカスタム パーティショナーを実装する方法を示しています。 パーティショナーは動的なパーティションをサポートしていないため、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> からは利用することはできません。 この特定のパーティショナーは、各要素が大量の処理時間を必要とするデータ ソースで、既定の範囲のパーティショナーよりも処理速度を向上させることができる場合があります。  
  
## <a name="example"></a>例  

 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 この例のパーティションでは、各要素の処理時間が直線的に増加することが前提となっています。 実際には、この方法で処理時間を予測するのは難しい場合があります。 特定のデータ ソースで静的パーティショナーを使用している場合、ソースのパーティション分割の数式を最適化したり、負荷分散のロジックを追加したり、「[方法: 動的パーティションを実装する](how-to-implement-dynamic-partitions.md)」に示すチャンク パーティション分割の手法を使用することができます。  
  
## <a name="see-also"></a>関連項目

- [PLINQ および TPL 用のカスタム パーティショナー](custom-partitioners-for-plinq-and-tpl.md)
