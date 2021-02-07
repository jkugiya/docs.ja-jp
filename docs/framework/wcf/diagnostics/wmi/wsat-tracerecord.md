---
description: '詳細については、次を参照してください: WSAT_TraceRecord'
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 67202c5d2910783c40b934d2da6108e6b514a728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756878"
---
# <a name="wsat_tracerecord"></a><span data-ttu-id="51531-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="51531-103">WSAT_TraceRecord</span></span>

<span data-ttu-id="51531-104">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="51531-104">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51531-105">構文</span><span class="sxs-lookup"><span data-stu-id="51531-105">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="51531-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="51531-106">Methods</span></span>  

 <span data-ttu-id="51531-107">WSAT_TraceRecord クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="51531-107">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="51531-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="51531-108">Properties</span></span>  

 <span data-ttu-id="51531-109">WSAT_TraceRecord クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="51531-109">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="51531-110">ActivityID</span><span class="sxs-lookup"><span data-stu-id="51531-110">ActivityID</span></span>  

 <span data-ttu-id="51531-111">データ型: object</span><span class="sxs-lookup"><span data-stu-id="51531-111">Data type: object</span></span>  
<span data-ttu-id="51531-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51531-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51531-113">トレース レコードのアクティビティ ID です。</span><span class="sxs-lookup"><span data-stu-id="51531-113">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="51531-114">EventID</span><span class="sxs-lookup"><span data-stu-id="51531-114">EventID</span></span>  

 <span data-ttu-id="51531-115">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="51531-115">Data type: sint32</span></span>  
<span data-ttu-id="51531-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51531-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51531-117">トレース レコードのイベント ID です。</span><span class="sxs-lookup"><span data-stu-id="51531-117">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="51531-118">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="51531-118">TraceRecord</span></span>  

 <span data-ttu-id="51531-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="51531-119">Data type: string</span></span>  
<span data-ttu-id="51531-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51531-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51531-121">トレース レコード</span><span class="sxs-lookup"><span data-stu-id="51531-121">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51531-122">要件</span><span class="sxs-lookup"><span data-stu-id="51531-122">Requirements</span></span>  
  
|<span data-ttu-id="51531-123">MOF</span><span class="sxs-lookup"><span data-stu-id="51531-123">MOF</span></span>|<span data-ttu-id="51531-124">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="51531-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="51531-125">名前空間</span><span class="sxs-lookup"><span data-stu-id="51531-125">Namespace</span></span>|<span data-ttu-id="51531-126">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="51531-126">Defined in root\ServiceModel</span></span>|
