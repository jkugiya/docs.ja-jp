---
description: '詳細情報: 方法:コード エディターを使用してエンティティ クラスをカスタマイズする'
title: '方法: コード エディターを使用してエンティティ クラスをカスタマイズする'
ms.date: 03/30/2017
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
ms.openlocfilehash: 6b4e8b5dcd5cb11095667fe95293a376cc63ade8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738989"
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="37e33-103">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="37e33-103">How to: Customize Entity Classes by Using the Code Editor</span></span>

<span data-ttu-id="37e33-104">Visual Studio を使用する開発者は、オブジェクト リレーショナル デザイナーを使用して、エンティティ クラスを作成またはカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="37e33-104">Developers using Visual Studio can use the Object Relational Designer to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="37e33-105">Visual Studio のコード エディターを使用して、独自のマッピング コードを記述したり、既に生成されているコードをカスタマイズしたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="37e33-105">You can also use the Visual Studio code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="37e33-106">詳しくは、「[属性ベースの対応付け](attribute-based-mapping.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="37e33-106">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="37e33-107">このセクションのトピックでは、オブジェクト モデルをカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-107">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="37e33-108">方法: データベースの名前を指定する</span><span class="sxs-lookup"><span data-stu-id="37e33-108">How to: Specify Database Names</span></span>](how-to-specify-database-names.md)  
 <span data-ttu-id="37e33-109"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-109">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="37e33-110">方法: クラスとしてテーブルを表す</span><span class="sxs-lookup"><span data-stu-id="37e33-110">How to: Represent Tables as Classes</span></span>](how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="37e33-111"><xref:System.Data.Linq.Mapping.TableAttribute> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-111">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="37e33-112">方法: クラス メンバーとして列を表す</span><span class="sxs-lookup"><span data-stu-id="37e33-112">How to: Represent Columns as Class Members</span></span>](how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="37e33-113"><xref:System.Data.Linq.Mapping.ColumnAttribute> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-113">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="37e33-114">方法: 主キーを表す</span><span class="sxs-lookup"><span data-stu-id="37e33-114">How to: Represent Primary Keys</span></span>](how-to-represent-primary-keys.md)  
 <span data-ttu-id="37e33-115"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-115">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="37e33-116">方法: データベース リレーションシップを割り当てる</span><span class="sxs-lookup"><span data-stu-id="37e33-116">How to: Map Database Relationships</span></span>](how-to-map-database-relationships.md)  
 <span data-ttu-id="37e33-117"><xref:System.Data.Linq.Mapping.AssociationAttribute> 属性の使い方の例を示します。</span><span class="sxs-lookup"><span data-stu-id="37e33-117">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="37e33-118">方法: 列をデータベース生成列として表す</span><span class="sxs-lookup"><span data-stu-id="37e33-118">How to: Represent Columns as Database-Generated</span></span>](how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="37e33-119"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-119">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="37e33-120">方法: 列をタイムスタンプ列またはバージョン列として表現する</span><span class="sxs-lookup"><span data-stu-id="37e33-120">How to: Represent Columns as Timestamp or Version Columns</span></span>](how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="37e33-121"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-121">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="37e33-122">方法: データベース データ型を指定する</span><span class="sxs-lookup"><span data-stu-id="37e33-122">How to: Specify Database Data Types</span></span>](how-to-specify-database-data-types.md)  
 <span data-ttu-id="37e33-123"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-123">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="37e33-124">方法: 計算列を表す</span><span class="sxs-lookup"><span data-stu-id="37e33-124">How to: Represent Computed Columns</span></span>](how-to-represent-computed-columns.md)  
 <span data-ttu-id="37e33-125"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-125">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="37e33-126">方法: プライベート ストレージ フィールドを指定する</span><span class="sxs-lookup"><span data-stu-id="37e33-126">How to: Specify Private Storage Fields</span></span>](how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="37e33-127"><xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-127">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="37e33-128">方法: null 値を許可する列として列を表す</span><span class="sxs-lookup"><span data-stu-id="37e33-128">How to: Represent Columns as Allowing Null Values</span></span>](how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="37e33-129"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-129">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="37e33-130">方法: 継承階層を割り当てる</span><span class="sxs-lookup"><span data-stu-id="37e33-130">How to: Map Inheritance Hierarchies</span></span>](how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="37e33-131">継承階層の指定に必要な割り当てについて説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-131">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="37e33-132">方法: コンカレンシーの競合のチェックを指定する</span><span class="sxs-lookup"><span data-stu-id="37e33-132">How to: Specify Concurrency-Conflict Checking</span></span>](how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="37e33-133"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e33-133">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e33-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="37e33-134">See also</span></span>

- [<span data-ttu-id="37e33-135">SqlMetal.exe (コード生成ツール)</span><span class="sxs-lookup"><span data-stu-id="37e33-135">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
