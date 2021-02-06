---
description: 詳細については、「AJAX の統合と JSON のサポート」を参照してください。
title: AJAX の統合と JSON のサポート
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 13e52a3013e9c04f57d6303caf18fd23a41ebf25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643892"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="a6cf0-103">AJAX の統合と JSON のサポート</span><span class="sxs-lookup"><span data-stu-id="a6cf0-103">AJAX Integration and JSON Support</span></span>

<span data-ttu-id="a6cf0-104">ASP.NET (WCF) による非同期 JavaScript と XML (AJAX) および JavaScript Object Notation (JSON) データ形式のサポートにより Windows Communication Foundation、WCF サービスは AJAX クライアントに操作を公開できます。</span><span class="sxs-lookup"><span data-stu-id="a6cf0-104">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="a6cf0-105">AJAX クライアントは、JavaScript コードを実行し、HTTP 要求を使用してこれらの WCF サービスにアクセスする Web ページです。</span><span class="sxs-lookup"><span data-stu-id="a6cf0-105">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="a6cf0-106">このセクションのトピックでは、このサポートと実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6cf0-106">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="a6cf0-107">ASP.NET AJAX と ASP.NET 2.0 との統合の詳細については、「 [ASP.NET ajax の概要](/previous-versions/aspnet/bb398874(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6cf0-107">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](/previous-versions/aspnet/bb398874(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6cf0-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a6cf0-108">In This Section</span></span>  

 [<span data-ttu-id="a6cf0-109">ASP.NET AJAX 用の WCF サービスの作成</span><span class="sxs-lookup"><span data-stu-id="a6cf0-109">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="a6cf0-110">構成によって適切な AJAX エンドポイントを追加するか、またはカスタマイズされたサービスホストファクトリを使用して AJAX エンドポイントを自動的に構成するサービスホストを生成することによって、WCF サービスを AJAX クライアントに公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6cf0-110">Describes how a WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="a6cf0-111">ASP.NET を使用せずに WCF AJAX サービスを作成する方法</span><span class="sxs-lookup"><span data-stu-id="a6cf0-111">Creating WCF AJAX Services without ASP.NET</span></span>](creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="a6cf0-112">ASP.NET を使用せずに WCF サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6cf0-112">Describes how to create a WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="a6cf0-113">JSON などのデータ転送形式のサポート</span><span class="sxs-lookup"><span data-stu-id="a6cf0-113">Support for JSON and Other Data Transfer Formats</span></span>](support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="a6cf0-114">ASP.NET AJAX サービスとのメッセージングで、XML の代わりに一般に使用される JSON 形式のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a6cf0-114">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="a6cf0-115">方法: AJAX 対応 ASP.NET Web サービスを WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="a6cf0-115">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="a6cf0-116">AJAX 対応の ASP.NET Web サービスを WCF Web サービスに移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6cf0-116">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6cf0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6cf0-117">See also</span></span>

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="a6cf0-118">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="a6cf0-118">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
