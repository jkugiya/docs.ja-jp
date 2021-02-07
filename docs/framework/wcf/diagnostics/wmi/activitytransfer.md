---
description: 詳細については、「ActivityTransfer」を参照してください。
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 28f7d1c0d1056327313e7aa6be293eb325d8f265
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99758009"
---
# <a name="activitytransfer"></a><span data-ttu-id="6b8a3-103">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="6b8a3-103">ActivityTransfer</span></span>

<span data-ttu-id="6b8a3-104">アクティビティ転送イベント</span><span class="sxs-lookup"><span data-stu-id="6b8a3-104">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b8a3-105">構文</span><span class="sxs-lookup"><span data-stu-id="6b8a3-105">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6b8a3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="6b8a3-106">Methods</span></span>  

 <span data-ttu-id="6b8a3-107">ActivityTransfer クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="6b8a3-107">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6b8a3-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6b8a3-108">Properties</span></span>  

 <span data-ttu-id="6b8a3-109">ActivityTransfer クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="6b8a3-109">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="6b8a3-110">ActivityID</span><span class="sxs-lookup"><span data-stu-id="6b8a3-110">ActivityID</span></span>  
  
- <span data-ttu-id="6b8a3-111">データ型: object</span><span class="sxs-lookup"><span data-stu-id="6b8a3-111">Data type: object</span></span>  
    <span data-ttu-id="6b8a3-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6b8a3-112">Access type: Read-only</span></span>  
  
- <span data-ttu-id="6b8a3-113">アクティビティ ID</span><span class="sxs-lookup"><span data-stu-id="6b8a3-113">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="6b8a3-114">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="6b8a3-114">RelatedActivityID</span></span>  
  
- <span data-ttu-id="6b8a3-115">データ型: object</span><span class="sxs-lookup"><span data-stu-id="6b8a3-115">Data type: object</span></span>  
    <span data-ttu-id="6b8a3-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6b8a3-116">Access type: Read-only</span></span>  
  
- <span data-ttu-id="6b8a3-117">関連アクティビティ ID</span><span class="sxs-lookup"><span data-stu-id="6b8a3-117">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b8a3-118">要件</span><span class="sxs-lookup"><span data-stu-id="6b8a3-118">Requirements</span></span>  
  
|<span data-ttu-id="6b8a3-119">MOF</span><span class="sxs-lookup"><span data-stu-id="6b8a3-119">MOF</span></span>|<span data-ttu-id="6b8a3-120">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="6b8a3-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6b8a3-121">名前空間</span><span class="sxs-lookup"><span data-stu-id="6b8a3-121">Namespace</span></span>|<span data-ttu-id="6b8a3-122">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="6b8a3-122">Defined in root\ServiceModel.</span></span>|
