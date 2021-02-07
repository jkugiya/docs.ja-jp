---
description: 詳細については、「WCF エラー処理」を参照してください。
title: WCF エラー処理
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 57f2c5078e0f73ff57eec79041cb7a2b2d42b498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668176"
---
# <a name="wcf-error-handling"></a><span data-ttu-id="8e80a-103">WCF エラー処理</span><span class="sxs-lookup"><span data-stu-id="8e80a-103">WCF Error Handling</span></span>

<span data-ttu-id="8e80a-104">WCF アプリケーションで発生したエラーは次の 3 つのグループのいずれかに属します。</span><span class="sxs-lookup"><span data-stu-id="8e80a-104">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1. <span data-ttu-id="8e80a-105">通信エラー</span><span class="sxs-lookup"><span data-stu-id="8e80a-105">Communication Errors</span></span>  
  
2. <span data-ttu-id="8e80a-106">プロキシ/チャネル エラー</span><span class="sxs-lookup"><span data-stu-id="8e80a-106">Proxy/Channel Errors</span></span>  
  
3. <span data-ttu-id="8e80a-107">アプリケーション エラー</span><span class="sxs-lookup"><span data-stu-id="8e80a-107">Application Errors</span></span>  
  
 <span data-ttu-id="8e80a-108">通信エラーは、ネットワークが利用できない場合、クライアントが無効なアドレスを使用している場合、またはサービス ホストが受信メッセージをリッスンしていない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="8e80a-108">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="8e80a-109">この種類のエラーは、クライアントに <xref:System.ServiceModel.CommunicationException> または <xref:System.ServiceModel.CommunicationException> 派生クラスとして返されます。</span><span class="sxs-lookup"><span data-stu-id="8e80a-109">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="8e80a-110">プロキシ/チャネル エラーは、チャネルまたはプロキシ自体に発生するエラーです。</span><span class="sxs-lookup"><span data-stu-id="8e80a-110">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="8e80a-111">この種類のエラーには、閉じられているプロキシまたはチャネルを使用しようとした、クライアントとサービス間にコントラクトの不一致が存在する、またはクライアントの資格情報がサービスによって拒否されたなどがあります。</span><span class="sxs-lookup"><span data-stu-id="8e80a-111">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="8e80a-112">このカテゴリには、ここに一覧を示せないほど多くのさまざまなエラーの種類があります。</span><span class="sxs-lookup"><span data-stu-id="8e80a-112">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="8e80a-113">この種類のエラーは、クライアントにそのままの状態で返されます (例外オブジェクトに対して変換は実行されません)。</span><span class="sxs-lookup"><span data-stu-id="8e80a-113">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="8e80a-114">アプリケーション エラーは、サービス操作の実行中に発生します。</span><span class="sxs-lookup"><span data-stu-id="8e80a-114">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="8e80a-115">この種類のエラーは、クライアントに <xref:System.ServiceModel.FaultException> または <xref:System.ServiceModel.FaultException%601> として送信されます。</span><span class="sxs-lookup"><span data-stu-id="8e80a-115">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="8e80a-116">WCF でのエラー処理は、次の 1 つ以上によって実行されます。</span><span class="sxs-lookup"><span data-stu-id="8e80a-116">Error handling in WCF is performed by one or more of the following:</span></span>  
  
- <span data-ttu-id="8e80a-117">スローされた例外の直接処理。</span><span class="sxs-lookup"><span data-stu-id="8e80a-117">Directly handling the exception thrown.</span></span> <span data-ttu-id="8e80a-118">これは、通信エラーとプロキシ/チャネル エラーに対してのみ行われます。</span><span class="sxs-lookup"><span data-stu-id="8e80a-118">This is only done for communication and proxy/channel errors.</span></span>  
  
- <span data-ttu-id="8e80a-119">エラー コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="8e80a-119">Using fault contracts</span></span>  
  
- <span data-ttu-id="8e80a-120"><xref:System.ServiceModel.Dispatcher.IErrorHandler> インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="8e80a-120">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
- <span data-ttu-id="8e80a-121"><xref:System.ServiceModel.ServiceHost> イベントの処理</span><span class="sxs-lookup"><span data-stu-id="8e80a-121">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="8e80a-122">エラー コントラクト</span><span class="sxs-lookup"><span data-stu-id="8e80a-122">Fault Contracts</span></span>  

 <span data-ttu-id="8e80a-123">エラー コントラクトでは、プラットフォームに依存しない方法で、サービス操作中に発生する可能性のあるエラーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="8e80a-123">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="8e80a-124">既定では、サービス操作内からスローされたすべての例外はクライアントに <xref:System.ServiceModel.FaultException> オブジェクトとして返されます。</span><span class="sxs-lookup"><span data-stu-id="8e80a-124">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="8e80a-125"><xref:System.ServiceModel.FaultException> オブジェクトには、情報がほとんど含まれません。</span><span class="sxs-lookup"><span data-stu-id="8e80a-125">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="8e80a-126">エラー コントラクトを定義し、エラーを <xref:System.ServiceModel.FaultException%601> として返すことにより、クライアントに送信される情報を制御できます。</span><span class="sxs-lookup"><span data-stu-id="8e80a-126">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> <span data-ttu-id="8e80a-127">詳細については、「 [コントラクトとサービスのエラーの指定と処理](specifying-and-handling-faults-in-contracts-and-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e80a-127">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="8e80a-128">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="8e80a-128">IErrorHandler</span></span>  

 <span data-ttu-id="8e80a-129"><xref:System.ServiceModel.Dispatcher.IErrorHandler> インターフェイスでは、WCF アプリケーションがエラーに応答する方法を詳細に制御できます。</span><span class="sxs-lookup"><span data-stu-id="8e80a-129">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="8e80a-130">クライアントに返されるエラー メッセージを制御し、ログ記録などのカスタム エラー処理を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8e80a-130">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  <span data-ttu-id="8e80a-131">詳細については <xref:System.ServiceModel.Dispatcher.IErrorHandler> 、[エラー処理およびレポート](./samples/extending-control-over-error-handling-and-reporting.md)に対する制御の拡張に関する情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e80a-131">For more information about <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](./samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="8e80a-132">ServiceHost イベント</span><span class="sxs-lookup"><span data-stu-id="8e80a-132">ServiceHost Events</span></span>  

 <span data-ttu-id="8e80a-133"><xref:System.ServiceModel.ServiceHost> クラスはサービスをホストし、エラー処理に必要になる可能性のあるいくつかのイベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="8e80a-133">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="8e80a-134">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8e80a-134">For example:</span></span>  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 <span data-ttu-id="8e80a-135">詳細については、<xref:System.ServiceModel.ServiceHost> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e80a-135">For more information, see <xref:System.ServiceModel.ServiceHost></span></span>
