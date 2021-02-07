---
description: 詳細については、クエリのサポートに関するページを参照してください。
title: クエリのサポート
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 418e511e8b845653b9f3ec86d90c6cbfb25d5671
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755214"
---
# <a name="support-for-queries"></a><span data-ttu-id="15965-103">クエリのサポート</span><span class="sxs-lookup"><span data-stu-id="15965-103">Support for Queries</span></span>

<span data-ttu-id="15965-104">SQL Workflow Instance Store は、一連の既知のプロパティをストアに記録します。</span><span class="sxs-lookup"><span data-stu-id="15965-104">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="15965-105">ユーザーは、これらのプロパティに基づいてインスタンスのクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="15965-105">Users can query for instances based on these properties.</span></span> <span data-ttu-id="15965-106">これらの既知のプロパティの一部を次の一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="15965-106">The following list contains some of these well-known properties:</span></span>  
  
- <span data-ttu-id="15965-107">**サイト名。**</span><span class="sxs-lookup"><span data-stu-id="15965-107">**Site Name.**</span></span> <span data-ttu-id="15965-108">サービスが存在する Web サイトの名前。</span><span class="sxs-lookup"><span data-stu-id="15965-108">Name of the Web site that contains the service.</span></span>  
  
- <span data-ttu-id="15965-109">**相対アプリケーション パス:**</span><span class="sxs-lookup"><span data-stu-id="15965-109">**Relative Application Path.**</span></span> <span data-ttu-id="15965-110">Web サイトを基準としたアプリケーションの相対パス。</span><span class="sxs-lookup"><span data-stu-id="15965-110">Path of the application relative to the Web site.</span></span>  
  
- <span data-ttu-id="15965-111">**相対サービス パス:**</span><span class="sxs-lookup"><span data-stu-id="15965-111">**Relative Service Path.**</span></span> <span data-ttu-id="15965-112">アプリケーションを基準としたサービスの相対パス。</span><span class="sxs-lookup"><span data-stu-id="15965-112">Path of the service relative to the application.</span></span>  
  
- <span data-ttu-id="15965-113">**サービス名。**</span><span class="sxs-lookup"><span data-stu-id="15965-113">**Service Name.**</span></span> <span data-ttu-id="15965-114">サービスの名前。</span><span class="sxs-lookup"><span data-stu-id="15965-114">Name of the service.</span></span>  
  
- <span data-ttu-id="15965-115">**サービスの名前空間。**</span><span class="sxs-lookup"><span data-stu-id="15965-115">**Service Namespace.**</span></span> <span data-ttu-id="15965-116">サービスが使用する名前空間の名称。</span><span class="sxs-lookup"><span data-stu-id="15965-116">Name of the namespace that the service uses.</span></span>  
  
- <span data-ttu-id="15965-117">**現在のコンピューター:**</span><span class="sxs-lookup"><span data-stu-id="15965-117">**Current Machine.**</span></span>  
  
