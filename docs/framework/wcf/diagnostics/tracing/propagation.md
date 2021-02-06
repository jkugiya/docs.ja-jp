---
description: '詳細情報: 伝達'
title: 伝達
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 43ecbf7b8db66f26accc058501730300a2891284
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635598"
---
# <a name="propagation"></a><span data-ttu-id="7e691-103">伝達</span><span class="sxs-lookup"><span data-stu-id="7e691-103">Propagation</span></span>

<span data-ttu-id="7e691-104">このトピックでは、Windows Communication Foundation (WCF) トレースモデルでのアクティビティの伝達について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e691-104">This topic describes activity propagation in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="7e691-105">伝達を使用したエンドポイント間でのアクティビティの関連付け</span><span class="sxs-lookup"><span data-stu-id="7e691-105">Using Propagation to Correlate Activities Across Endpoints</span></span>  

 <span data-ttu-id="7e691-106">伝達を使用することで、複数のアプリケーション エンドポイントについて、同じ処理単位 (要求など) のエラー トレースを直接関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="7e691-106">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="7e691-107">さまざまなエンドポイントで発生した同じ処理単位のエラーは、アプリケーション ドメインが異なる場合でも同じアクティビティとしてグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="7e691-107">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="7e691-108">これは、メッセージ ヘッダーで特定のアクティビティ ID を伝達することによって実現されます。</span><span class="sxs-lookup"><span data-stu-id="7e691-108">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="7e691-109">したがって、サーバーの内部エラーによってクライアントがタイムアウトした場合、これらのエラーは直接関係しているので、どちらも同じアクティビティに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e691-109">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="7e691-110">これを行うには、前述の例に示すように `ActivityTracing` 設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e691-110">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="7e691-111">さらに、すべてのエンドポイントで `propagateActivity` トレース ソースの `System.ServiceModel` 属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="7e691-111">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="7e691-112">アクティビティの伝達は構成可能な機能であり、WCF によって送信メッセージにヘッダーが追加されます。これには、TLS のアクティビティ ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e691-112">Activity propagation is a configurable capability that causes WCF to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="7e691-113">サーバー側の以降のトレースでこの ID を含めることにより、クライアントとサーバーのアクティビティを相互に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="7e691-113">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="7e691-114">伝達の定義</span><span class="sxs-lookup"><span data-stu-id="7e691-114">Propagation Definition</span></span>  

 <span data-ttu-id="7e691-115">次のすべての条件に該当する場合に、アクティビティ M の gAId がアクティビティ N に伝達されます。</span><span class="sxs-lookup"><span data-stu-id="7e691-115">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
- <span data-ttu-id="7e691-116">M に起因して N が作成された。</span><span class="sxs-lookup"><span data-stu-id="7e691-116">N is created because of M</span></span>  
  
- <span data-ttu-id="7e691-117">M の gAId を N が認識している。</span><span class="sxs-lookup"><span data-stu-id="7e691-117">M’s gAId is known to N</span></span>  
  
- <span data-ttu-id="7e691-118">N の gAId と M の gAId が同じである。</span><span class="sxs-lookup"><span data-stu-id="7e691-118">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="7e691-119">次の XML スキーマに示すように、gAId は ActivityId メッセージ ヘッダーによって伝達されます。</span><span class="sxs-lookup"><span data-stu-id="7e691-119">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="7e691-120">メッセージ ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7e691-120">The following is an example of the message header.</span></span>  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="7e691-121">伝達とアクティビティ境界</span><span class="sxs-lookup"><span data-stu-id="7e691-121">Propagation and Activity Boundaries</span></span>  

 <span data-ttu-id="7e691-122">エンドポイント間でアクティビティ ID が伝達されると、メッセージの受信側は、その (伝達された) アクティビティ ID を使用して Start トレースと Stop トレースを出力します。</span><span class="sxs-lookup"><span data-stu-id="7e691-122">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="7e691-123">したがって、各トレース ソースごとに、該当の gAId を持つ Start/Stop トレースが存在することになります。</span><span class="sxs-lookup"><span data-stu-id="7e691-123">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="7e691-124">複数のエンドポイントが同じプロセス内に存在し、同じトレース ソース名を使用している場合、同じ lAId (同じ gAId、同じトレース ソース、同じプロセス) を持つ複数の Start と Stop が作成されます。</span><span class="sxs-lookup"><span data-stu-id="7e691-124">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="7e691-125">同期</span><span class="sxs-lookup"><span data-stu-id="7e691-125">Synchronization</span></span>  

 <span data-ttu-id="7e691-126">異なるコンピューター上で実行されるエンドポイント間でイベントを同期するには、メッセージ内で伝達される ActivityId ヘッダーに CorrelationId を追加します。</span><span class="sxs-lookup"><span data-stu-id="7e691-126">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="7e691-127">ツールはこの ID を使用することにより、クロックにずれのあるコンピューター間でもイベントを同期できます。</span><span class="sxs-lookup"><span data-stu-id="7e691-127">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="7e691-128">具体的に言うと、サービス トレース ビューアー ツールは、エンドポイント間のメッセージ フローを示す際に、この ID を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e691-128">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e691-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e691-129">See also</span></span>

- [<span data-ttu-id="7e691-130">トレースの構成</span><span class="sxs-lookup"><span data-stu-id="7e691-130">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="7e691-131">サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="7e691-131">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="7e691-132">エンドツーエンドのトレースのシナリオ</span><span class="sxs-lookup"><span data-stu-id="7e691-132">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="7e691-133">サービス トレース ビューアー ツール (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="7e691-133">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
