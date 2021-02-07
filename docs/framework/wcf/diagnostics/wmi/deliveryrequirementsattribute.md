---
description: '詳細情報: DeliveryRequirementsAttribute'
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: ee27ada1c1fb447de3d7a108a4a285ca106e4e8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757502"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="135b8-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="135b8-103">DeliveryRequirementsAttribute</span></span>

<span data-ttu-id="135b8-104">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="135b8-104">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="135b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="135b8-105">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="135b8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="135b8-106">Methods</span></span>  

 <span data-ttu-id="135b8-107">DeliveryRequirementsAttribute クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="135b8-107">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="135b8-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="135b8-108">Properties</span></span>  

 <span data-ttu-id="135b8-109">DeliveryRequirementsAttribute クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="135b8-109">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="135b8-110">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="135b8-110">QueuedDeliveryRequirements</span></span>  

 <span data-ttu-id="135b8-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="135b8-111">Data type: string</span></span>  
  
 <span data-ttu-id="135b8-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="135b8-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="135b8-113">サービスのバインドがコントラクトをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="135b8-113">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="135b8-114">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="135b8-114">RequireOrderedDelivery</span></span>  

 <span data-ttu-id="135b8-115">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="135b8-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="135b8-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="135b8-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="135b8-117">バインディングが順序付きメッセージをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="135b8-117">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="135b8-118">TargetContract</span><span class="sxs-lookup"><span data-stu-id="135b8-118">TargetContract</span></span>  

 <span data-ttu-id="135b8-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="135b8-119">Data type: string</span></span>  
  
 <span data-ttu-id="135b8-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="135b8-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="135b8-121">適用先となるコントラクトです。</span><span class="sxs-lookup"><span data-stu-id="135b8-121">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="135b8-122">要件</span><span class="sxs-lookup"><span data-stu-id="135b8-122">Requirements</span></span>  
  
|<span data-ttu-id="135b8-123">MOF</span><span class="sxs-lookup"><span data-stu-id="135b8-123">MOF</span></span>|<span data-ttu-id="135b8-124">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="135b8-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="135b8-125">名前空間</span><span class="sxs-lookup"><span data-stu-id="135b8-125">Namespace</span></span>|<span data-ttu-id="135b8-126">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="135b8-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="135b8-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="135b8-127">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
