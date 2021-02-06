---
description: '詳細情報: 信頼できるセッション'
title: 信頼できるセッション
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 86df4ccf9c1fd52d162ad7272ece5591f0ca7482
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632881"
---
# <a name="reliable-sessions"></a><span data-ttu-id="f39cf-103">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="f39cf-103">Reliable Sessions</span></span>

<span data-ttu-id="f39cf-104">このセクションでは、Windows Communication Foundation (WCF) の信頼できるセッションについて説明します。これは、どのように使用されるか、どのように使用されるか、どのようなバインディング構成がサポートしているか、およびベストプラクティスに関するヒントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f39cf-104">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="f39cf-105">このセクションの重要なポイントと関連するトピックの詳細について、次の表にまとめます。</span><span class="sxs-lookup"><span data-stu-id="f39cf-105">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="f39cf-106">Reliable session WCF は、エンドポイント間で送信されるメッセージが SOAP またはトランスポート中継局間で転送されることを保証する機能を提供します。また、必要に応じて、送信された順序で1回だけ配信されます。</span><span class="sxs-lookup"><span data-stu-id="f39cf-106">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="f39cf-107">WCF アプリケーションで信頼できるセッションを使用するには、既定で、またはオプションとして、信頼できるセッションをサポートするシステム指定のバインディングのいずれかを使用するか、またはセッションをサポートする独自のカスタムバインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="f39cf-107">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f39cf-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f39cf-108">In This Section</span></span>

<span data-ttu-id="f39cf-109">[信頼できるセッションの概要](reliable-sessions-overview.md) 信頼できるセッション、使用するタイミング、信頼できるセッションをサポートするさまざまなバインディング、および動作のしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f39cf-109">[Reliable Sessions Overview](reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="f39cf-110">[方法: 信頼できるセッション内でメッセージを交換](how-to-exchange-messages-within-a-reliable-session.md) する構成で指定されたカスタムバインディングを使用して、HTTP 経由で信頼できるセッションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f39cf-110">[How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="f39cf-111">[方法: 信頼できるセッション内のメッセージをセキュリティで保護する](how-to-secure-messages-within-reliable-sessions.md) 信頼できるセッションをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f39cf-111">[How to: Secure Messages within Reliable Sessions](how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="f39cf-112">[方法: HTTPS を使用してカスタムの信頼できるセッションバインディングを作成](how-to-create-a-custom-reliable-session-binding-with-https.md) するHTTPS を介して信頼できるセッションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f39cf-112">[How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="f39cf-113">[信頼できるセッションのベストプラクティス](best-practices-for-reliable-sessions.md) 信頼できるセッションの使用に関連するベストプラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f39cf-113">[Best Practices for Reliable Sessions](best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="f39cf-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f39cf-114">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="f39cf-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f39cf-115">See also</span></span>

- [<span data-ttu-id="f39cf-116">キューと信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="f39cf-116">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
- [<span data-ttu-id="f39cf-117">セッション、インスタンス化、およびコンカレンシー</span><span class="sxs-lookup"><span data-stu-id="f39cf-117">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
