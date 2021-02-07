---
description: 詳細については、「カスタム追跡レコード」を参照してください。
title: カスタム追跡レコード
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 9d6988465fa3afca4302c86e0c2cad2778f2beae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742694"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="f6fa3-103">カスタム追跡レコード</span><span class="sxs-lookup"><span data-stu-id="f6fa3-103">Custom Tracking Records</span></span>

<span data-ttu-id="f6fa3-104">このトピックではカスタム追跡レコードを作成し、出力されたデータをレコードと一緒に読み込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f6fa3-104">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="f6fa3-105">カスタム追跡レコードの出力</span><span class="sxs-lookup"><span data-stu-id="f6fa3-105">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="f6fa3-106">次の例に示すように、カスタム追跡レコードはコード アクティビティから出力できます。</span><span class="sxs-lookup"><span data-stu-id="f6fa3-106">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="f6fa3-107"><xref:System.Activities.Tracking.CustomTrackingRecord> 上で <xref:System.Activities.NativeActivityContext.Track%2A> メソッドを呼び出すことで、`ActivityContext` をコード アクティビティに出力できます。</span><span class="sxs-lookup"><span data-stu-id="f6fa3-107">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6fa3-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6fa3-108">See also</span></span>

- <span data-ttu-id="f6fa3-109">[Windows Server App Fabric の監視](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f6fa3-109">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="f6fa3-110">[App Fabric を使用したアプリケーションの監視](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f6fa3-110">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
