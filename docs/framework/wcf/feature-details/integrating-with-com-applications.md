---
description: 詳細については、「COM アプリケーションとの統合」を参照してください。
title: COM アプリケーションとの統合
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: 7afee4bed334d7f392b73773f0981022a59170fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802802"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="6ec64-103">COM アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="6ec64-103">Integrating with COM Applications</span></span>

<span data-ttu-id="6ec64-104">WCF サービスモニカーを使用すると、Windows Communication Foundation (WCF) サービスを既存のコードに直接統合できます。</span><span class="sxs-lookup"><span data-stu-id="6ec64-104">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="6ec64-105">サービス モニカーは Office VBA、Visual Basic 6.0、または Visual C++ 6.0 などの幅広い COM ベースの開発環境で使用可能です。</span><span class="sxs-lookup"><span data-stu-id="6ec64-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ec64-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6ec64-106">In This Section</span></span>  

 [<span data-ttu-id="6ec64-107">COM アプリケーションとの統合の概要</span><span class="sxs-lookup"><span data-stu-id="6ec64-107">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)  
 <span data-ttu-id="6ec64-108">統合プロセスの主要部分の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="6ec64-108">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="6ec64-109">方法: サービス モニカーを登録および構成する</span><span class="sxs-lookup"><span data-stu-id="6ec64-109">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="6ec64-110">COM アプリケーション内で WCF サービスモニカーを使用するには、必要な属性型を COM に登録し、必要なバインド構成を使用して COM アプリケーションとモニカーを構成します。</span><span class="sxs-lookup"><span data-stu-id="6ec64-110">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="6ec64-111">方法: 未登録で Windows Communication Foundation のサービス モニカーを使用する</span><span class="sxs-lookup"><span data-stu-id="6ec64-111">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="6ec64-112">WSDL (Web Services Definition Language) ドキュメントの形式で、または WS-MetadataExchange エンドポイントからコントラクトの定義を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6ec64-112">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="6ec64-113">方法: WSDL コントラクトと共にサービス モニカーを使用する</span><span class="sxs-lookup"><span data-stu-id="6ec64-113">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="6ec64-114">Wcf WSDL モニカーを使用して WCF サンプルを呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ec64-114">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="6ec64-115">方法: Metadata Exchange コントラクトと共にサービス モニカーを使用する</span><span class="sxs-lookup"><span data-stu-id="6ec64-115">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="6ec64-116">Mex エンドポイントを指定する WCF モニカーを使用して WCF サンプルを呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ec64-116">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="6ec64-117">方法: チャネルのセキュリティ資格情報を指定する</span><span class="sxs-lookup"><span data-stu-id="6ec64-117">How to: Specify Channel Security Credentials</span></span>](how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="6ec64-118">WCF サービスモニカーは、 `IChannelCredentials` チャネル資格情報を指定するためのさまざまな代替メソッドを許可するインターフェイスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6ec64-118">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6ec64-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ec64-119">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="6ec64-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ec64-120">See also</span></span>

- [<span data-ttu-id="6ec64-121">COM + アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="6ec64-121">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
