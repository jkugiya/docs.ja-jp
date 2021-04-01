---
description: '詳細情報: PLINQ のマージ オプションを指定する方法'
title: 方法:PLINQ のマージ オプションを指定する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: bfce7617a11a23833dd340b8445d75b164e8045f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701743"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>方法:PLINQ のマージ オプションを指定する

この例では、PLINQ クエリの後続のすべての演算子に適用されるマージ オプションを指定する方法を示します。 マージ オプションを明示的に設定する必要はありませんが、設定することでパフォーマンスが向上する可能性があります。 マージ オプションの詳細については、「[PLINQ のマージ オプション](merge-options-in-plinq.md)」を参照してください。  
  
> [!WARNING]
> この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。 高速化の詳細については、「[PLINQ での高速化について](understanding-speedup-in-plinq.md)」を参照してください。  
  
## <a name="example"></a>例  

 次の例では、順序付けされていないソースがあり、すべての要素に負荷が大きい関数を適用する基本的なシナリオでのマージ オプションの動作を示します。  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 最初の要素が生成される前に <xref:System.Linq.ParallelMergeOptions.AutoBuffered> オプションで望ましくない待機時間が発生した場合は、結果要素をより速く、よりスムーズに生成するために <xref:System.Linq.ParallelMergeOptions.NotBuffered> オプションを試してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Linq.ParallelMergeOptions>
- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
