---
description: '詳細については、「方法: 信頼できるセッション内のメッセージをセキュリティで保護する」を参照してください。'
title: '方法: 信頼できるセッション内でメッセージをセキュリティで保護する'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: 73ca0d543edc2445dc72264e7eccf6c1eb616313
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643359"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="fa2ea-103">方法: 信頼できるセッション内でメッセージをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="fa2ea-103">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="fa2ea-104">ここでは、信頼できるセッション内で交換されるメッセージに対して、メッセージ レベルのセキュリティを有効にするために必要な手順について説明します。このとき、信頼できるセッションがオプションでサポートされているシステム指定のバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-104">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="fa2ea-105">コードを使用するか、構成ファイルで宣言によって、セキュリティで保護された信頼できるセッションを強制的に有効にします。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-105">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="fa2ea-106">この手順では、クライアントとサービスの構成ファイルを使用して、セキュリティで保護された信頼できるセッションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-106">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="fa2ea-107">この手順の主な部分は、次の 3 つのタスクで構成されます。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-107">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="fa2ea-108">クライアントとサービスのメッセージ交換は信頼できるセッション内で行うことを指定します。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-108">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="fa2ea-109">信頼できるセッション内でメッセージ レベルのセキュリティを要求します。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-109">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="fa2ea-110">サービスに対する認証時にクライアントが使用する必要があるクライアント資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-110">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="fa2ea-111">最初のタスクでは、エンドポイント構成要素に `bindingConfiguration` という名前のバインディング構成 (この例では) を参照する属性が含まれていることが重要です `MessageSecurity` 。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-111">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="fa2ea-112">次に、 [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) 要素の属性をに設定して、構成要素がこの名前を参照して信頼できるセッションを有効にし `enabled` [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) `true` ます。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-112">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="fa2ea-113">信頼できるセッション内で使用できる順序付き配信の保証は、`ordered` 属性を `true` に設定することによって要求できます。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-113">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="fa2ea-114">この構成手順の基になっている例のソースコピーについては、「 [WS Reliable Session](../samples/ws-reliable-session.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-114">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="fa2ea-115">2番目のタスクの重要な項目は、 `mode` **\<security>** クライアントとサービスの要素に含まれる要素の属性をに設定することによって実現され **\<binding>** `Message` ます。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-115">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="fa2ea-116">3番目のタスクの重要な項目は、 `clientCredentialType` **\<message>** クライアントとサービスの要素に含まれる要素の属性をに設定することによって実現され **\<security>** `Certificate` ます。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-116">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="fa2ea-117">信頼できるセッションでメッセージセキュリティを使用する場合、信頼できるメッセージは、最初のエラー時に例外をスローするのではなく、タイムアウトが発生するまで、認証されていないクライアントの認証を試みます。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-117">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="fa2ea-118">信頼できるセッションを使用するようにサービスを WSHttpBinding で構成する</span><span class="sxs-lookup"><span data-stu-id="fa2ea-118">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="fa2ea-119">この手順については [、「方法: 信頼できるセッション内でメッセージを交換](how-to-exchange-messages-within-a-reliable-session.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-119">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="fa2ea-120">信頼できるセッションを使用するようにクライアントを WSHttpBinding で構成する</span><span class="sxs-lookup"><span data-stu-id="fa2ea-120">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="fa2ea-121">この手順については [、「方法: 信頼できるセッション内でメッセージを交換](how-to-exchange-messages-within-a-reliable-session.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-121">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="fa2ea-122">構成にモードと ClientCredentialType を設定する</span><span class="sxs-lookup"><span data-stu-id="fa2ea-122">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="fa2ea-123">構成ファイルの要素に適切なバインド要素を追加 [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) します。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-123">Add an appropriate binding element to the [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="fa2ea-124">次の例では、要素を追加し [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-124">The following example adds a [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="fa2ea-125">要素を追加 **\<binding>** し、その `name` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-125">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="fa2ea-126">この例では、という名前を使用し `MessageSecurity` ます。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-126">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="fa2ea-127">要素を追加 **\<security>** し、 `mode` 属性をに設定し `Message` ます。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-127">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="fa2ea-128">要素内に **\<security>** 要素を追加 **\<message>** し、 `clientCredentialType` 属性をに設定し `Certificate` ます。</span><span class="sxs-lookup"><span data-stu-id="fa2ea-128">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
