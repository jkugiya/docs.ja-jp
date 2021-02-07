---
description: 詳細情報:/の動作
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: fa9e403324afe818e247d1f751cce0ce7d5a6fb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757762"
---
# <a name="callbackbehavior"></a><span data-ttu-id="1ae7a-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="1ae7a-103">CallbackBehavior</span></span>

<span data-ttu-id="1ae7a-104">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="1ae7a-104">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae7a-105">構文</span><span class="sxs-lookup"><span data-stu-id="1ae7a-105">Syntax</span></span>  
  
```csharp
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1ae7a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="1ae7a-106">Methods</span></span>  

 <span data-ttu-id="1ae7a-107">CallbackBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="1ae7a-107">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1ae7a-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1ae7a-108">Properties</span></span>  

 <span data-ttu-id="1ae7a-109">CallbackBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="1ae7a-109">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="1ae7a-110">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="1ae7a-110">AutomaticSessionShutdown</span></span>  

 <span data-ttu-id="1ae7a-111">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1ae7a-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="1ae7a-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1ae7a-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ae7a-113">true の場合、サービスが双方向セッションを閉じると、セッションが自動的に閉じられます。</span><span class="sxs-lookup"><span data-stu-id="1ae7a-113">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="1ae7a-114">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="1ae7a-114">ConcurrencyMode</span></span>  

 <span data-ttu-id="1ae7a-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="1ae7a-115">Data type: string</span></span>  
<span data-ttu-id="1ae7a-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1ae7a-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ae7a-117">サービスが単一のスレッド、複数のスレッド、再入可能呼び出しのいずれをサポートするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ae7a-117">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="1ae7a-118">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="1ae7a-118">IgnoreExtensionDataObject</span></span>  

 <span data-ttu-id="1ae7a-119">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1ae7a-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="1ae7a-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1ae7a-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ae7a-121">不明なシリアル化データをネットワークで送信するかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="1ae7a-121">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="1ae7a-122">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="1ae7a-122">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="1ae7a-123">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1ae7a-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="1ae7a-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1ae7a-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ae7a-125">有効にした場合は、コールバックの例外に関する詳細情報が、サービスに戻されるエラーに添付されます。</span><span class="sxs-lookup"><span data-stu-id="1ae7a-125">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="1ae7a-126">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="1ae7a-126">MaxItemsInObjectGraph</span></span>  

 <span data-ttu-id="1ae7a-127">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1ae7a-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="1ae7a-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1ae7a-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ae7a-129">1 つのシリアル化されたオブジェクトで許可される項目の最大数。</span><span class="sxs-lookup"><span data-stu-id="1ae7a-129">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="1ae7a-130">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="1ae7a-130">UseSynchronizationContext</span></span>  

 <span data-ttu-id="1ae7a-131">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1ae7a-131">Data type: boolean</span></span>  
  
 <span data-ttu-id="1ae7a-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1ae7a-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ae7a-133">現在の同期コンテキストを使用して実行のスレッドを選択するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ae7a-133">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="1ae7a-134">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="1ae7a-134">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="1ae7a-135">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1ae7a-135">Data type: boolean</span></span>  
  
 <span data-ttu-id="1ae7a-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1ae7a-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ae7a-137">システムまたはアプリケーションで SOAP MustUnderstand ヘッダー処理を強制的に行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ae7a-137">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ae7a-138">要件</span><span class="sxs-lookup"><span data-stu-id="1ae7a-138">Requirements</span></span>  
  
|<span data-ttu-id="1ae7a-139">MOF</span><span class="sxs-lookup"><span data-stu-id="1ae7a-139">MOF</span></span>|<span data-ttu-id="1ae7a-140">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="1ae7a-140">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1ae7a-141">名前空間</span><span class="sxs-lookup"><span data-stu-id="1ae7a-141">Namespace</span></span>|<span data-ttu-id="1ae7a-142">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="1ae7a-142">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ae7a-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ae7a-143">See also</span></span>

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
