---
description: '詳細情報: DataAdapter のイベント処理'
title: DataAdapter のイベント処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: 045a48ae545ad4354844dd451ff58618b760a9a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723947"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="968fe-103">DataAdapter のイベント処理</span><span class="sxs-lookup"><span data-stu-id="968fe-103">Handling DataAdapter Events</span></span>

<span data-ttu-id="968fe-104">ADO.NET <xref:System.Data.Common.DataAdapter> は、データ ソースのデータに対して行われた変更に応答するときに使用できる 3 つのイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="968fe-104">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="968fe-105">`DataAdapter` のイベントを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="968fe-105">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="968fe-106">event</span><span class="sxs-lookup"><span data-stu-id="968fe-106">Event</span></span>|<span data-ttu-id="968fe-107">説明</span><span class="sxs-lookup"><span data-stu-id="968fe-107">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="968fe-108">行に対する UPDATE、INSERT、または DELETE の各操作が (`Update` メソッドの 1 つの呼び出しによって) 開始しようとしています。</span><span class="sxs-lookup"><span data-stu-id="968fe-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="968fe-109">行に対する UPDATE、INSERT、DELETE の各操作が (`Update` メソッドの 1 つの呼び出しによって) 完了しました。</span><span class="sxs-lookup"><span data-stu-id="968fe-109">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="968fe-110">`Fill` 操作中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="968fe-110">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="968fe-111">RowUpdating と RowUpdated</span><span class="sxs-lookup"><span data-stu-id="968fe-111">RowUpdating and RowUpdated</span></span>  

 <span data-ttu-id="968fe-112">`RowUpdating` は、<xref:System.Data.DataSet> 側で生じた行に対する更新が、データ ソース側で処理される前に発生します。</span><span class="sxs-lookup"><span data-stu-id="968fe-112">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="968fe-113">`RowUpdated` は、`DataSet` 側で生じた行に対する更新が、データ ソース側で処理された後で発生します。</span><span class="sxs-lookup"><span data-stu-id="968fe-113">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="968fe-114">したがって、更新が始まる前に `RowUpdating` を使用して更新の動作を変更することで、更新発生時に行う追加の処理の提供、更新行への参照の保存、現在の更新のキャンセル、後で処理するバッチ処理のための更新スケジュールなどを提供できます。</span><span class="sxs-lookup"><span data-stu-id="968fe-114">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="968fe-115">`RowUpdated` は、更新中に発生するエラーや例外の応答に便利です。</span><span class="sxs-lookup"><span data-stu-id="968fe-115">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="968fe-116">`DataSet` にエラー情報や再試行ロジックなどを追加できます。</span><span class="sxs-lookup"><span data-stu-id="968fe-116">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="968fe-117">`RowUpdating` イベントおよび `RowUpdated` イベントに渡される <xref:System.Data.Common.RowUpdatingEventArgs> 引数および <xref:System.Data.Common.RowUpdatedEventArgs> 引数には、更新を実行するために使用される `Command` オブジェクトを参照する `Command` プロパティ、更新情報を格納する `DataRow` オブジェクトを参照する `Row` プロパティ、どのタイプの更新を実行するかを示す `StatementType` プロパティ、適用可能な場合は `TableMapping`、および、操作の `Status` などがあります。</span><span class="sxs-lookup"><span data-stu-id="968fe-117">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="968fe-118">`Status` プロパティを使用すると、操作中にエラーが発生したかどうかを確認したり、必要に応じて現在の行および結果行に対するアクションを制御したりできます。</span><span class="sxs-lookup"><span data-stu-id="968fe-118">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="968fe-119">イベントが発生すると、`Status` プロパティは `Continue` または `ErrorsOccurred` のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="968fe-119">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="968fe-120">次の表では、更新の後続のアクションを制御するために `Status` プロパティに設定できる値を示しています。</span><span class="sxs-lookup"><span data-stu-id="968fe-120">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="968fe-121">Status</span><span class="sxs-lookup"><span data-stu-id="968fe-121">Status</span></span>|<span data-ttu-id="968fe-122">説明</span><span class="sxs-lookup"><span data-stu-id="968fe-122">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="968fe-123">更新操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="968fe-123">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="968fe-124">更新操作を中止し、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="968fe-124">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="968fe-125">現在の行を無視し、更新操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="968fe-125">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="968fe-126">更新操作を中止しますが、例外はスローしません。</span><span class="sxs-lookup"><span data-stu-id="968fe-126">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="968fe-127">`Status` プロパティを `ErrorsOccurred` に設定すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="968fe-127">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="968fe-128">`Errors` プロパティを例外として設定することで、どの例外をスローするかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="968fe-128">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="968fe-129">`Status` に他の値を使用すると、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="968fe-129">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="968fe-130">`ContinueUpdateOnError` プロパティを使用して更新行に関するエラーを処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="968fe-130">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="968fe-131">`DataAdapter.ContinueUpdateOnError` を `true` に設定すると、行を更新した結果、例外がスローされようとしているときに、例外のテキストをその行の `RowError` 情報の中に格納し、例外をスローせずに処理を続行できます。</span><span class="sxs-lookup"><span data-stu-id="968fe-131">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="968fe-132">これにより、`Update` が完了した時点でエラーに応答できるようになります。これに対して `RowUpdated` イベントを使用すると、エラーが発生した時点でエラーに応答できます。</span><span class="sxs-lookup"><span data-stu-id="968fe-132">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="968fe-133">イベント ハンドラーを追加および削除する方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="968fe-133">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="968fe-134">`RowUpdating` イベント ハンドラーは、削除されたすべてのレコードのログをタイムスタンプと共に記録します。</span><span class="sxs-lookup"><span data-stu-id="968fe-134">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="968fe-135">`RowUpdated` イベント ハンドラーでは、`DataSet` の行の `RowError` プロパティにエラー情報を追加し、例外をスローせずに処理を続行します (`ContinueUpdateOnError` = `true` の場合と同等の動作です)。</span><span class="sxs-lookup"><span data-stu-id="968fe-135">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a><span data-ttu-id="968fe-136">FillError</span><span class="sxs-lookup"><span data-stu-id="968fe-136">FillError</span></span>  

 <span data-ttu-id="968fe-137">`DataAdapter` は、`FillError` 操作中にエラーが発生すると `Fill` イベントを発行します。</span><span class="sxs-lookup"><span data-stu-id="968fe-137">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="968fe-138">このタイプのエラーは通常、追加する行のデータを .NET Framework 型に変換したときに、有効桁を消失してしまった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="968fe-138">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="968fe-139">`Fill` 操作中にエラーが発生した場合、現在の行は `DataTable` に追加されません。</span><span class="sxs-lookup"><span data-stu-id="968fe-139">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="968fe-140">`FillError` イベントを使用すると、エラーを解決してその行を追加するか、または除外された行を無視し、`Fill` 操作を続行できます。</span><span class="sxs-lookup"><span data-stu-id="968fe-140">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="968fe-141">`FillErrorEventArgs` イベントに渡す `FillError` には、エラーに応答してエラーを解決できるいくつかのプロパティを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="968fe-141">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="968fe-142">`FillErrorEventArgs` オブジェクトのプロパティを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="968fe-142">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="968fe-143">プロパティ</span><span class="sxs-lookup"><span data-stu-id="968fe-143">Property</span></span>|<span data-ttu-id="968fe-144">説明</span><span class="sxs-lookup"><span data-stu-id="968fe-144">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="968fe-145">発生した `Exception`。</span><span class="sxs-lookup"><span data-stu-id="968fe-145">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="968fe-146">エラー発生時にデータを格納しようとしていた `DataTable` オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="968fe-146">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="968fe-147">エラー発生時に追加しようとしていた行の値を保持しているオブジェクトの配列。</span><span class="sxs-lookup"><span data-stu-id="968fe-147">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="968fe-148">`Values` 配列の序数参照は、追加しようとしていた行の列の序数参照に対応します。</span><span class="sxs-lookup"><span data-stu-id="968fe-148">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="968fe-149">たとえば、`Values[0]` は、行の第 1 列として追加しようとした値です。</span><span class="sxs-lookup"><span data-stu-id="968fe-149">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="968fe-150">例外をスローするかどうかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="968fe-150">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="968fe-151">`Continue` プロパティを `false` に設定すると、エラーが発生したときに現在の `Fill` 操作を停止し、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="968fe-151">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="968fe-152">`Continue` を `true` に設定すると、エラーに関係なく `Fill` 操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="968fe-152">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="968fe-153">次のコード例では、`FillError` の `DataAdapter` イベントにイベント ハンドラーを追加しています。</span><span class="sxs-lookup"><span data-stu-id="968fe-153">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="968fe-154">この `FillError` イベント コードの例は、有効桁の消失が発生したかどうかを確認し、例外に応答する機会を与えます。</span><span class="sxs-lookup"><span data-stu-id="968fe-154">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    myRow.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    myRow.RowError =
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="968fe-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="968fe-155">See also</span></span>

- [<span data-ttu-id="968fe-156">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="968fe-156">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="968fe-157">DataSet のイベント処理</span><span class="sxs-lookup"><span data-stu-id="968fe-157">Handling DataSet Events</span></span>](./dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="968fe-158">DataTable イベントの処理</span><span class="sxs-lookup"><span data-stu-id="968fe-158">Handling DataTable Events</span></span>](./dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="968fe-159">イベント</span><span class="sxs-lookup"><span data-stu-id="968fe-159">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="968fe-160">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="968fe-160">ADO.NET Overview</span></span>](ado-net-overview.md)
