---
description: '詳細情報: ローカル メソッド呼び出し'
title: ローカル メソッド呼び出し
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 7f3870a700ac86e87e3464f0bc6aaccbb2525168
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695542"
---
# <a name="local-method-calls"></a><span data-ttu-id="dc853-103">ローカル メソッド呼び出し</span><span class="sxs-lookup"><span data-stu-id="dc853-103">Local Method Calls</span></span>

<span data-ttu-id="dc853-104">ローカル メソッド呼び出しとは、オブジェクト モデル内で実行される呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="dc853-104">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="dc853-105">リモート メソッド呼び出しとは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が SQL に変換し、データベース エンジンに送信して実行される呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="dc853-105">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="dc853-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が呼び出しを SQL に変換できないときには、ローカル メソッド呼び出しが必要です。</span><span class="sxs-lookup"><span data-stu-id="dc853-106">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="dc853-107">それ以外の場合は、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="dc853-107">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="dc853-108">例 1</span><span class="sxs-lookup"><span data-stu-id="dc853-108">Example 1</span></span>  

 <span data-ttu-id="dc853-109">次の例では、`Order` クラスは Northwind サンプル データベースの Orders テーブルに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="dc853-109">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="dc853-110">このクラスには、ローカル インスタンス メソッドが追加されています。</span><span class="sxs-lookup"><span data-stu-id="dc853-110">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="dc853-111">クエリ 1 では、`Order` クラスのコンストラクターがローカルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="dc853-111">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="dc853-112">クエリ 2 では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が `LocalInstanceMethod()` を SQL に変換しようとすると、処理は失敗し、<xref:System.InvalidOperationException> 例外がスローされるはずです。</span><span class="sxs-lookup"><span data-stu-id="dc853-112">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="dc853-113">しかし、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ではローカル メソッド呼び出しがサポートされているため、クエリ 2 で例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="dc853-113">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dc853-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc853-114">See also</span></span>

- [<span data-ttu-id="dc853-115">背景情報</span><span class="sxs-lookup"><span data-stu-id="dc853-115">Background Information</span></span>](background-information.md)
