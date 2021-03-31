---
description: '詳細情報: スキーマをコンパイルするための XmlSchemaSet'
title: スキーマをコンパイルするための XmlSchemaSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 1c053c4db6e9c018e6186e6015aedc9c1b36b4e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782625"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="08144-103">スキーマをコンパイルするための XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="08144-103">XmlSchemaSet for Schema Compilation</span></span>

<span data-ttu-id="08144-104">XML スキーマ定義言語 (XSD) スキーマの格納と検証が可能なキャッシュである <xref:System.Xml.Schema.XmlSchemaSet> について説明します。</span><span class="sxs-lookup"><span data-stu-id="08144-104">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="08144-105">XmlSchemaSet クラス</span><span class="sxs-lookup"><span data-stu-id="08144-105">The XmlSchemaSet Class</span></span>  

 <span data-ttu-id="08144-106"><xref:System.Xml.Schema.XmlSchemaSet> は、XML スキーマ定義言語 (XSD) スキーマの格納と検証が可能なキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="08144-106">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="08144-107"><xref:System.Xml?displayProperty=nameWithType> Version 1.0 では、XML スキーマはスキーマのライブラリとして <xref:System.Xml.Schema.XmlSchemaCollection> クラスに読み込まれました。</span><span class="sxs-lookup"><span data-stu-id="08144-107">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="08144-108"><xref:System.Xml?displayProperty=nameWithType> Version 2.0 では、<xref:System.Xml.XmlValidatingReader> クラスおよび <xref:System.Xml.Schema.XmlSchemaCollection> クラスは廃止され、それぞれ <xref:System.Xml.XmlReader.Create%2A> メソッドおよび <xref:System.Xml.Schema.XmlSchemaSet> クラスによって置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="08144-108">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="08144-109"><xref:System.Xml.Schema.XmlSchemaSet> は、標準との互換性、パフォーマンス、廃止された Microsoft XDR (XML-Data Reduced) スキーマ形式など、多くの問題を解決するために導入されました。</span><span class="sxs-lookup"><span data-stu-id="08144-109">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="08144-110">以下は、<xref:System.Xml.Schema.XmlSchemaCollection> クラスと <xref:System.Xml.Schema.XmlSchemaSet> クラスの比較です。</span><span class="sxs-lookup"><span data-stu-id="08144-110">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="08144-111">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="08144-111">XmlSchemaCollection</span></span>|<span data-ttu-id="08144-112">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="08144-112">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="08144-113">Microsoft XDR と W3C XML スキーマをサポート。</span><span class="sxs-lookup"><span data-stu-id="08144-113">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="08144-114">W3C XML スキーマだけをサポート。</span><span class="sxs-lookup"><span data-stu-id="08144-114">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="08144-115">スキーマは、<xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> メソッドの呼び出し時にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="08144-115">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="08144-116">スキーマは、<xref:System.Xml.Schema.XmlSchemaSet.Add%2A> メソッドの呼び出し時にコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="08144-116">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="08144-117">これによって、スキーマ ライブラリ作成時のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="08144-117">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="08144-118">各スキーマが個別のコンパイル済みバージョンを生成するため、"スキーマ アイランド" が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="08144-118">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="08144-119">結果として、すべての include および import はそのスキーマ内だけにスコープ設定されます。</span><span class="sxs-lookup"><span data-stu-id="08144-119">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="08144-120">コンパイル済みスキーマは、1 つの論理スキーマ (スキーマの集合を 1 つ) を生成します。</span><span class="sxs-lookup"><span data-stu-id="08144-120">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="08144-121">1 つのスキーマ内の、その集合にインポートされ追加されるすべてのスキーマは、集合自体に直接追加されます。</span><span class="sxs-lookup"><span data-stu-id="08144-121">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="08144-122">これは、すべてのスキーマに対して、すべての型を使用できることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="08144-122">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="08144-123">コレクション内では、特定の対象名前空間に対して 1 つのスキーマだけが存在可能です。</span><span class="sxs-lookup"><span data-stu-id="08144-123">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="08144-124">型の競合がない限り、同じ対象名前空間に対して複数のスキーマを追加できます。</span><span class="sxs-lookup"><span data-stu-id="08144-124">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="08144-125">XmlSchemaSet への移行</span><span class="sxs-lookup"><span data-stu-id="08144-125">Migrating to the XmlSchemaSet</span></span>  

 <span data-ttu-id="08144-126">次のサンプル コードでは、廃止された <xref:System.Xml.Schema.XmlSchemaSet> クラスから新しい <xref:System.Xml.Schema.XmlSchemaCollection> クラスへの移行のガイドを提供します。</span><span class="sxs-lookup"><span data-stu-id="08144-126">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="08144-127">このコード サンプルは、次に挙げるこれら 2 つのクラスの主な相違点を説明するものです。</span><span class="sxs-lookup"><span data-stu-id="08144-127">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="08144-128"><xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> クラスの <xref:System.Xml.Schema.XmlSchemaCollection> メソッドとは異なり、スキーマは <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッド呼び出し時にはコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="08144-128">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="08144-129">サンプル コード内では、<xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドが明示的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="08144-129">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="08144-130"><xref:System.Xml.Schema.XmlSchemaSet> を繰り返すには、<xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> の <xref:System.Xml.Schema.XmlSchemaSet> プロパティを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08144-130">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="08144-131">廃止された <xref:System.Xml.Schema.XmlSchemaCollection> のコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="08144-131">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 <span data-ttu-id="08144-132">対応する <xref:System.Xml.Schema.XmlSchemaSet> のコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="08144-132">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="08144-133">スキーマの追加と取り出し</span><span class="sxs-lookup"><span data-stu-id="08144-133">Adding and Retrieving Schemas</span></span>  

 <span data-ttu-id="08144-134">スキーマは <xref:System.Xml.Schema.XmlSchemaSet> の <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> メソッドを使用して <xref:System.Xml.Schema.XmlSchemaSet> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="08144-134">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="08144-135">スキーマが <xref:System.Xml.Schema.XmlSchemaSet> に追加される場合、そのスキーマは対象名前空間の URI に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="08144-135">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="08144-136">対象名前空間の URI は、<xref:System.Xml.Schema.XmlSchemaSet.Add%2A> メソッドへのパラメーターとして指定するか、名前空間が指定されていない場合、<xref:System.Xml.Schema.XmlSchemaSet> がスキーマ内に定義されている名前空間を使用するかのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="08144-136">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="08144-137">スキーマは <xref:System.Xml.Schema.XmlSchemaSet> の <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> プロパティを使用して <xref:System.Xml.Schema.XmlSchemaSet> から取り出されます。</span><span class="sxs-lookup"><span data-stu-id="08144-137">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="08144-138"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> の <xref:System.Xml.Schema.XmlSchemaSet> プロパティでは、<xref:System.Xml.Schema.XmlSchema> に含まれる <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトに対して繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="08144-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="08144-139"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> プロパティは、<xref:System.Xml.Schema.XmlSchema> に含まれるすべての <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトを返すか、または対象名前空間のパラメーターが指定された場合、その名前空間に属するすべての <xref:System.Xml.Schema.XmlSchema> オブジェクトを返すかのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="08144-139">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="08144-140">対象名前空間として `null` が指定された場合、<xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> プロパティは名前空間のないスキーマをすべて返します。</span><span class="sxs-lookup"><span data-stu-id="08144-140">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="08144-141">次の例では、`books.xsd` 名前空間内の `http://www.contoso.com/books` スキーマを <xref:System.Xml.Schema.XmlSchemaSet> に追加し、`http://www.contoso.com/books` 名前空間に属しているすべてのスキーマを <xref:System.Xml.Schema.XmlSchemaSet> から取り出した後、それらのスキーマを <xref:System.Console> に書き出します。</span><span class="sxs-lookup"><span data-stu-id="08144-141">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 <span data-ttu-id="08144-142"><xref:System.Xml.Schema.XmlSchemaSet> オブジェクトのスキーマの追加と取り出しに関する詳細については、<xref:System.Xml.Schema.XmlSchemaSet.Add%2A> メソッドおよび <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> プロパティのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="08144-142">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="08144-143">スキーマのコンパイル</span><span class="sxs-lookup"><span data-stu-id="08144-143">Compiling Schemas</span></span>  

 <span data-ttu-id="08144-144"><xref:System.Xml.Schema.XmlSchemaSet> 内のスキーマは、<xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドによって、1 つの論理スキーマにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="08144-144">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08144-145">廃止された <xref:System.Xml.Schema.XmlSchemaCollection> クラスとは異なり、スキーマは <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> メソッドの呼び出し時にはコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="08144-145">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="08144-146"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> メソッドの実行が成功した場合、<xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> の <xref:System.Xml.Schema.XmlSchemaSet> プロパティは `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="08144-146">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08144-147"><xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> プロパティは、スキーマが <xref:System.Xml.Schema.XmlSchemaSet> 内にあるときに編集されても、影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="08144-147">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="08144-148"><xref:System.Xml.Schema.XmlSchemaSet> 内の個別のスキーマの更新は追跡されません。</span><span class="sxs-lookup"><span data-stu-id="08144-148">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="08144-149">その結果、<xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> プロパティは、`true` のスキーマが追加または削除されない限り、<xref:System.Xml.Schema.XmlSchemaSet> に含まれるスキーマの 1 つが変更されていても、<xref:System.Xml.Schema.XmlSchemaSet> になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="08144-149">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="08144-150">次の例では、`books.xsd` ファイルを <xref:System.Xml.Schema.XmlSchemaSet> に追加した後、<xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="08144-150">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 <span data-ttu-id="08144-151"><xref:System.Xml.Schema.XmlSchemaSet> 内のスキーマのコンパイルに関する詳細については、<xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> メソッドのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="08144-151">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="08144-152">スキーマの再処理</span><span class="sxs-lookup"><span data-stu-id="08144-152">Reprocessing Schemas</span></span>  

 <span data-ttu-id="08144-153"><xref:System.Xml.Schema.XmlSchemaSet> 内のスキーマの再処理は、<xref:System.Xml.Schema.XmlSchemaSet.Add%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッド呼び出し時にスキーマに対して実行されるすべての前処理手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="08144-153">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="08144-154"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> メソッドの呼び出しが成功した場合、<xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> の <xref:System.Xml.Schema.XmlSchemaSet> プロパティは `false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="08144-154">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="08144-155"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> のコンパイル後、<xref:System.Xml.Schema.XmlSchemaSet> 内のスキーマが変更された場合は、<xref:System.Xml.Schema.XmlSchemaSet> メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08144-155">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="08144-156">次の例は、<xref:System.Xml.Schema.XmlSchemaSet> メソッドを使用して <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> に追加されたスキーマの再処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="08144-156">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="08144-157"><xref:System.Xml.Schema.XmlSchemaSet> メソッドを使用して <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> がコンパイルされた後、<xref:System.Xml.Schema.XmlSchemaSet> に追加されたスキーマが変更された場合、<xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 内のスキーマは変更されているのに、`true` プロパティは <xref:System.Xml.Schema.XmlSchemaSet> に設定されています。</span><span class="sxs-lookup"><span data-stu-id="08144-157">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="08144-158"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> メソッドの呼び出しは、<xref:System.Xml.Schema.XmlSchemaSet.Add%2A> メソッドによって実行されるすべての前処理を実行し、<xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="08144-158">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 <span data-ttu-id="08144-159"><xref:System.Xml.Schema.XmlSchemaSet> 内のスキーマの前処理に関する詳細については、<xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> メソッドのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="08144-159">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="08144-160">スキーマの確認</span><span class="sxs-lookup"><span data-stu-id="08144-160">Checking for a Schema</span></span>  

 <span data-ttu-id="08144-161"><xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドを使用して、<xref:System.Xml.Schema.XmlSchemaSet> 内にスキーマが含まれているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="08144-161">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="08144-162"><xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> メソッドは、確認対象に対象名前空間または <xref:System.Xml.Schema.XmlSchema> オブジェクトのどちらかを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="08144-162">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="08144-163">どちらの場合も、<xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> メソッドは、`true` 内にスキーマが含まれている場合 <xref:System.Xml.Schema.XmlSchemaSet> を、それ以外の場合 `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="08144-163">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="08144-164">スキーマの確認に関する詳細については、<xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> メソッドのリファレンス ドキュメントを参照してださい。</span><span class="sxs-lookup"><span data-stu-id="08144-164">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="08144-165">スキーマの削除</span><span class="sxs-lookup"><span data-stu-id="08144-165">Removing Schemas</span></span>  

 <span data-ttu-id="08144-166">スキーマは <xref:System.Xml.Schema.XmlSchemaSet> の <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> および <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> メソッドを使用して <xref:System.Xml.Schema.XmlSchemaSet> から削除されます。</span><span class="sxs-lookup"><span data-stu-id="08144-166">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="08144-167"><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> メソッドは、指定されたスキーマを <xref:System.Xml.Schema.XmlSchemaSet> から削除し、<xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> メソッドは、指定されたスキーマとそのスキーマがインポートしているすべてのスキーマを <xref:System.Xml.Schema.XmlSchemaSet> から削除します。</span><span class="sxs-lookup"><span data-stu-id="08144-167">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="08144-168">以下は、複数のスキーマを <xref:System.Xml.Schema.XmlSchemaSet> に追加してから、<xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> メソッドを使用して、それらのスキーマの 1 つとそのスキーマがインポートしているすべてのスキーマを削除する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="08144-168">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 <span data-ttu-id="08144-169"><xref:System.Xml.Schema.XmlSchemaSet> からのスキーマの削除に関する詳細については、<xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> メソッドおよび <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> メソッドのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="08144-169">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="08144-170">スキーマの解決と xs:import</span><span class="sxs-lookup"><span data-stu-id="08144-170">Schema Resolution and xs:import</span></span>  

 <span data-ttu-id="08144-171">次の例は、<xref:System.Xml.Schema.XmlSchemaSet> 内で、指定された名前空間に対して複数のスキーマが存在するときに、スキーマをインポートする場合の <xref:System.Xml.Schema.XmlSchemaSet> の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="08144-171">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="08144-172">例として、<xref:System.Xml.Schema.XmlSchemaSet> 名前空間に関する複数のスキーマを含む `http://www.contoso.com` を考えます。</span><span class="sxs-lookup"><span data-stu-id="08144-172">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="08144-173">次の `xs:import` ディレクティブを持つスキーマが <xref:System.Xml.Schema.XmlSchemaSet> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="08144-173">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="08144-174"><xref:System.Xml.Schema.XmlSchemaSet> は、`http://www.contoso.com` URL から読み込むことによって、`http://www.contoso.com/schema.xsd` 名前空間に関するスキーマをインポートしようとします。</span><span class="sxs-lookup"><span data-stu-id="08144-174">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="08144-175">`http://www.contoso.com` 名前空間に関する他のスキーマ ドキュメントが <xref:System.Xml.Schema.XmlSchemaSet> 内にある場合でも、インポート元のスキーマでは、スキーマ宣言とそのスキーマ ドキュメント内で定義した型だけしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="08144-175">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="08144-176">`schema.xsd` ファイルが `http://www.contoso.com/schema.xsd` URL で見つからない場合、`http://www.contoso.com` 名前空間に関するスキーマは、インポート元のスキーマにインポートされません。</span><span class="sxs-lookup"><span data-stu-id="08144-176">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="08144-177">XML ドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="08144-177">Validating XML Documents</span></span>  

 <span data-ttu-id="08144-178">XML ドキュメントは、<xref:System.Xml.Schema.XmlSchemaSet> 内のスキーマに対して検証できます。</span><span class="sxs-lookup"><span data-stu-id="08144-178">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="08144-179">スキーマを <xref:System.Xml.XmlReaderSettings> オブジェクトの <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> プロパティに追加するか、<xref:System.Xml.Schema.XmlSchemaSet> を <xref:System.Xml.XmlReaderSettings> オブジェクトの <xref:System.Xml.XmlReaderSettings.Schemas%2A> プロパティに追加することによって、XML ドキュメントを検証します。</span><span class="sxs-lookup"><span data-stu-id="08144-179">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="08144-180">次に、<xref:System.Xml.XmlReaderSettings> オブジェクトを作成して、XML ドキュメントを検証するために、<xref:System.Xml.XmlReader.Create%2A> オブジェクトが <xref:System.Xml.XmlReader> クラスの <xref:System.Xml.XmlReader> メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="08144-180">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="08144-181"><xref:System.Xml.Schema.XmlSchemaSet> を利用して XML 文書を検証する方法については、「[XmlSchemaSet による XML スキーマ (XSD) 検証](xml-schema-xsd-validation-with-xmlschemaset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08144-181">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08144-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="08144-182">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="08144-183">スキーマ キャッシュとしての XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="08144-183">XmlSchemaSet as a Schema Cache</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="08144-184">XmlSchemaSet による XML スキーマ (XSD) 検証</span><span class="sxs-lookup"><span data-stu-id="08144-184">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](xml-schema-xsd-validation-with-xmlschemaset.md)