- <span data-ttu-id="15965-118">**最後のコンピューター**。</span><span class="sxs-lookup"><span data-stu-id="15965-118">**Last Machine**.</span></span> <span data-ttu-id="15965-119">ワークフロー サービスのインスタンスが最後に実行されたコンピューター。</span><span class="sxs-lookup"><span data-stu-id="15965-119">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15965-120">ワークフロー サービス ホストを使用する自己ホスト型のシナリオでは、最後の 4 つのプロパティにのみ値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="15965-120">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="15965-121">ワークフロー アプリケーション シナリオでは、最後のプロパティにのみ値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="15965-121">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="15965-122">ワークフロー ランタイムは、最初の 3 つのプロパティの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="15965-122">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="15965-123">ワークフローサービスホストは、 **Suspend Reason** プロパティの値を提供します。</span><span class="sxs-lookup"><span data-stu-id="15965-123">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="15965-124">SQL Workflow Instance Store 自体は、 **最後に更新されたコンピューター** プロパティの値を提供します。</span><span class="sxs-lookup"><span data-stu-id="15965-124">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="15965-125">また、SQL Workflow Instance Store の機能により、永続性データベースで値を格納したり、クエリで使用したりするカスタム プロパティを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="15965-125">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="15965-126">カスタムプロモーションの詳細については、「 [ストアの拡張機能](store-extensibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15965-126">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="15965-127">ビュー</span><span class="sxs-lookup"><span data-stu-id="15965-127">Views</span></span>  

 <span data-ttu-id="15965-128">インスタンス ストアには、次のビューがあります。</span><span class="sxs-lookup"><span data-stu-id="15965-128">The instance store contains the following views.</span></span> <span data-ttu-id="15965-129">詳細については、「 [永続性データベーススキーマ](persistence-database-schema.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15965-129">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="15965-130">Instances ビュー</span><span class="sxs-lookup"><span data-stu-id="15965-130">The Instances View</span></span>  

 <span data-ttu-id="15965-131">Instances ビューには、次のフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="15965-131">The Instances view contains the following fields:</span></span>  
  
1. <span data-ttu-id="15965-132">**Id**</span><span class="sxs-lookup"><span data-stu-id="15965-132">**Id**</span></span>  
  
2. <span data-ttu-id="15965-133">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="15965-133">**PendingTimer**</span></span>  
  
3. <span data-ttu-id="15965-134">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="15965-134">**CreationTime**</span></span>  
  
4. <span data-ttu-id="15965-135">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="15965-135">**LastUpdatedTime**</span></span>  
  
5. <span data-ttu-id="15965-136">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="15965-136">**ServiceDeploymentId**</span></span>  
  
6. <span data-ttu-id="15965-137">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="15965-137">**SuspensionExceptionName**</span></span>  
  
7. <span data-ttu-id="15965-138">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="15965-138">**SuspensionReason**</span></span>  
  
8. <span data-ttu-id="15965-139">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="15965-139">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="15965-140">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="15965-140">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="15965-141">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="15965-141">**LastMachine**</span></span>  
  
11. <span data-ttu-id="15965-142">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="15965-142">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="15965-143">**IsInitialized**</span><span class="sxs-lookup"><span data-stu-id="15965-143">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="15965-144">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="15965-144">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="15965-145">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="15965-145">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="15965-146">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="15965-146">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="15965-147">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="15965-147">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="15965-148">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="15965-148">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="15965-149">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="15965-149">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="15965-150">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="15965-150">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="15965-151">ServiceDeployments ビュー</span><span class="sxs-lookup"><span data-stu-id="15965-151">The ServiceDeployments view</span></span>  

 <span data-ttu-id="15965-152">ServiceDeployments ビューには、次のフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="15965-152">The ServiceDeployments view contains the following fields:</span></span>  
  
1. <span data-ttu-id="15965-153">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="15965-153">**SiteName**</span></span>  
  
2. <span data-ttu-id="15965-154">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="15965-154">**RelativeServicePath**</span></span>  
  
3. <span data-ttu-id="15965-155">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="15965-155">**RelativeApplicationPath**</span></span>  
  
4. <span data-ttu-id="15965-156">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="15965-156">**ServiceName**</span></span>  
  
5. <span data-ttu-id="15965-157">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="15965-157">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="15965-158">InstancePromotedProperties ビュー</span><span class="sxs-lookup"><span data-stu-id="15965-158">The InstancePromotedProperties view</span></span>  

 <span data-ttu-id="15965-159">InstancePromotedProperties ビューには、次のフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="15965-159">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="15965-160">昇格させたプロパティの詳細については、 [ストアの機能拡張](store-extensibility.md) に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="15965-160">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. <span data-ttu-id="15965-161">**InstanceId**</span><span class="sxs-lookup"><span data-stu-id="15965-161">**InstanceId**</span></span>  
  
2. <span data-ttu-id="15965-162">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="15965-162">**EncodingOption**</span></span>  
  
3. <span data-ttu-id="15965-163">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="15965-163">**PromotionName**</span></span>  
  
4. <span data-ttu-id="15965-164">**値 #** ( **Value1** から **Value64** までのフィールドの範囲)。</span><span class="sxs-lookup"><span data-stu-id="15965-164">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
