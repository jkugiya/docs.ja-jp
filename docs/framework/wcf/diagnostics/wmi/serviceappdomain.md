---
description: '詳細情報: ServiceAppDomain'
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 1ac32b1fbd88518ffb260be9dd3ed2adb88d211c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715640"
---
# <a name="serviceappdomain"></a><span data-ttu-id="04c3e-103">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="04c3e-103">ServiceAppDomain</span></span>

<span data-ttu-id="04c3e-104">アプリケーション ドメインにサービスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="04c3e-104">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04c3e-105">構文</span><span class="sxs-lookup"><span data-stu-id="04c3e-105">Syntax</span></span>  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="04c3e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="04c3e-106">Methods</span></span>  

 <span data-ttu-id="04c3e-107">ServiceAppDomain クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="04c3e-107">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="04c3e-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="04c3e-108">Properties</span></span>  

 <span data-ttu-id="04c3e-109">ServiceAppDomain クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="04c3e-109">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="04c3e-110">ref</span><span class="sxs-lookup"><span data-stu-id="04c3e-110">ref</span></span>  

 <span data-ttu-id="04c3e-111">データ型 : Service</span><span class="sxs-lookup"><span data-stu-id="04c3e-111">Data type: Service</span></span>  
<span data-ttu-id="04c3e-112">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="04c3e-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="04c3e-113">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="04c3e-113">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04c3e-114">このアプリケーション ドメインのサービスです。</span><span class="sxs-lookup"><span data-stu-id="04c3e-114">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="04c3e-115">ref</span><span class="sxs-lookup"><span data-stu-id="04c3e-115">ref</span></span>  

 <span data-ttu-id="04c3e-116">データ型: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="04c3e-116">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="04c3e-117">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="04c3e-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="04c3e-118">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="04c3e-118">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04c3e-119">アプリケーション ドメインのプロパティが格納されています。</span><span class="sxs-lookup"><span data-stu-id="04c3e-119">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04c3e-120">要件</span><span class="sxs-lookup"><span data-stu-id="04c3e-120">Requirements</span></span>  
  
|<span data-ttu-id="04c3e-121">MOF</span><span class="sxs-lookup"><span data-stu-id="04c3e-121">MOF</span></span>|<span data-ttu-id="04c3e-122">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="04c3e-122">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="04c3e-123">名前空間</span><span class="sxs-lookup"><span data-stu-id="04c3e-123">Namespace</span></span>|<span data-ttu-id="04c3e-124">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="04c3e-124">Defined in root\ServiceModel</span></span>|
