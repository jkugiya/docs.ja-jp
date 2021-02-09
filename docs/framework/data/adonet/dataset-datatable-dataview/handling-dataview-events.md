---
description: '詳細情報: DataView イベントの処理'
title: DataView イベントの処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: d3e72adefa6b320d48b90d481a20644b62009cdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652316"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="f20bc-103">DataView イベントの処理</span><span class="sxs-lookup"><span data-stu-id="f20bc-103">Handling DataView Events</span></span>

<span data-ttu-id="f20bc-104"><xref:System.Data.DataView.ListChanged> の <xref:System.Data.DataView> イベントを使用して、ビューが更新されているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f20bc-104">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="f20bc-105">基になるテーブルの行の追加、削除、または変更や、このスキーマの列の追加または削除、親子のリレーションシップの変更など、これらの更新を行うとこのイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="f20bc-105">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="f20bc-106">さらに、現在表示されている行のリストが新しい並べ替え順序またはフィルターの適用により大幅に変更された場合、**ListChanged** イベントではそのことも通知されます。</span><span class="sxs-lookup"><span data-stu-id="f20bc-106">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="f20bc-107">**ListChanged** イベントは、<xref:System.ComponentModel> 名前空間の **ListChangedEventHandler** デリゲートを実装し、<xref:System.ComponentModel.ListChangedEventArgs> オブジェクトを入力として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f20bc-107">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="f20bc-108">発生した変更の内容を確認するには、**ListChangedEventArgs** オブジェクトの **ListChangedType** プロパティの <xref:System.ComponentModel.ListChangedType> 列挙値を使用します。</span><span class="sxs-lookup"><span data-stu-id="f20bc-108">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="f20bc-109">行の追加、削除、または移動による変更の場合、追加された行または移動された行の新しいインデックスと削除された行の古いインデックスには、**ListChangedEventArgs** オブジェクトの **NewIndex** プロパティを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f20bc-109">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="f20bc-110">移動された行の場合、移動前の古いインデックスにアクセスするには **ListChangedEventArgs** オブジェクトの **OldIndex** プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="f20bc-110">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="f20bc-111">**DataViewManager** では、さらにテーブルが追加または削除された場合に、または基になる **DataSet** の **Relations** コレクションが変更された場合に、そのことを通知するために **ListChanged** イベントが公開されます。</span><span class="sxs-lookup"><span data-stu-id="f20bc-111">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="f20bc-112">**ListChanged** イベント ハンドラーを追加する方法のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f20bc-112">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f20bc-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f20bc-113">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="f20bc-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="f20bc-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="f20bc-115">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="f20bc-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
