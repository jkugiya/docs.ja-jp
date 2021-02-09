---
description: '詳細情報: DataSet のイベント処理'
title: DataSet のイベント処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: a0000396c7c1e2762a5a2937f7979d917257facc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652368"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="cf3ce-103">DataSet のイベント処理</span><span class="sxs-lookup"><span data-stu-id="cf3ce-103">Handling DataSet Events</span></span>

<span data-ttu-id="cf3ce-104"><xref:System.Data.DataSet> オブジェクトには、 <xref:System.ComponentModel.MarshalByValueComponent.Disposed>、 <xref:System.Data.DataSet.Initialized>、 <xref:System.Data.DataSet.MergeFailed>という 3 つのイベントがあります。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-104">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="cf3ce-105">MergeFailed イベント</span><span class="sxs-lookup"><span data-stu-id="cf3ce-105">The MergeFailed Event</span></span>  

 <span data-ttu-id="cf3ce-106">`DataSet` オブジェクトのイベントの中で最も使用頻度が高いイベントは、マージしようとしている `MergeFailed`オブジェクトのスキーマが競合する場合に発生する `DataSet` です。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-106">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="cf3ce-107">この状況は、ターゲットとソースの <xref:System.Data.DataRow> が同じ主キー値を持ち、なおかつ、 <xref:System.Data.DataSet.EnforceConstraints%2A> プロパティが `true`に設定されている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-107">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="cf3ce-108">たとえば、マージ対象のテーブルの主キーの列が 2 つの `DataSet` オブジェクトのテーブル間で同じ場合、例外がスローされ、 `MergeFailed` イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-108">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="cf3ce-109"><xref:System.Data.MergeFailedEventArgs> イベントに渡される `MergeFailed` オブジェクトには、2 つの <xref:System.Data.MergeFailedEventArgs.Conflict%2A> オブジェクト間のスキーマで発生した競合を示す `DataSet` プロパティ、および競合が発生したテーブルの名前を示す <xref:System.Data.MergeFailedEventArgs.Table%2A> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-109">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="cf3ce-110">次のコードは、 `MergeFailed` イベントのイベント ハンドラーを追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-110">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a><span data-ttu-id="cf3ce-111">Initialized イベント</span><span class="sxs-lookup"><span data-stu-id="cf3ce-111">The Initialized Event</span></span>  

 <span data-ttu-id="cf3ce-112"><xref:System.Data.DataSet.Initialized> イベントは、 `DataSet` のコンストラクターによって `DataSet`の新しいインスタンスが初期化された後に発生します。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-112">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="cf3ce-113"><xref:System.Data.DataSet.IsInitialized%2A> プロパティは、 `true` の初期化が完了した場合に `DataSet` を返します。それ以外の場合は `false`を返します。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-113">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="cf3ce-114">この値は、 <xref:System.Data.DataSet.BeginInit%2A> の初期化を開始する `DataSet`メソッドによって <xref:System.Data.DataSet.IsInitialized%2A> が `false`に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-114">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="cf3ce-115">また、 <xref:System.Data.DataSet.EndInit%2A> の初期化を終了する `DataSet`メソッドによって `true`に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-115">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="cf3ce-116">これらのメソッドは、別のコンポーネントによって使用されている `DataSet` を初期化するために、Visual Studio のデザイン環境によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-116">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="cf3ce-117">通常、コード内で直接使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-117">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="cf3ce-118">Disposed イベント</span><span class="sxs-lookup"><span data-stu-id="cf3ce-118">The Disposed Event</span></span>  

 <span data-ttu-id="cf3ce-119">`DataSet` は、 <xref:System.ComponentModel.MarshalByValueComponent> メソッドおよび <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> イベントの両方を公開する <xref:System.ComponentModel.MarshalByValueComponent.Disposed> クラスから派生しています。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-119">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="cf3ce-120"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> イベントでは、コンポーネントが破棄されたことを伝えるイベントをリッスンするためのイベント ハンドラーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-120">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="cf3ce-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> メソッドが呼び出されたときにコードを実行したい場合は、`DataSet` の <xref:System.ComponentModel.MarshalByValueComponent.Disposed> イベントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-121">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="cf3ce-122"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> では、<xref:System.ComponentModel.MarshalByValueComponent> によって使用されたリソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-122"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf3ce-123">`DataSet` オブジェクトと `DataTable` オブジェクトでは、<xref:System.ComponentModel.MarshalByValueComponent> が継承されていて、リモート処理用の <xref:System.Runtime.Serialization.ISerializable> インターフェイスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-123">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="cf3ce-124">これらは、リモート処理ができる唯一の ADO.NET オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-124">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="cf3ce-125">詳しくは、「[.NET リモート処理](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-125">For more information, see [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span></span>  
  
 <span data-ttu-id="cf3ce-126">`DataSet` を操作するときに使用できる他のイベントについては、「[DataTable イベントの処理](handling-datatable-events.md)」および「[DataAdapter のイベント処理](../handling-dataadapter-events.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cf3ce-126">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](handling-datatable-events.md) and [Handling DataAdapter Events](../handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf3ce-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf3ce-127">See also</span></span>

- [<span data-ttu-id="cf3ce-128">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="cf3ce-128">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="cf3ce-129">[データの検証](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="cf3ce-129">[Validating Data](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span></span>
- [<span data-ttu-id="cf3ce-130">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="cf3ce-130">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="cf3ce-131">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="cf3ce-131">ADO.NET Overview</span></span>](../ado-net-overview.md)
