---
description: 詳細については、「ServiceTimeoutsBehavior」を参照してください。
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 147d249af0e87bc41da93a4a31355da7053caaf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715419"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="a7f3f-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="a7f3f-103">ServiceTimeoutsBehavior</span></span>

<span data-ttu-id="a7f3f-104">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="a7f3f-104">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f3f-105">構文</span><span class="sxs-lookup"><span data-stu-id="a7f3f-105">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a7f3f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a7f3f-106">Methods</span></span>  

 <span data-ttu-id="a7f3f-107">ServiceTimeoutsBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="a7f3f-107">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a7f3f-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a7f3f-108">Properties</span></span>  

 <span data-ttu-id="a7f3f-109">ServiceTimeoutsBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="a7f3f-109">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="a7f3f-110">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="a7f3f-110">TransactionTimeout</span></span>  

 <span data-ttu-id="a7f3f-111">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="a7f3f-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="a7f3f-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a7f3f-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a7f3f-113">トランザクションを完了しなければならない期間。</span><span class="sxs-lookup"><span data-stu-id="a7f3f-113">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7f3f-114">要件</span><span class="sxs-lookup"><span data-stu-id="a7f3f-114">Requirements</span></span>  
  
|<span data-ttu-id="a7f3f-115">MOF</span><span class="sxs-lookup"><span data-stu-id="a7f3f-115">MOF</span></span>|<span data-ttu-id="a7f3f-116">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="a7f3f-116">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a7f3f-117">名前空間</span><span class="sxs-lookup"><span data-stu-id="a7f3f-117">Namespace</span></span>|<span data-ttu-id="a7f3f-118">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="a7f3f-118">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7f3f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7f3f-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
