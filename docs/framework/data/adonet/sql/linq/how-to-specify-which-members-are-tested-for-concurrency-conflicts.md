---
description: '詳細情報: 方法:コンカレンシーの競合を検査するメンバーを指定する'
title: '方法: コンカレンシーの競合を検査するメンバーを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: f2623c1e6afcf97ee2de62b94b80145ca2a5cad3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785857"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="76c57-103">方法: コンカレンシーの競合を検査するメンバーを指定する</span><span class="sxs-lookup"><span data-stu-id="76c57-103">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>

<span data-ttu-id="76c57-104">オプティミスティック コンカレンシーの競合を検出する更新チェックにどのメンバーを含めるかを指定するには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性の <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティに、3 つの列挙値のいずれか 1 つを適用します。</span><span class="sxs-lookup"><span data-stu-id="76c57-104">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="76c57-105"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ (デザイン時に設定) は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の実行時のコンカレンシー機能と一緒に使用されます。</span><span class="sxs-lookup"><span data-stu-id="76c57-105">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="76c57-106">詳しくは、「[オプティミスティック コンカレンシー: 概要)](optimistic-concurrency-overview.md) の下のステートメントを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="76c57-106">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76c57-107">`IsVersion=true` として指定されているメンバーがない限り、元のメンバーの各値は、データベースの現在の状態と比較されます。</span><span class="sxs-lookup"><span data-stu-id="76c57-107">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="76c57-108">詳細については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76c57-108">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="76c57-109">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76c57-109">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="76c57-110">競合の検出でこのメンバーを常に使用するには</span><span class="sxs-lookup"><span data-stu-id="76c57-110">To always use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="76c57-111"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="76c57-111">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="76c57-112"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ値を `Always` に設定します。</span><span class="sxs-lookup"><span data-stu-id="76c57-112">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="76c57-113">競合の検出でこのメンバーを使用しないようにするには</span><span class="sxs-lookup"><span data-stu-id="76c57-113">To never use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="76c57-114"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="76c57-114">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="76c57-115"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ値を `Never` に設定します。</span><span class="sxs-lookup"><span data-stu-id="76c57-115">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="76c57-116">アプリケーションでメンバーの値が変更された場合にのみ、競合の検出でこのメンバーを使用するには</span><span class="sxs-lookup"><span data-stu-id="76c57-116">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1. <span data-ttu-id="76c57-117"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="76c57-117">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="76c57-118"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ値を `WhenChanged` に設定します。</span><span class="sxs-lookup"><span data-stu-id="76c57-118">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76c57-119">例</span><span class="sxs-lookup"><span data-stu-id="76c57-119">Example</span></span>  

 <span data-ttu-id="76c57-120">次の例では、更新チェックで `HomePage` オブジェクトが検査されないように指定しています。</span><span class="sxs-lookup"><span data-stu-id="76c57-120">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="76c57-121">詳細については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76c57-121">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="76c57-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="76c57-122">See also</span></span>

- [<span data-ttu-id="76c57-123">方法: 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="76c57-123">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="76c57-124">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="76c57-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
