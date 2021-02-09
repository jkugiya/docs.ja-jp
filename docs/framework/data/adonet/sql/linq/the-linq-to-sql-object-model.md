---
description: '詳細情報: LINQ to SQL オブジェクト モデル'
title: LINQ to SQL オブジェクト モデル
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: be4021019d09d1479364b25268eefda50b6eaa6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681267"
---
# <a name="the-linq-to-sql-object-model"></a><span data-ttu-id="96318-103">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="96318-103">The LINQ to SQL Object Model</span></span>

<span data-ttu-id="96318-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、開発者のプログラミング言語で表されるオブジェクト モデルが、リレーショナル データベースのデータ モデルに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="96318-104">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model expressed in the programming language of the developer is mapped to the data model of a relational database.</span></span> <span data-ttu-id="96318-105">データ操作はオブジェクト モデルに従って行われます。</span><span class="sxs-lookup"><span data-stu-id="96318-105">Operations on the data are then conducted according to the object model.</span></span>  
  
 <span data-ttu-id="96318-106">このシナリオでは、データベースに対してデータベース コマンド (`INSERT` など) を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="96318-106">In this scenario, you do not issue database commands (for example, `INSERT`) to the database.</span></span> <span data-ttu-id="96318-107">代わりに、オブジェクト モデル内で値を変更し、メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="96318-107">Instead, you change values and execute methods within your object model.</span></span> <span data-ttu-id="96318-108">データベースに対してクエリを実行したり、変更を送信する必要がある場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、要求を正しい SQL コマンドに変換し、そのコマンドをデータベースに送信します。</span><span class="sxs-lookup"><span data-stu-id="96318-108">When you want to query the database or send it changes, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your requests into the correct SQL commands and sends those commands to the database.</span></span>  
  
 ![Linq オブジェクト モデルを示すスクリーンショット。](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="96318-110">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] オブジェクト モデル内の最も基本的な要素と、リレーショナル データ モデル内の要素との関係を、次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="96318-110">The most fundamental elements in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model and their relationship to elements in the relational data model are summarized in the following table:</span></span>  
  
