---
description: '詳細情報: ビジネス ロジックの実装 (LINQ to SQL)'
title: ビジネス ロジックの実装 (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 3f2b7085db3832f37da7520c8f75b6bc120125f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803881"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="2b7f3-103">ビジネス ロジックの実装 (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="2b7f3-103">Implementing Business Logic (LINQ to SQL)</span></span>

<span data-ttu-id="2b7f3-104">このトピックの「ビジネス ロジック」とは、データベースでデータを挿入、更新、または削除される前にデータに適用されるカスタム規則または検証テストのことです。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-104">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="2b7f3-105">ビジネス ロジックは、「ビジネス ルール」または「ドメイン ロジック」とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-105">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="2b7f3-106">n 層アプリケーションでは、通常、論理層として設計されるため、プレゼンテーション層やデータ アクセス層から独立して変更できます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-106">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="2b7f3-107">データベースのデータを更新、挿入、または削除する前または後に、データ アクセス層によってビジネス ロジックを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-107">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="2b7f3-108">ビジネス ロジックは、フィールドの型がテーブル列の型と互換性を持つかどうか確認するスキーマ検証のような簡単なものにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-108">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="2b7f3-109">または、任意の複雑な方法で相互に影響するオブジェクトのセットから成るビジネス ロジックも可能です。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-109">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="2b7f3-110">規則は、データベース上のストアド プロシージャとして、またはメモリ内のオブジェクトとして実装可能です。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-110">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="2b7f3-111">ビジネス ロジックの実装方法とは無関係に、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、部分クラスと部分メソッドを使ってビジネス ロジックをデータ アクセス コードから分離することができます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-111">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="2b7f3-112">LINQ to SQL でビジネス ロジックを呼び出す方法</span><span class="sxs-lookup"><span data-stu-id="2b7f3-112">How LINQ to SQL Invokes Your Business Logic</span></span>  

 <span data-ttu-id="2b7f3-113">手動で、またはオブジェクト リレーショナル デザイナーか SQLMetal を使用して、デザイン時にエンティティ クラスを生成すると、部分クラスとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-113">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="2b7f3-114">つまり、別個のコード ファイル内で、カスタム ビジネス ロジックを格納するエンティティ クラスの別の部分を定義できます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-114">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="2b7f3-115">コンパイル時に 2 つの部分が 1 つのクラスにマージされます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-115">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="2b7f3-116">ただし、オブジェクト リレーショナル デザイナーまたは SQLMetal を使ってエンティティ クラスを再生成する必要がある場合は、そうしてもかまいません。その場合、開発者が作成したクラスの部分は変更されません。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-116">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="2b7f3-117">エンティティと <xref:System.Data.Linq.DataContext> を定義する部分クラスには、部分メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-117">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="2b7f3-118">これらは機能拡張ポイントであり、これらを使用して、エンティティまたはエンティティ プロパティを更新、挿入、削除する前および後にビジネス ロジックを適用できます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-118">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="2b7f3-119">部分メソッドはコンパイル時のイベントのようなものです。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-119">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="2b7f3-120">コード ジェネレーターはメソッド シグネチャを定義して、get および set プロパティ アクセサー内、`DataContext` コンストラクター内、および、場合によっては <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼び出し時に背後でメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-120">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="2b7f3-121">ただし、特定の部分メソッドを実装しない場合には、そのメソッドのすべての参照と定義はコンパイル時に削除されます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-121">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="2b7f3-122">別個のコード ファイル内に作成する実装定義では、必要な任意のカスタム ロジックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-122">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="2b7f3-123">部分クラス自体をドメイン層として使用できます。または、部分メソッドの実装定義から別個の 1 つ以上のオブジェクトに呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-123">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="2b7f3-124">どちらの場合も、ビジネス ロジックはデータ アクセス コードとプレゼンテーション層コードから明確に分離されています。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-124">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="2b7f3-125">機能拡張ポイントの詳細</span><span class="sxs-lookup"><span data-stu-id="2b7f3-125">A Closer Look at the Extensibility Points</span></span>  

 <span data-ttu-id="2b7f3-126">次の例は、`Customers` と `Orders` の 2 つのテーブルを持つ `DataContext` クラス用にオブジェクト リレーショナル デザイナーによって生成されるコードの一部分です。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-126">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="2b7f3-127">このクラスで Insert、Update、および Delete メソッドがテーブルごとに定義されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-127">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 <span data-ttu-id="2b7f3-128">部分クラス内で Insert、Update、および Delete メソッドを実装すると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ランタイムは <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の呼び出し時に、既定のメソッドの代わりにこれらのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-128">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="2b7f3-129">こうすることで、作成、読み取り、更新、削除操作の既定の動作をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-129">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="2b7f3-130">詳細については、「[チュートリアル:エンティティ クラスの挿入、更新、および削除の動作のカスタマイズ](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-130">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="2b7f3-131">`OnCreated` メソッドはクラス コンストラクター内で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-131">The `OnCreated` method is called in the class constructor.</span></span>  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 <span data-ttu-id="2b7f3-132">エンティティの作成時、読み込み時、および検証時 ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の呼び出し時) に `SubmitChanges` ランタイムによって呼び出される 3 つのメソッドが、エンティティ クラスに含まれています。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-132">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="2b7f3-133">さらに、エンティティ クラスには、各プロパティごとの 2 つの部分メソッドも含まれています。このうち 1 つはプロパティの設定前に、もう 1 つは設定後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-133">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="2b7f3-134">次のコード例は、`Customer` クラス用に生成されるいくつかのメソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-134">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 <span data-ttu-id="2b7f3-135">以下の `CustomerID` プロパティの例に示されるように、メソッドはプロパティの set アクセサー内で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-135">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 <span data-ttu-id="2b7f3-136">クラスの開発者が作成する部分で、メソッドの実装定義を記述します。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-136">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="2b7f3-137">Visual Studio では、「`partial`」と入力した後、クラスの別の部分にメソッド定義用の IntelliSense が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-137">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 <span data-ttu-id="2b7f3-138">部分メソッドを使ってビジネス ロジックをアプリケーションに追加する方法の詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b7f3-138">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="2b7f3-139">方法: エンティティ クラスに検証を追加する</span><span class="sxs-lookup"><span data-stu-id="2b7f3-139">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="2b7f3-140">チュートリアル: エンティティ クラスの挿入、更新、および削除の動作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="2b7f3-140">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="2b7f3-141">[チュートリアル: エンティティ クラスに検証を追加する](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="2b7f3-141">[Walkthrough: Adding Validation to Entity Classes](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b7f3-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b7f3-142">See also</span></span>

- [<span data-ttu-id="2b7f3-143">部分クラスと部分メソッド</span><span class="sxs-lookup"><span data-stu-id="2b7f3-143">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="2b7f3-144">部分メソッド</span><span class="sxs-lookup"><span data-stu-id="2b7f3-144">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="2b7f3-145">Visual Studio の LINQ to SQL ツール</span><span class="sxs-lookup"><span data-stu-id="2b7f3-145">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="2b7f3-146">SqlMetal.exe (コード生成ツール)</span><span class="sxs-lookup"><span data-stu-id="2b7f3-146">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
