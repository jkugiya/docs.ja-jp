---
description: '詳細情報: 方法:継承階層を割り当てる'
title: '方法: 継承階層を割り当てる'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 19d7e73dd477a474c98612fae8b0376188d1f08f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802035"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="46cde-103">方法: 継承階層を割り当てる</span><span class="sxs-lookup"><span data-stu-id="46cde-103">How to: Map Inheritance Hierarchies</span></span>

<span data-ttu-id="46cde-104">LINQ で継承の割り当てを実装するには、以下の手順で示すように、継承階層のルート クラスで属性および属性プロパティを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46cde-104">To implement inheritance mapping in LINQ, you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="46cde-105">Visual Studio を使用している開発者は、オブジェクト リレーショナル デザイナーを使用して継承改装をマップできます。</span><span class="sxs-lookup"><span data-stu-id="46cde-105">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="46cde-106">「[方法:O/R デザイナーを使用して継承を構成する](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46cde-106">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46cde-107">サブクラスには特別な属性やプロパティは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="46cde-107">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="46cde-108">特に、サブクラスに <xref:System.Data.Linq.Mapping.TableAttribute> 属性がない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="46cde-108">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="46cde-109">継承階層を割り当てるには</span><span class="sxs-lookup"><span data-stu-id="46cde-109">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="46cde-110">ルート クラスに <xref:System.Data.Linq.Mapping.TableAttribute> 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="46cde-110">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="46cde-111">ルート クラスに対し、階層構造の各クラスについて <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="46cde-111">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="46cde-112">各 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性に対し、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="46cde-112">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="46cde-113">このプロパティは、データベース テーブルの <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 列に含まれる値を保持し、このデータ行が属するクラスまたはサブクラスを示します。</span><span class="sxs-lookup"><span data-stu-id="46cde-113">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="46cde-114">各 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性に対し、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> プロパティも追加します。</span><span class="sxs-lookup"><span data-stu-id="46cde-114">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="46cde-115">このプロパティは、キー値が示すクラスまたはサブクラスを表す値を保持します。</span><span class="sxs-lookup"><span data-stu-id="46cde-115">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="46cde-116">1 つの <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性にのみ、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="46cde-116">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="46cde-117">このプロパティでは、データベース テーブルから取得された識別値が、継承マッピングのどの <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 値とも一致しないときの、"*フォールバック*" マッピングが指定されます。</span><span class="sxs-lookup"><span data-stu-id="46cde-117">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="46cde-118"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="46cde-118">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="46cde-119">このプロパティは、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 値を保持する列であることを示します。</span><span class="sxs-lookup"><span data-stu-id="46cde-119">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46cde-120">例</span><span class="sxs-lookup"><span data-stu-id="46cde-120">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46cde-121">Visual Studio を使用している場合は、オブジェクト リレーショナル デザイナーを使用して、継承を構成できます。</span><span class="sxs-lookup"><span data-stu-id="46cde-121">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="46cde-122">「[方法:O/R デザイナーを使用して継承を構成する](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="46cde-122">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="46cde-123">次のコード例では、`Vehicle` がルート クラスとして定義され、LINQ の階層を記述するためにここまでの手順が実装されています。</span><span class="sxs-lookup"><span data-stu-id="46cde-123">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for LINQ.</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="46cde-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="46cde-124">See also</span></span>

- [<span data-ttu-id="46cde-125">継承のサポート</span><span class="sxs-lookup"><span data-stu-id="46cde-125">Inheritance Support</span></span>](inheritance-support.md)
- [<span data-ttu-id="46cde-126">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="46cde-126">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