|<span data-ttu-id="96318-111">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="96318-111">LINQ to SQL Object Model</span></span>|<span data-ttu-id="96318-112">リレーショナル データ モデル</span><span class="sxs-lookup"><span data-stu-id="96318-112">Relational Data Model</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="96318-113">エンティティ クラス</span><span class="sxs-lookup"><span data-stu-id="96318-113">Entity class</span></span>|<span data-ttu-id="96318-114">テーブル</span><span class="sxs-lookup"><span data-stu-id="96318-114">Table</span></span>|  
|<span data-ttu-id="96318-115">クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="96318-115">Class member</span></span>|<span data-ttu-id="96318-116">Column</span><span class="sxs-lookup"><span data-stu-id="96318-116">Column</span></span>|  
|<span data-ttu-id="96318-117">関連付け</span><span class="sxs-lookup"><span data-stu-id="96318-117">Association</span></span>|<span data-ttu-id="96318-118">外部キー リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="96318-118">Foreign-key relationship</span></span>|  
|<span data-ttu-id="96318-119">メソッド</span><span class="sxs-lookup"><span data-stu-id="96318-119">Method</span></span>|<span data-ttu-id="96318-120">ストアド プロシージャまたは関数</span><span class="sxs-lookup"><span data-stu-id="96318-120">Stored Procedure or Function</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="96318-121">次の説明は、リレーショナル データ モデルと規則に関する基本的な知識があることが前提です。</span><span class="sxs-lookup"><span data-stu-id="96318-121">The following descriptions assume that you have a basic knowledge of the relational data model and rules.</span></span>  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a><span data-ttu-id="96318-122">LINQ to SQL エンティティ クラスおよびデータベース テーブル</span><span class="sxs-lookup"><span data-stu-id="96318-122">LINQ to SQL Entity Classes and Database Tables</span></span>  

 <span data-ttu-id="96318-123">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、データベース テーブルは "*エンティティ クラス*" によって表されます。</span><span class="sxs-lookup"><span data-stu-id="96318-123">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a database table is represented by an *entity class*.</span></span> <span data-ttu-id="96318-124">エンティティ クラスは、作成する他のクラスに似ていますが、クラスをデータベース テーブルに関連付ける特別な情報を使用して、クラスに注釈を付ける点が異なります。</span><span class="sxs-lookup"><span data-stu-id="96318-124">An entity class is like any other class you might create except that you annotate the class by using special information that associates the class with a database table.</span></span> <span data-ttu-id="96318-125">次の例に示すように、クラス宣言にカスタム属性 (<xref:System.Data.Linq.Mapping.TableAttribute>) を追加することによって、この注釈を付けます。</span><span class="sxs-lookup"><span data-stu-id="96318-125">You make this annotation by adding a custom attribute (<xref:System.Data.Linq.Mapping.TableAttribute>) to your class declaration, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="96318-126">例</span><span class="sxs-lookup"><span data-stu-id="96318-126">Example</span></span>  

 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 <span data-ttu-id="96318-127">テーブルとして宣言されたクラスのインスタンスのみ (つまり、エンティティ クラス)、データベースに保存できます。</span><span class="sxs-lookup"><span data-stu-id="96318-127">Only instances of classes declared as tables (that is, entity classes) can be saved to the database.</span></span>  
  
 <span data-ttu-id="96318-128">詳しくは、「[属性ベースの対応付け](attribute-based-mapping.md)」のテーブル属性のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96318-128">For more information, see the Table Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a><span data-ttu-id="96318-129">LINQ to SQL クラス メンバーおよびデータベース列</span><span class="sxs-lookup"><span data-stu-id="96318-129">LINQ to SQL Class Members and Database Columns</span></span>  

 <span data-ttu-id="96318-130">クラスとテーブルの関連付けに加えて、フィールドまたはプロパティを設定してデータベース列を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="96318-130">In addition to associating classes with tables, you designate fields or properties to represent database columns.</span></span> <span data-ttu-id="96318-131">このためには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の例に示すように <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="96318-131">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] defines the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="96318-132">例</span><span class="sxs-lookup"><span data-stu-id="96318-132">Example</span></span>  

 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 <span data-ttu-id="96318-133">列に対応付けられたフィールドおよびプロパティのみ、データベースに保持したり、データベースから取得できます。</span><span class="sxs-lookup"><span data-stu-id="96318-133">Only fields and properties mapped to columns are persisted to or retrieved from the database.</span></span> <span data-ttu-id="96318-134">列として宣言されていないものは、アプリケーション ロジックの一時的な部分と見なされます。</span><span class="sxs-lookup"><span data-stu-id="96318-134">Those not declared as columns are considered as transient parts of your application logic.</span></span>  
  
 <span data-ttu-id="96318-135"><xref:System.Data.Linq.Mapping.ColumnAttribute> 属性にはさまざまなプロパティがあり、これを使用することで、列を表すメンバーをカスタマイズできます (たとえば、主キー列を表すメンバーを指定できます)。</span><span class="sxs-lookup"><span data-stu-id="96318-135">The <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute has a variety of properties that you can use to customize these members that represent columns (for example, designating a member as representing a primary key column).</span></span> <span data-ttu-id="96318-136">詳しくは、「[属性ベースの対応付け](attribute-based-mapping.md)」の列属性のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96318-136">For more information, see the Column Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a><span data-ttu-id="96318-137">LINQ to SQL の関連付けおよびデータベースの外部キー リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="96318-137">LINQ to SQL Associations and Database Foreign-key Relationships</span></span>  

 <span data-ttu-id="96318-138">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Data.Linq.Mapping.AssociationAttribute> 属性を適用することによって、データベースの関連付け (外部キーと主キーのリレーションシップなど) を表します。</span><span class="sxs-lookup"><span data-stu-id="96318-138">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you represent database associations (such as foreign-key to primary-key relationships) by applying the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="96318-139">次のコード セグメントでは、<xref:System.Data.Linq.Mapping.AssociationAttribute> 属性を持つ `Customer` プロパティが `Order` クラスに含まれています。</span><span class="sxs-lookup"><span data-stu-id="96318-139">In the following segment of code, the `Order` class contains a `Customer` property that has an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="96318-140">このプロパティとその属性が、`Order` クラスおよび `Customer` クラスとのリレーションシップを提供します。</span><span class="sxs-lookup"><span data-stu-id="96318-140">This property and its attribute provide the `Order` class with a relationship to the `Customer` class.</span></span>  
  
 <span data-ttu-id="96318-141">`Customer` クラスの `Order` プロパティを表示する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="96318-141">The following code example shows the `Customer` property from the `Order` class.</span></span>  
  
