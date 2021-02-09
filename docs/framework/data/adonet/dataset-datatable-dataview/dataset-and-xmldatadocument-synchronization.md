---
description: '詳細情報: DataSet と XmlDataDocument の同期'
title: DataSet と XmlDataDocument の同期
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: c3bb1af305dfc319cb2c4783f4e4edc108e9d737
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739561"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="2d07c-103">DataSet と XmlDataDocument の同期</span><span class="sxs-lookup"><span data-stu-id="2d07c-103">DataSet and XmlDataDocument Synchronization</span></span>

<span data-ttu-id="2d07c-104">ADO.NET の <xref:System.Data.DataSet> には、データのリレーショナル表現があります。</span><span class="sxs-lookup"><span data-stu-id="2d07c-104">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="2d07c-105">階層データにアクセスするには、.NET Framework で使用できる XML クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-105">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="2d07c-106">従来、この 2 つのデータ表現は個別に使用されていました。</span><span class="sxs-lookup"><span data-stu-id="2d07c-106">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="2d07c-107">.NET Framework では、データのリレーショナル表現と階層表現の両方へリアルタイムに同期的な方法でアクセスできます。リレーショナル表現にアクセスするには **DataSet** オブジェクトを使用します。階層表現にアクセスするには <xref:System.Xml.XmlDataDocument> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-107">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="2d07c-108">**DataSet** が **XmlDataDocument** と同期されているときは、両方のオブジェクトが 1 つのデータ セットで動作しています。</span><span class="sxs-lookup"><span data-stu-id="2d07c-108">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="2d07c-109">つまり **DataSet** が変更されると、その変更内容が **XmlDataDocument** に反映されます。この逆の反映も行われます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-109">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="2d07c-110">**DataSet** と **XmlDataDocument** の間のリレーションシップにより、1 つのアプリケーションから 1 つのデータ セットを使用して、**DataSet** の周囲に構築されたサービス スイート全体 (Web Forms、Windows フォーム コントロール、Visual Studio、.NET デザイナーなど) にアクセスしたり、XML サービス スイート (XSL (Extensible Stylesheet Language)、XSLT (XSL Transformations)、XPath (XML Path Language) など) にアクセスしたりできる優れた柔軟性が実現されます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-110">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="2d07c-111">アプリケーションでアクセス対象とするサービス セットを選択する必要はありません。どちらのサービス セットにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-111">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="2d07c-112">**DataSet** を **XmlDataDocument** と同期する方法は数種類あります。</span><span class="sxs-lookup"><span data-stu-id="2d07c-112">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="2d07c-113">次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-113">You can:</span></span>  
  
