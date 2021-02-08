---
description: 詳細については、「MsmqBindingElementBase」を参照してください。
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 3aa5ec2343d73798f1cf5e3c7d4b5a8282f97ac9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803179"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="5bcff-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="5bcff-103">MsmqBindingElementBase</span></span>

<span data-ttu-id="5bcff-104">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="5bcff-104">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bcff-105">構文</span><span class="sxs-lookup"><span data-stu-id="5bcff-105">Syntax</span></span>  
  
```csharp  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5bcff-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5bcff-106">Methods</span></span>  

 <span data-ttu-id="5bcff-107">MsmqBindingElementBase クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="5bcff-107">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5bcff-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5bcff-108">Properties</span></span>  

 <span data-ttu-id="5bcff-109">MsmqBindingElementBase クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="5bcff-109">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="5bcff-110">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="5bcff-110">CustomDeadLetterQueue</span></span>  

 <span data-ttu-id="5bcff-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="5bcff-111">Data type: string</span></span>  
  
 <span data-ttu-id="5bcff-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-113">アプリケーションごとの配信不能キューの場所が含まれている URI です。ここには、期限切れのメッセージや、転送または配信に失敗したメッセージが配置されます。</span><span class="sxs-lookup"><span data-stu-id="5bcff-113">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="5bcff-114">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="5bcff-114">DeadLetterQueue</span></span>  

 <span data-ttu-id="5bcff-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="5bcff-115">Data type: string</span></span>  
  
 <span data-ttu-id="5bcff-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-117">使用する配信不能キューの型を示す列挙型の値です。</span><span class="sxs-lookup"><span data-stu-id="5bcff-117">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="5bcff-118">Durable</span><span class="sxs-lookup"><span data-stu-id="5bcff-118">Durable</span></span>  

 <span data-ttu-id="5bcff-119">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="5bcff-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="5bcff-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-121">このバインディングによって処理されるメッセージが永続的なものか不安定なものかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="5bcff-121">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="5bcff-122">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="5bcff-122">ExactlyOnce</span></span>  

 <span data-ttu-id="5bcff-123">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="5bcff-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="5bcff-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-125">このバインディングで処理されるメッセージが正確に 1 回だけ受信されるかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="5bcff-125">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="5bcff-126">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="5bcff-126">MaxRetryCycles</span></span>  

 <span data-ttu-id="5bcff-127">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="5bcff-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="5bcff-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-129">受信アプリケーションにメッセージを配信する再試行サイクルの最大数です。</span><span class="sxs-lookup"><span data-stu-id="5bcff-129">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="5bcff-130">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="5bcff-130">ReceiveErrorHandling</span></span>  

 <span data-ttu-id="5bcff-131">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="5bcff-131">Data type: string</span></span>  
  
 <span data-ttu-id="5bcff-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-133">有害メッセージの処理の設定です。</span><span class="sxs-lookup"><span data-stu-id="5bcff-133">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="5bcff-134">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="5bcff-134">ReceiveRetryCount</span></span>  

 <span data-ttu-id="5bcff-135">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="5bcff-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="5bcff-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-137">アプリケーション キューから読み取られるメッセージの即時再試行の最大回数です。</span><span class="sxs-lookup"><span data-stu-id="5bcff-137">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="5bcff-138">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="5bcff-138">RetryCycleDelay</span></span>  

 <span data-ttu-id="5bcff-139">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="5bcff-139">Data type: datetime</span></span>  
  
 <span data-ttu-id="5bcff-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-141">すぐに配信できなかったメッセージを配信しようとするときの、再試行サイクルの時間遅延を示す値です。</span><span class="sxs-lookup"><span data-stu-id="5bcff-141">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="5bcff-142">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="5bcff-142">TimeToLive</span></span>  

 <span data-ttu-id="5bcff-143">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="5bcff-143">Data type: datetime</span></span>  
  
 <span data-ttu-id="5bcff-144">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-145">このバインディングで処理されるメッセージの期限が切れるまで、メッセージをキュー内で保持する時間です。</span><span class="sxs-lookup"><span data-stu-id="5bcff-145">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="5bcff-146">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="5bcff-146">UseMsmqTracing</span></span>  

 <span data-ttu-id="5bcff-147">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="5bcff-147">Data type: boolean</span></span>  
  
 <span data-ttu-id="5bcff-148">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-149">このバインディングにより処理されるメッセージをトレースするかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="5bcff-149">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="5bcff-150">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="5bcff-150">UseSourceJournal</span></span>  

 <span data-ttu-id="5bcff-151">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="5bcff-151">Data type: boolean</span></span>  
  
 <span data-ttu-id="5bcff-152">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5bcff-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5bcff-153">このバインディングにより処理されるメッセージのコピーをソース ジャーナル キューに保存するかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="5bcff-153">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bcff-154">要件</span><span class="sxs-lookup"><span data-stu-id="5bcff-154">Requirements</span></span>  
  
|<span data-ttu-id="5bcff-155">MOF</span><span class="sxs-lookup"><span data-stu-id="5bcff-155">MOF</span></span>|<span data-ttu-id="5bcff-156">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="5bcff-156">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5bcff-157">名前空間</span><span class="sxs-lookup"><span data-stu-id="5bcff-157">Namespace</span></span>|<span data-ttu-id="5bcff-158">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="5bcff-158">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bcff-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bcff-159">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
