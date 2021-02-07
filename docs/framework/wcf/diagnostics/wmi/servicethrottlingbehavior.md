---
description: '詳細情報: ServiceThrottlingBehavior'
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: c4cf354c96340b910807bf7904e63a08dc01764b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715445"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="3cc17-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="3cc17-103">ServiceThrottlingBehavior</span></span>

<span data-ttu-id="3cc17-104">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="3cc17-104">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc17-105">構文</span><span class="sxs-lookup"><span data-stu-id="3cc17-105">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3cc17-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3cc17-106">Methods</span></span>  

 <span data-ttu-id="3cc17-107">ServiceThrottlingBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="3cc17-107">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3cc17-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3cc17-108">Properties</span></span>  

 <span data-ttu-id="3cc17-109">ServiceThrottlingBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3cc17-109">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="3cc17-110">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="3cc17-110">MaxConcurrentCalls</span></span>  

 <span data-ttu-id="3cc17-111">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="3cc17-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="3cc17-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3cc17-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3cc17-113">ServiceHost 内のすべてのディスパッチャー オブジェクトでアクティブに処理中のメッセージの最大数。</span><span class="sxs-lookup"><span data-stu-id="3cc17-113">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="3cc17-114">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="3cc17-114">MaxConcurrentInstances</span></span>  

 <span data-ttu-id="3cc17-115">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="3cc17-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="3cc17-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3cc17-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3cc17-117">一度に実行可能なサービス オブジェクトの最大数。</span><span class="sxs-lookup"><span data-stu-id="3cc17-117">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="3cc17-118">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="3cc17-118">MaxConcurrentSessions</span></span>  

 <span data-ttu-id="3cc17-119">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="3cc17-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="3cc17-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3cc17-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3cc17-121">ホストが一度に受け入れ可能なセッションの最大数。</span><span class="sxs-lookup"><span data-stu-id="3cc17-121">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc17-122">要件</span><span class="sxs-lookup"><span data-stu-id="3cc17-122">Requirements</span></span>  
  
|<span data-ttu-id="3cc17-123">MOF</span><span class="sxs-lookup"><span data-stu-id="3cc17-123">MOF</span></span>|<span data-ttu-id="3cc17-124">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="3cc17-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3cc17-125">名前空間</span><span class="sxs-lookup"><span data-stu-id="3cc17-125">Namespace</span></span>|<span data-ttu-id="3cc17-126">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="3cc17-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3cc17-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cc17-127">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
