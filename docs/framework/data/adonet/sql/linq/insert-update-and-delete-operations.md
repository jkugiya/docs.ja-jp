---
description: '詳細情報: 挿入、更新、および削除の各操作'
title: 挿入、更新、および削除の各操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 2d0470ed6abe654ca08f954c3de97de207adb75d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803816"
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="35a21-103">挿入、更新、および削除の各操作</span><span class="sxs-lookup"><span data-stu-id="35a21-103">Insert, Update, and Delete Operations</span></span>

<span data-ttu-id="35a21-104">オブジェクト モデルに対してオブジェクトの追加、変更、および削除を行うには、`Insert` で `Update`、`Delete`、および [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の各操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="35a21-104">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="35a21-105">既定では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって SQL に対する操作が変換され、変更内容がデータベースに送信されます。</span><span class="sxs-lookup"><span data-stu-id="35a21-105">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="35a21-106">では、オブジェクトに対して行った変更内容の操作と維持に関して、最大限の柔軟性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="35a21-106">offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="35a21-107">クエリによって取得するか新規に作成することによりエンティティ オブジェクトが使用可能になった後で、通常のオブジェクトと同じようにそれらのオブジェクトをアプリケーションで変更できます。</span><span class="sxs-lookup"><span data-stu-id="35a21-107">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="35a21-108">つまり、それらに対して、値の変更、コレクションへの追加、およびコレクションからの削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="35a21-108">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="35a21-109">では変更履歴が保持されるため、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、変更内容をデータベースに送信できます。</span><span class="sxs-lookup"><span data-stu-id="35a21-109">tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="35a21-110">は連鎖削除操作をサポートせず、認識もしません。</span><span class="sxs-lookup"><span data-stu-id="35a21-110">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="35a21-111">制約を持つテーブルの行を削除するには、データベース内の外部キー制約で `ON DELETE CASCADE` 規則を設定するか、独自のコードを使用して、親オブジェクトの削除を妨げる子オブジェクトを最初に削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35a21-111">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="35a21-112">それ以外の場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35a21-112">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="35a21-113">詳細については、[行をデータベースから削除する](how-to-delete-rows-from-the-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35a21-113">For more information, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>

<span data-ttu-id="35a21-114">次の例では、Northwind サンプル データベースの `Customer` クラスと `Order` クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="35a21-114">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="35a21-115">簡潔にするため、ここではクラス定義を省いています。</span><span class="sxs-lookup"><span data-stu-id="35a21-115">Class definitions are not shown for brevity.</span></span>

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

<span data-ttu-id="35a21-116"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、変更内容をデータベースに送信する SQL コマンドが [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって自動的に生成され、実行されます。</span><span class="sxs-lookup"><span data-stu-id="35a21-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>

> [!NOTE]
> <span data-ttu-id="35a21-117">独自に作成したロジック (通常はストアド プロシージャ) を使用して、この動作をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="35a21-117">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="35a21-118">詳細については、「[既定の動作をオーバーライドするときの開発者の責任](responsibilities-of-the-developer-in-overriding-default-behavior.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35a21-118">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>
>
> <span data-ttu-id="35a21-119">Visual Studio を使用している開発者は、オブジェクト リレーショナル デザイナーを使用して、この目的のストアド プロシージャを開発できます。</span><span class="sxs-lookup"><span data-stu-id="35a21-119">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for this purpose.</span></span>

## <a name="see-also"></a><span data-ttu-id="35a21-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="35a21-120">See also</span></span>

- [<span data-ttu-id="35a21-121">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="35a21-121">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="35a21-122">挿入、更新、および削除の各操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="35a21-122">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
