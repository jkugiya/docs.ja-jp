---
description: 詳細については、使用する目的と標準に基づいた WCF への ASP.NET ウェブサービスの比較に関するページを参照してください。
title: 使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: debc20f3ab3e8e9f83641eaa7d3b52dabe82055c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743448"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a><span data-ttu-id="191ac-103">使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較</span><span class="sxs-lookup"><span data-stu-id="191ac-103">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>

<span data-ttu-id="191ac-104">ASP.NET Web サービスは、HTTP 上で SOAP (Simple Object Access Protocol) を使用してメッセージを送受信するアプリケーションを構築するために開発されました。</span><span class="sxs-lookup"><span data-stu-id="191ac-104">ASP.NET Web services was developed for building applications that send and receive messages by using the Simple Object Access Protocol (SOAP) over HTTP.</span></span> <span data-ttu-id="191ac-105">メッセージ構造は XML スキーマを使用して定義できます。また、.NET Framework オブジェクトに対するメッセージのシリアル化を容易にするツールも提供されています。</span><span class="sxs-lookup"><span data-stu-id="191ac-105">The structure of the messages can be defined using an XML Schema, and a tool is provided to facilitate serializing the messages to and from .NET Framework objects.</span></span> <span data-ttu-id="191ac-106">このテクノロジを使用すると、Web サービス記述言語 (WSDL) で Web サービスを記述するメタデータが自動で生成されます。また、WSDL から Web サービス用のクライアントを生成する別のツールも用意されています。</span><span class="sxs-lookup"><span data-stu-id="191ac-106">The technology can automatically generate metadata to describe Web services in the Web Services Description Language (WSDL), and a second tool is provided for generating clients for Web services from the WSDL.</span></span>  
  
 <span data-ttu-id="191ac-107">WCF は、.NET Framework アプリケーションが他のソフトウェアエンティティとメッセージを交換できるようにするためのものです。</span><span class="sxs-lookup"><span data-stu-id="191ac-107">WCF is for enabling .NET Framework applications to exchange messages with other software entities.</span></span> <span data-ttu-id="191ac-108">既定では SOAP が使用されますが、任意の形式のメッセージを使用でき、任意のトランスポート プロトコルを使用してメッセージを伝達できます。</span><span class="sxs-lookup"><span data-stu-id="191ac-108">SOAP is used by default, but the messages can be in any format, and conveyed by using any transport protocol.</span></span> <span data-ttu-id="191ac-109">メッセージ構造は XML スキーマを使用して定義できます。また、.NET Framework オブジェクトに対するメッセージをシリアル化するさまざまなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="191ac-109">The structure of the messages can be defined using an XML Schema, and there are various options for serializing the messages to and from .NET Framework objects.</span></span> <span data-ttu-id="191ac-110">WCF は、WSDL のテクノロジを使用して構築されたアプリケーションを記述するメタデータを自動的に生成できます。また、これらのアプリケーションのクライアントを WSDL から生成するためのツールも提供します。</span><span class="sxs-lookup"><span data-stu-id="191ac-110">WCF can automatically generate metadata to describe applications built using the technology in WSDL, and it also provides a tool for generating clients for those applications from the WSDL.</span></span>  
  
 <span data-ttu-id="191ac-111">ASP.NET ウェブサービスでサポートされる標準は、 [ASP.NET を使用して作成された XML Web サービスの利点](/previous-versions/dotnet/netframework-4.0/0859ebft(v=vs.100))に関するドキュメントに記載されています。</span><span class="sxs-lookup"><span data-stu-id="191ac-111">The standards supported by ASP.NET Web services are documented in [Benefits of XML Web Services Created Using ASP.NET](/previous-versions/dotnet/netframework-4.0/0859ebft(v=vs.100)).</span></span> <span data-ttu-id="191ac-112">WCF でサポートされる標準の詳細な一覧については、 [「System-Provided 相互運用性バインドでサポートされる Web サービスプロトコル](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="191ac-112">The more extensive list of standards supported by WCF are listed at [Web Services Protocols Supported by System-Provided Interoperability Bindings](web-services-protocols-supported-by-system-provided-interoperability-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="191ac-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="191ac-113">See also</span></span>

- [<span data-ttu-id="191ac-114">開発者の視点から見た ASP.NET Web サービスと WCF との比較</span><span class="sxs-lookup"><span data-stu-id="191ac-114">Comparing ASP.NET Web Services to WCF Based on Development</span></span>](comparing-aspnet-web-services-to-wcf-based-on-development.md)