### <a name="example"></a><span data-ttu-id="96318-142">例</span><span class="sxs-lookup"><span data-stu-id="96318-142">Example</span></span>  

 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 <span data-ttu-id="96318-143">詳しくは、「[属性ベースの対応付け](attribute-based-mapping.md)」の関連付け属性のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96318-143">For more information, see the Association Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a><span data-ttu-id="96318-144">LINQ to SQL メソッドおよびデータベース ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="96318-144">LINQ to SQL Methods and Database Stored Procedures</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="96318-145">は、ストアド プロシージャとユーザー定義関数をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="96318-145">supports stored procedures and user-defined functions.</span></span> <span data-ttu-id="96318-146">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、これらのデータベース定義の概念をクライアント オブジェクトに対応付けることによって、クライアント コードから厳密に型指定された方法でのアクセスが実現されます。</span><span class="sxs-lookup"><span data-stu-id="96318-146">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you map these database-defined abstractions to client objects so that you can access them in a strongly typed manner from client code.</span></span> <span data-ttu-id="96318-147">メソッド シグネチャは、データベース内で定義されているプロシージャおよび関数のシグネチャと可能な限りよく似ています。</span><span class="sxs-lookup"><span data-stu-id="96318-147">The method signatures resemble as closely as possible the signatures of the procedures and functions defined in the database.</span></span> <span data-ttu-id="96318-148">IntelliSense を使用して、これらのメソッドを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="96318-148">You can use IntelliSense to discover these methods.</span></span>  
  
 <span data-ttu-id="96318-149">呼び出しによって対応するプロシージャに返される結果セットは、厳密に型指定されたコレクションです。</span><span class="sxs-lookup"><span data-stu-id="96318-149">A result set that is returned by a call to a mapped procedure is a strongly typed collection.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="96318-150">は、<xref:System.Data.Linq.Mapping.FunctionAttribute> 属性と <xref:System.Data.Linq.Mapping.ParameterAttribute> 属性を使用して、ストアド プロシージャおよび関数をメソッドに対応付けます。</span><span class="sxs-lookup"><span data-stu-id="96318-150">maps stored procedures and functions to methods by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> and <xref:System.Data.Linq.Mapping.ParameterAttribute> attributes.</span></span> <span data-ttu-id="96318-151">ストアド プロシージャを表すメソッドは、<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> プロパティによって、ユーザー定義関数を表すメソッドと区別されます。</span><span class="sxs-lookup"><span data-stu-id="96318-151">Methods representing stored procedures are distinguished from those representing user-defined functions by the <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> property.</span></span> <span data-ttu-id="96318-152">このプロパティが `false` (既定値) に設定されている場合、メソッドはストアド プロシージャを表します。</span><span class="sxs-lookup"><span data-stu-id="96318-152">If this property is set to `false` (the default), the method represents a stored procedure.</span></span> <span data-ttu-id="96318-153">`true` に設定されている場合、メソッドはデータベース関数を表します。</span><span class="sxs-lookup"><span data-stu-id="96318-153">If it is set to `true`, the method represents a database function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96318-154">Visual Studio を使用している場合は、オブジェクト リレーショナル デザイナーを使用して、ストアド プロシージャおよびユーザー定義関数に対応付けられるメソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="96318-154">If you are using Visual Studio, you can use the Object Relational Designer to create methods mapped to stored procedures and user-defined functions.</span></span>  
  
### <a name="example"></a><span data-ttu-id="96318-155">例</span><span class="sxs-lookup"><span data-stu-id="96318-155">Example</span></span>  

 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 <span data-ttu-id="96318-156">詳しくは、「[属性ベースの対応付け](attribute-based-mapping.md)」の関数属性、ストアド プロシージャ属性、パラメーター属性の各セクション、および「[ストアド プロシージャ](stored-procedures.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="96318-156">For more information, see the Function Attribute, Stored Procedure Attribute, and Parameter Attribute sections of [Attribute-Based Mapping](attribute-based-mapping.md) and [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96318-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="96318-157">See also</span></span>

- [<span data-ttu-id="96318-158">属性ベースの対応付け</span><span class="sxs-lookup"><span data-stu-id="96318-158">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="96318-159">背景情報</span><span class="sxs-lookup"><span data-stu-id="96318-159">Background Information</span></span>](background-information.md)
