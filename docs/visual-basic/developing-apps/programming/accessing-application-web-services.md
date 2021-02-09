---
description: '詳細情報: アプリケーションの Web サービスへのアクセス (Visual Basic)'
title: アプリケーションの Web サービスへのアクセス
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: 4efd35ed7c8f4251a749b85a45242af299a51e6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797888"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="eab66-103">アプリケーションの Web サービスへのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eab66-103">Accessing Application Web Services (Visual Basic)</span></span>

<span data-ttu-id="eab66-104">`My.WebServices` オブジェクトは、現在のプロジェクトにより参照されている各 Web サービスのインスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="eab66-104">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="eab66-105">各インスタンスは要求に応じてインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="eab66-105">Each instance is instantiated on demand.</span></span> <span data-ttu-id="eab66-106">これらの Web サービスには `My.WebServices` オブジェクトのプロパティを介してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="eab66-106">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="eab66-107">プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じになります。</span><span class="sxs-lookup"><span data-stu-id="eab66-107">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="eab66-108"><xref:System.Web.Services.Protocols.SoapHttpClientProtocol> から継承されたクラスはすべて Web サービスです。</span><span class="sxs-lookup"><span data-stu-id="eab66-108">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>

## <a name="tasks"></a><span data-ttu-id="eab66-109">タスク</span><span class="sxs-lookup"><span data-stu-id="eab66-109">Tasks</span></span>

<span data-ttu-id="eab66-110">次の表は、アプリケーションにより参照される Web サービスにアクセスする方法を一覧にしたものです。</span><span class="sxs-lookup"><span data-stu-id="eab66-110">The following table lists possible ways to access Web services referenced by an application.</span></span>

|<span data-ttu-id="eab66-111">終了</span><span class="sxs-lookup"><span data-stu-id="eab66-111">To</span></span>|<span data-ttu-id="eab66-112">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="eab66-112">See</span></span>|
|---|---|
|<span data-ttu-id="eab66-113">Web サービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="eab66-113">Call a Web service</span></span>|[<span data-ttu-id="eab66-114">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="eab66-114">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)|
|<span data-ttu-id="eab66-115">Web サービスを非同期で呼び出し、完了時にイベントを処理する</span><span class="sxs-lookup"><span data-stu-id="eab66-115">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="eab66-116">方法: Web サービスを非同期で呼び出す</span><span class="sxs-lookup"><span data-stu-id="eab66-116">How to: Call a Web Service Asynchronously</span></span>](how-to-call-a-web-service-asynchronously.md)|

## <a name="see-also"></a><span data-ttu-id="eab66-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="eab66-117">See also</span></span>

- [<span data-ttu-id="eab66-118">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="eab66-118">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
