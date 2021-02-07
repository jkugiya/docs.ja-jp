---
description: '詳細情報: ServiceToEndpointAssociation'
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 1ae2ce2bcc0b3494b00fffa750f3ca46d26fe08f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715341"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="0685d-103">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="0685d-103">ServiceToEndpointAssociation</span></span>

<span data-ttu-id="0685d-104">エンドポイントにサービスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="0685d-104">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0685d-105">構文</span><span class="sxs-lookup"><span data-stu-id="0685d-105">Syntax</span></span>  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0685d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="0685d-106">Methods</span></span>  

 <span data-ttu-id="0685d-107">ServiceToEndpointAssociation クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="0685d-107">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0685d-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0685d-108">Properties</span></span>  

 <span data-ttu-id="0685d-109">ServiceToEndpointAssociation クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="0685d-109">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="0685d-110">ref</span><span class="sxs-lookup"><span data-stu-id="0685d-110">ref</span></span>  

 <span data-ttu-id="0685d-111">データ型 : Service</span><span class="sxs-lookup"><span data-stu-id="0685d-111">Data type: Service</span></span>  
  
 <span data-ttu-id="0685d-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="0685d-112">Access type: Read-only</span></span>  
<span data-ttu-id="0685d-113">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="0685d-113">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="0685d-114">エンドポイントに関連付けられるサービス。</span><span class="sxs-lookup"><span data-stu-id="0685d-114">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="0685d-115">ref</span><span class="sxs-lookup"><span data-stu-id="0685d-115">ref</span></span>  

 <span data-ttu-id="0685d-116">データ型 : Endpoint</span><span class="sxs-lookup"><span data-stu-id="0685d-116">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="0685d-117">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="0685d-117">Access type: Read-only</span></span>  
<span data-ttu-id="0685d-118">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="0685d-118">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="0685d-119">サービスに関連付けられるエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="0685d-119">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0685d-120">要件</span><span class="sxs-lookup"><span data-stu-id="0685d-120">Requirements</span></span>  
  
|<span data-ttu-id="0685d-121">MOF</span><span class="sxs-lookup"><span data-stu-id="0685d-121">MOF</span></span>|<span data-ttu-id="0685d-122">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="0685d-122">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0685d-123">名前空間</span><span class="sxs-lookup"><span data-stu-id="0685d-123">Namespace</span></span>|<span data-ttu-id="0685d-124">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="0685d-124">Defined in root\ServiceModel</span></span>|