- <span data-ttu-id="2d07c-114">**DataSet** にスキーマ (リレーショナル構造) とデータを読み込み、この DataSet を新しい **XmlDataDocument** と同期します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-114">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="2d07c-115">この方法では、既存のリレーショナル データの階層ビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-115">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="2d07c-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-116">For example:</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
- <span data-ttu-id="2d07c-117">**DataSet** にスキーマだけを読み込み (厳密に型指定された **DataSet** など)、それを **XmlDataDocument** と同期します。次に、XML ドキュメントから **XmlDataDocument** を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-117">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="2d07c-118">この方法では、既存の階層データのリレーショナル ビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-118">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="2d07c-119">**DataSet** スキーマのテーブル名と列名が、同期をとる XML 要素の名前と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d07c-119">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="2d07c-120">この名前の一致では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-120">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="2d07c-121">**DataSet** のスキーマが一致する必要があるのは、リレーショナル ビューで公開する XML 要素だけです。</span><span class="sxs-lookup"><span data-stu-id="2d07c-121">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="2d07c-122">つまり、このドキュメント上に非常に大きい XML ドキュメントと非常に小さなリレーショナル ウィンドウを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-122">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="2d07c-123">**DataSet** で XML ドキュメントの一部だけが公開される場合でも、**XmlDataDocument** では XML ドキュメント全体が保持されます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-123">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="2d07c-124">(これの詳しい例については、「[Dataset と XmlDataDocument の同期](synchronizing-a-dataset-with-an-xmldatadocument.md)」をご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="2d07c-124">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="2d07c-125">次のコード例では、**DataSet** を作成してそのスキーマを読み込み、**XmlDataDocument** と同期する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-125">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="2d07c-126">**DataSet** スキーマが一致する必要があるのは、**XmlDataDocument** の中で **DataSet** を使用して公開する要素だけであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2d07c-126">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     <span data-ttu-id="2d07c-127">データが含まれる **DataSet** と同期されている **XmlDataDocument** を読み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="2d07c-127">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="2d07c-128">読み込もうとすると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-128">An exception will be thrown.</span></span>  
  
- <span data-ttu-id="2d07c-129">新しい **XmlDataDocument** を作成して、XML ドキュメントからこの XmlDataDocument を読み込みます。次に、**XmlDataDocument** の **DataSet** プロパティを使用してデータのリレーショナル ビューにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2d07c-129">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="2d07c-130">**DataSet** を使用して **XmlDataDocument** のデータを表示するには、**DataSet** のスキーマを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d07c-130">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="2d07c-131">この場合も、**DataSet** スキーマのテーブル名と列名が、同期をとる XML 要素の名前と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d07c-131">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="2d07c-132">この名前の一致では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-132">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="2d07c-133">次のコード例では、**XmlDataDocument** のデータのリレーショナル ビューにアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-133">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 <span data-ttu-id="2d07c-134">**XmlDataDocument** を **DataSet** と同期するもう 1 つの利点は、XML ドキュメントが完全に保持されることです。</span><span class="sxs-lookup"><span data-stu-id="2d07c-134">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="2d07c-135">**ReadXml** を使用して XML ドキュメントのデータを **DataSet** に格納すると、**WriteXml** を使用してデータが XML ドキュメントとして書き込まれるときに、この XML ドキュメントと元の XML ドキュメントが大幅に異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2d07c-135">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="2d07c-136">これは、**DataSet** では XML ドキュメントから読み込んだ空白などの書式設定や、要素順序などの階層情報が維持されないためです。</span><span class="sxs-lookup"><span data-stu-id="2d07c-136">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="2d07c-137">**DataSet** には、XML ドキュメントで無視された要素も含まれていません。これは、これらの要素が **Dataset** のスキーマに一致しないためです。</span><span class="sxs-lookup"><span data-stu-id="2d07c-137">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="2d07c-138">**XmlDataDocument** を **DataSet** と同期することで、元の XML ドキュメントの書式設定要素や階層要素の構造が **XmlDataDocument** で維持され、**DataSet** には **DataSet** に適切なデータおよびスキーマ情報だけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-138">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="2d07c-139">**DataSet** を **XmlDataDocument** と同期する場合、<xref:System.Data.DataRelation> オブジェクトが入れ子かどうかによって同期結果が異なります。</span><span class="sxs-lookup"><span data-stu-id="2d07c-139">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="2d07c-140">詳しくは、「[DataRelation の入れ子化](nesting-datarelations.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2d07c-140">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d07c-141">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2d07c-141">In This Section</span></span>  

 [<span data-ttu-id="2d07c-142">DataSet と XmlDataDocument の同期</span><span class="sxs-lookup"><span data-stu-id="2d07c-142">Synchronizing a DataSet with an XmlDataDocument</span></span>](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="2d07c-143">最小限のスキーマが含まれており、厳密に型指定された **DataSet** を **XmlDataDocument** と同期させる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-143">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="2d07c-144">DataSet に対する XPath クエリの実行</span><span class="sxs-lookup"><span data-stu-id="2d07c-144">Performing an XPath Query on a DataSet</span></span>](performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="2d07c-145">**DataSet** の内容に対して XPath クエリを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-145">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="2d07c-146">DataSet への XSLT 変換の適用</span><span class="sxs-lookup"><span data-stu-id="2d07c-146">Applying an XSLT Transform to a DataSet</span></span>](applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="2d07c-147">**DataSet** の内容に XSLT 変換を適用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-147">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2d07c-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d07c-148">Related Sections</span></span>  

 [<span data-ttu-id="2d07c-149">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="2d07c-149">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="2d07c-150">**DataSet** の内容を XML データとして読み込んで永続化する方法など、**DataSet** でデータ ソースとして XML と対話する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-150">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="2d07c-151">DataRelation の入れ子化</span><span class="sxs-lookup"><span data-stu-id="2d07c-151">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="2d07c-152">**DataSet** の内容を XML データとして表現する場合における、入れ子になった **DataRelation** オブジェクトの重要性について説明します。また、このようなリレーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-152">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="2d07c-153">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="2d07c-153">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="2d07c-154">**DataSet** について説明し、DataSet を使用したアプリケーション データの管理方法と、DataSet を使用したデータ ソース (リレーショナル データベースや XML など) との対話方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d07c-154">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="2d07c-155">**XmlDataDocument** クラスに関するリファレンス情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d07c-155">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d07c-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d07c-156">See also</span></span>

- [<span data-ttu-id="2d07c-157">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="2d07c-157">ADO.NET Overview</span></span>](../ado-net-overview.md)
