---
description: '詳細情報: 並列および順次の LINQ クエリを連結する方法'
title: '方法: 並列および順次の LINQ クエリを連結する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: b3ff966b944516bed6cfb4cacd32cb550455fea9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702068"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>方法: 並列および順次の LINQ クエリを連結する

この例では、PLINQ にクエリ内の後続のすべての演算子を順次処理するように指示する <xref:System.Linq.ParallelEnumerable.AsSequential%2A> メソッドの使用方法を示します。 順次処理はしばしば並列処理よりも遅いですが、正しい結果を出すためにこれが必要な場合もあります。  
  
> [!NOTE]
> この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。 高速化の詳細については、「[PLINQ での高速化について](understanding-speedup-in-plinq.md)」を参照してください。  
  
## <a name="example"></a>例  

 次の例は、クエリの前の句で確立された順序を保持する <xref:System.Linq.ParallelEnumerable.AsSequential%2A> が必要な 1 つのシナリオを示します。  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  

 このコードをコンパイルして実行するには、これを [PLINQ データのサンプル](plinq-data-sample.md) プロジェクトに貼り付けて、`Main` からメソッドを呼び出す行を追加し、**F5** キーを押します。  
  
## <a name="see-also"></a>関連項目

- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
