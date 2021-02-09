---
description: '詳細情報: DataView'
title: DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: dfc57c2ff9108f71d4dfa75447afc5f0ee8b9e54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652563"
---
# <a name="dataviews"></a><span data-ttu-id="39458-103">DataView</span><span class="sxs-lookup"><span data-stu-id="39458-103">DataViews</span></span>

<span data-ttu-id="39458-104"><xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータのさまざまなビューを作成できます。この機能は、データ連結アプリケーションで頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="39458-104">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="39458-105">**DataView** を使用すると、さまざまな並べ替え順序を使用してテーブルのデータを公開したり、行の状態やフィルター式に基づいてデータをフィルター処理したりできます。</span><span class="sxs-lookup"><span data-stu-id="39458-105">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>

 <span data-ttu-id="39458-106">**DataView** では、基になる **DataTable** のデータの動的ビューが作成されます。ビューの内容、順序、メンバーシップには、変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="39458-106">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="39458-107">これは、**DataTable** の **Select** メソッドとは異なります。このメソッドでは、特定のフィルターまたは並べ替え順序ごとにテーブルから <xref:System.Data.DataRow> の配列が戻されます。戻される配列の内容には、基になるテーブルの変更内容が反映されていますが、メンバーシップと順序は静的です。</span><span class="sxs-lookup"><span data-stu-id="39458-107">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: this content reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="39458-108">**DataView** は動的機能を備えているため、データ連結アプリケーションにとって理想的なオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="39458-108">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>

 <span data-ttu-id="39458-109">**DataView** は、1 つのデータ セットの動的ビューです。データベースのビューと同様に、この動的ビューには、さまざまな並べ替え順序やフィルター処理条件を適用できます。</span><span class="sxs-lookup"><span data-stu-id="39458-109">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="39458-110">ただし、データベース ビューとは異なり、**DataView** は、テーブルとしては処理できず、結合テーブルのビューも作成できません。</span><span class="sxs-lookup"><span data-stu-id="39458-110">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="39458-111">また、ソース テーブルに存在する列を除外したり、ソース テーブルに存在しない列 (計算列など) を追加したりすることもできません。</span><span class="sxs-lookup"><span data-stu-id="39458-111">You also cannot exclude columns that exist in the source table or append columns that do not exist in the source table, such as computational columns.</span></span>

 <span data-ttu-id="39458-112">**DataSet** のすべてのテーブルのビュー設定を管理するには、<xref:System.Data.DataView.DataViewManager%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="39458-112">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="39458-113">**DataViewManager** を使用すると、各テーブルの既定のビュー設定を簡単に管理できます。</span><span class="sxs-lookup"><span data-stu-id="39458-113">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="39458-114">**DataSet** の複数のテーブルにコントロールをバインドするときは、**DataViewManager** にバインドするのが最善の方法です。</span><span class="sxs-lookup"><span data-stu-id="39458-114">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="39458-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="39458-115">In This Section</span></span>

 <span data-ttu-id="39458-116">「[DataView の作成](creating-a-dataview.md)」では、**DataTable** の **DataView** の作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39458-116">[Creating a DataView](creating-a-dataview.md) Describes how to create a **DataView** for a **DataTable**.</span></span>

 <span data-ttu-id="39458-117">「[データの並べ替えとフィルター処理](sorting-and-filtering-data.md)」では、特定のフィルター条件を満たすデータ行のサブセットを返すか、または特定の並べ替え順序でデータを返すように、**DataView** のプロパティを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39458-117">[Sorting and Filtering Data](sorting-and-filtering-data.md) Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>

 <span data-ttu-id="39458-118">「[DataRow および DataRowView](datarows-and-datarowviews.md)」では、**DataView** によって公開されるデータへのアクセス方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39458-118">[DataRows and DataRowViews](datarows-and-datarowviews.md) Describes how to access the data exposed by the **DataView**.</span></span>

 <span data-ttu-id="39458-119">「[行の検索](finding-rows.md)」では、**DataView** での特定の行の検索方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39458-119">[Finding Rows](finding-rows.md) Describes how to find a particular row in a **DataView**.</span></span>

 <span data-ttu-id="39458-120">「[ChildView とリレーション](childviews-and-relations.md)」では、**DataView** を使用して親子のリレーションシップからデータ ビューを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39458-120">[ChildViews and Relations](childviews-and-relations.md) Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>

 <span data-ttu-id="39458-121">「[DataView の変更](modifying-dataviews.md)」では、**DataView** を使用して、基になる **DataTable** のデータを変更する方法について説明します。また、更新の有効化と無効化についても説明します。</span><span class="sxs-lookup"><span data-stu-id="39458-121">[Modifying DataViews](modifying-dataviews.md) Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>

 <span data-ttu-id="39458-122">「[DataView イベントの処理](handling-dataview-events.md)」では、**DataView** の内容または順序が更新されるときに、**ListChanged** イベントを使用して通知を受信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39458-122">[Handling DataView Events](handling-dataview-events.md) Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>

 <span data-ttu-id="39458-123">「[DataViews の管理](managing-dataviews.md)」では、**DataViewManager** を使用して **DataSet** の各テーブルの **DataView** 設定を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39458-123">[Managing DataViews](managing-dataviews.md) Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>

## <a name="related-sections"></a><span data-ttu-id="39458-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="39458-124">Related Sections</span></span>

 <span data-ttu-id="39458-125">[ASP.NET Web アプリケーション](/previous-versions/655cec97(v=vs.100))に関する記事では、ASP.NET アプリケーション、Web Forms、および Web サービスを作成する場合の概要と詳細なステップごとの手順を示します。</span><span class="sxs-lookup"><span data-stu-id="39458-125">[ASP.NET Web Applications](/previous-versions/655cec97(v=vs.100)) Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>

 <span data-ttu-id="39458-126">[Windows アプリケーション](/previous-versions/ms184421(v=vs.100))に関する記事では、Windows フォームおよびコンソール アプリケーションの操作に関する詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="39458-126">[Windows Applications](/previous-versions/ms184421(v=vs.100)) Provides detailed information about working with Windows Forms and console applications.</span></span>

 <span data-ttu-id="39458-127">「[DataSet、DataTable、および DataView](index.md)」では、**DataSet** オブジェクトと、それを使用してアプリケーション データを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39458-127">[DataSets, DataTables, and DataViews](index.md) Describes the **DataSet** object and how you can use it to manage application data.</span></span>

 <span data-ttu-id="39458-128">「[DataTable](datatables.md)」では、**DataTable** オブジェクトについて説明し、アプリケーション データを単独でまたは **DataSet** の一部として管理するために DataTable オブジェクトを使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="39458-128">[DataTables](datatables.md) Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>

 <span data-ttu-id="39458-129">「[ADO.NET](../index.md)」では、ADO.NET のアーキテクチャとコンポーネントについて説明し、ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39458-129">[ADO.NET](../index.md) Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>

## <a name="see-also"></a><span data-ttu-id="39458-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="39458-130">See also</span></span>

- [<span data-ttu-id="39458-131">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="39458-131">ADO.NET Overview</span></span>](../ado-net-overview.md)
