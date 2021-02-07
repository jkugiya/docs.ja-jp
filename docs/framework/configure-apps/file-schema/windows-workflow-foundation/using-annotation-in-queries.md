---
description: 詳細については、「クエリでの注釈の使用」を参照してください。
title: クエリにおける注釈の使用
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 97423fe8ea7d90522a5f469adda5f645aa7e4485
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698025"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="afa6b-103">クエリにおける注釈の使用</span><span class="sxs-lookup"><span data-stu-id="afa6b-103">Using Annotation in Queries</span></span>

<span data-ttu-id="afa6b-104">注釈を使用すると、ビルド後に構成できる値を使用して、追跡レコードへのタグ付けを任意に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-104">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="afa6b-105">たとえば、複数のワークフローで複数の追跡レコードを "Mail Server" = = "Mail Server1" とタグ付けすることができます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-105">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="afa6b-106">こうすると、後で追跡レコードのクエリを実行するときに、このタグの付いたすべてのレコードを簡単に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-106">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="afa6b-107">注釈の追加</span><span class="sxs-lookup"><span data-stu-id="afa6b-107">Adding Annotations</span></span>  

 <span data-ttu-id="afa6b-108">次の例に示すように、追跡クエリに注釈を追加できます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-108">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
> <span data-ttu-id="afa6b-109">これらの追跡クエリ要素は、追跡プロファイルの作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-109">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="afa6b-110">追跡プロファイルは構成またはコードで作成できます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-110">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa6b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="afa6b-111">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](participants.md)
- [<span data-ttu-id="afa6b-112">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="afa6b-112">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="afa6b-113">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="afa6b-113">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
