---
description: '詳細情報: 操作のカスタマイズ:概要'
title: 操作のカスタマイズ:概要
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: bdcaf482f49b9c55fb7a1834b19b683ac2fa16bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729602"
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="eed1d-103">操作のカスタマイズ:概要</span><span class="sxs-lookup"><span data-stu-id="eed1d-103">Customizing Operations: Overview</span></span>

<span data-ttu-id="eed1d-104">既定では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、対応付けに基づいて、挿入、更新、および削除の各操作のための動的な SQL を生成します。</span><span class="sxs-lookup"><span data-stu-id="eed1d-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="eed1d-105">しかし実際には、セキュリティや検証などを目的とした独自のビジネス ロジックを追加することが必要になる場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="eed1d-105">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="eed1d-106">では、以下の方法で、これらの操作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="eed1d-106">techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="eed1d-107">読み込みオプション</span><span class="sxs-lookup"><span data-stu-id="eed1d-107">Loading Options</span></span>  

 <span data-ttu-id="eed1d-108">クエリで、データベースに接続するときに、メイン ターゲットに関係するデータをどれだけ取得するかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="eed1d-108">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="eed1d-109">この機能は主に、<xref:System.Data.Linq.DataLoadOptions> を使用して実装します。</span><span class="sxs-lookup"><span data-stu-id="eed1d-109">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="eed1d-110">詳細については、「[遅延読み込みと即時読み込み](deferred-versus-immediate-loading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed1d-110">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="eed1d-111">部分メソッド</span><span class="sxs-lookup"><span data-stu-id="eed1d-111">Partial Methods</span></span>  

 <span data-ttu-id="eed1d-112">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] による既定の対応付けでは、ビジネス ロジックの実装に使用できる部分メソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="eed1d-112">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="eed1d-113">詳細については、「[部分メソッドによるビジネス ロジックの追加](adding-business-logic-by-using-partial-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed1d-113">For more information, see [Adding Business Logic By Using Partial Methods](adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="eed1d-114">ストアド プロシージャおよびユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="eed1d-114">Stored Procedures and User-Defined Functions</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="eed1d-115">では、ストアド プロシージャとユーザー定義関数の使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="eed1d-115">supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="eed1d-116">ストアド プロシージャは、操作のカスタマイズによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="eed1d-116">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="eed1d-117">詳細については、「[ストアド プロシージャ](stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed1d-117">For more information, see [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed1d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="eed1d-118">See also</span></span>

- [<span data-ttu-id="eed1d-119">挿入、更新、および削除の各操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="eed1d-119">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
