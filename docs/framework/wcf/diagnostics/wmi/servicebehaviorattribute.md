---
description: '詳細情報: ServiceBehaviorAttribute'
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: 57ffa9103523618db752b3be6d43bb16603d1728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715575"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="c3746-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="c3746-103">ServiceBehaviorAttribute</span></span>

<span data-ttu-id="c3746-104">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="c3746-104">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3746-105">構文</span><span class="sxs-lookup"><span data-stu-id="c3746-105">Syntax</span></span>  
  
```csharp
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c3746-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c3746-106">Methods</span></span>  

 <span data-ttu-id="c3746-107">ServiceBehaviorAttribute クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="c3746-107">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c3746-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c3746-108">Properties</span></span>  

 <span data-ttu-id="c3746-109">ServiceBehaviorAttribute クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c3746-109">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="c3746-110">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="c3746-110">AutomaticSessionShutdown</span></span>  

 <span data-ttu-id="c3746-111">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c3746-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="c3746-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-113">クライアントが出力セッションを閉じるときにセッションを自動的に閉じるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c3746-113">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="c3746-114">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="c3746-114">ConcurrencyMode</span></span>  

 <span data-ttu-id="c3746-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c3746-115">Data type: string</span></span>  
<span data-ttu-id="c3746-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-117">サービスで、1 つのスレッド、複数のスレッド、または再入呼び出しをサポートするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c3746-117">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="c3746-118">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="c3746-118">ConfigurationName</span></span>  

 <span data-ttu-id="c3746-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c3746-119">Data type: string</span></span>  
  
 <span data-ttu-id="c3746-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-121">サービス構成の名前。</span><span class="sxs-lookup"><span data-stu-id="c3746-121">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="c3746-122">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="c3746-122">IgnoreExtensionDataObject</span></span>  

 <span data-ttu-id="c3746-123">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c3746-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="c3746-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-125">不明なシリアル化データをネットワークで送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3746-125">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="c3746-126">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="c3746-126">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="c3746-127">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c3746-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="c3746-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-129">デバッグの目的でクライアントに返される SOAP エラーの詳細に、マネージド例外情報を含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3746-129">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="c3746-130">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="c3746-130">InstanceContextMode</span></span>  

 <span data-ttu-id="c3746-131">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c3746-131">Data type: string</span></span>  
  
 <span data-ttu-id="c3746-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-133">新しいサービス オブジェクトを作成するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3746-133">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="c3746-134">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="c3746-134">MaxItemsInObjectGraph</span></span>  

 <span data-ttu-id="c3746-135">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="c3746-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="c3746-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-137">1 つのシリアル化されたオブジェクトで許可される項目の最大数。</span><span class="sxs-lookup"><span data-stu-id="c3746-137">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="c3746-138">名前</span><span class="sxs-lookup"><span data-stu-id="c3746-138">Name</span></span>  

 <span data-ttu-id="c3746-139">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c3746-139">Data type: string</span></span>  
  
 <span data-ttu-id="c3746-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-141">WSDL でのサービスの名前属性。</span><span class="sxs-lookup"><span data-stu-id="c3746-141">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="c3746-142">名前空間</span><span class="sxs-lookup"><span data-stu-id="c3746-142">Namespace</span></span>  

 <span data-ttu-id="c3746-143">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c3746-143">Data type: string</span></span>  
  
 <span data-ttu-id="c3746-144">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-145">WSDL でのサービスのターゲット名前空間。</span><span class="sxs-lookup"><span data-stu-id="c3746-145">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="c3746-146">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="c3746-146">ReleaseServiceInstanceOnTransactionComplete</span></span>  

 <span data-ttu-id="c3746-147">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c3746-147">Data type: boolean</span></span>  
  
 <span data-ttu-id="c3746-148">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-149">現在のトランザクションの完了時に、サービス オブジェクトをリサイクルするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3746-149">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="c3746-150">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="c3746-150">TransactionAutoCompleteOnSessionClose</span></span>  

 <span data-ttu-id="c3746-151">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c3746-151">Data type: boolean</span></span>  
  
 <span data-ttu-id="c3746-152">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-153">現在のセッションの終了時に、保留中のトランザクションを完了するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3746-153">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="c3746-154">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="c3746-154">TransactionIsolationLevel</span></span>  

 <span data-ttu-id="c3746-155">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c3746-155">Data type: string</span></span>  
  
 <span data-ttu-id="c3746-156">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-157">トランザクション分離レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3746-157">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="c3746-158">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="c3746-158">TransactionTimeout</span></span>  

 <span data-ttu-id="c3746-159">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="c3746-159">Data type: datetime</span></span>  
  
 <span data-ttu-id="c3746-160">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-160">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-161">トランザクションを完了しなければならない期間。</span><span class="sxs-lookup"><span data-stu-id="c3746-161">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="c3746-162">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="c3746-162">UseSynchronizationContext</span></span>  

 <span data-ttu-id="c3746-163">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c3746-163">Data type: boolean</span></span>  
  
 <span data-ttu-id="c3746-164">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-164">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-165">現在の同期コンテキストを使用してスレッドの実行を選択するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3746-165">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="c3746-166">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="c3746-166">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="c3746-167">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c3746-167">Data type: boolean</span></span>  
  
 <span data-ttu-id="c3746-168">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c3746-168">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3746-169">システムまたはアプリケーションで SOAP MustUnderstand ヘッダー処理を強制的に行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3746-169">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3746-170">要件</span><span class="sxs-lookup"><span data-stu-id="c3746-170">Requirements</span></span>  
  
|<span data-ttu-id="c3746-171">MOF</span><span class="sxs-lookup"><span data-stu-id="c3746-171">MOF</span></span>|<span data-ttu-id="c3746-172">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="c3746-172">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c3746-173">名前空間</span><span class="sxs-lookup"><span data-stu-id="c3746-173">Namespace</span></span>|<span data-ttu-id="c3746-174">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="c3746-174">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3746-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3746-175">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
