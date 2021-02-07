---
description: '詳細情報: 機能拡張の概要'
title: 拡張機能の概要
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: a3e614d107d2371076358f8e7786c1bb246e36eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732840"
---
# <a name="introduction-to-extensibility"></a><span data-ttu-id="d4ac0-103">拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="d4ac0-103">Introduction to Extensibility</span></span>

<span data-ttu-id="d4ac0-104">Windows Communication Foundation (WCF) アプリケーションモデルは、分散アプリケーションの通信要件の大部分を解決するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-104">The Windows Communication Foundation (WCF) application model is designed to solve the greater part of the communication requirements of any distributed application.</span></span> <span data-ttu-id="d4ac0-105">ただし、既定のアプリケーション モデルとシステム提供の実装でサポートされないシナリオが必ず存在します。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-105">But there are always scenarios that the default application model and system-provided implementations do not support.</span></span> <span data-ttu-id="d4ac0-106">WCF の機能拡張モデルは、アプリケーションモデル全体を置き換えるポイントであっても、あらゆるレベルでシステムの動作を変更できるようにすることで、カスタムシナリオをサポートすることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-106">The WCF extensibility model is intended to support custom scenarios by enabling you to modify system behavior at every level, even to the point of replacing the entire application model.</span></span> <span data-ttu-id="d4ac0-107">ここでは、拡張のさまざまな領域を提示し、各領域の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-107">This topic outlines the various areas of extension and points to more information about each.</span></span>  
  
## <a name="areas-to-extend"></a><span data-ttu-id="d4ac0-108">拡張する領域</span><span class="sxs-lookup"><span data-stu-id="d4ac0-108">Areas to Extend</span></span>  

 <span data-ttu-id="d4ac0-109">次の領域を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-109">You can extend:</span></span>  
  
- <span data-ttu-id="d4ac0-110">アプリケーション ランタイム。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-110">The application runtime.</span></span> <span data-ttu-id="d4ac0-111">ここでは、アプリケーションについて、メッセージのディスパッチと処理を拡張します。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-111">This extends the dispatching and the processing of messages for the application.</span></span> <span data-ttu-id="d4ac0-112">この領域には、セキュリティ システム、メタデータ システム、シリアル化システム、およびアプリケーションを基になるチャネル システムに接続するためのバインディングとバインド要素も含まれます。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-112">This area also includes extending the security system, the metadata system, the serialization system, and the bindings and binding elements that connect the application with the underlying channel system.</span></span>  
  
- <span data-ttu-id="d4ac0-113">チャネルとチャネル ランタイム。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-113">The channel and channel runtime.</span></span> <span data-ttu-id="d4ac0-114">ここでは、メッセージ レベルで機能するシステムを拡張し、プロトコル、トランスポート、およびエンコーディングのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-114">This extends the system that functions at the message level, providing protocol, transport, and encoding support.</span></span>  
  
- <span data-ttu-id="d4ac0-115">ホスト ランタイム。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-115">The host runtime.</span></span> <span data-ttu-id="d4ac0-116">ここでは、チャネルおよびアプリケーション ランタイムとのホスト アプリケーション ドメインの関係を拡張します。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-116">This extends the relationship of the hosting application domain to the channel and application runtime.</span></span>  
  
### <a name="extending-the-application-runtime"></a><span data-ttu-id="d4ac0-117">アプリケーション ランタイムの拡張</span><span class="sxs-lookup"><span data-stu-id="d4ac0-117">Extending the Application Runtime</span></span>  

 <span data-ttu-id="d4ac0-118">WCF アプリケーションでは、対応するチャネル宛てのメッセージと、アプリケーション自体宛てのメッセージが区別されます。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-118">In WCF applications, there is a distinction between messages that are destined for a corresponding channel and messages that are destined for the application itself.</span></span> <span data-ttu-id="d4ac0-119">チャネル メッセージは、セキュリティで保護されたメッセージ交換の確立や、信頼できるセッションの確立など、特定のチャネル関連の機能をサポートします。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-119">Channel messages support some channel-related functionality, such as establishing a secure conversation or establishing a reliable session.</span></span> <span data-ttu-id="d4ac0-120">このメッセージは、アプリケーション ランタイムでは使用できません。このメッセージは、アプリケーション層が関係する前に処理されます。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-120">These messages are not available to the application runtime; they are processed before the application layer is involved.</span></span>  
  
 <span data-ttu-id="d4ac0-121">アプリケーション メッセージは、ユーザーまたはユーザーの顧客が作成したクライアントまたはサービスの操作向けのデータを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-121">Application messages contain data that is destined for a client or service operation that you or your customer has created.</span></span> <span data-ttu-id="d4ac0-122">このメッセージは、必要に応じて、メッセージまたはオブジェクトの形でアプリケーション レベルの拡張システムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-122">These messages are available to the application-level extension system in message or object form, depending upon your needs.</span></span>  
  
 <span data-ttu-id="d4ac0-123">すべてのメッセージはチャネル システムを通過しますが、アプリケーション メッセージだけがチャネル システムからアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-123">All messages pass through the channel system; only application messages are passed from the channel system into the application.</span></span> <span data-ttu-id="d4ac0-124">新しいチャネル レベルの機能を作成するには、チャネル システムを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-124">To create new channel-level functionality, you must extend the channel system.</span></span> <span data-ttu-id="d4ac0-125">新しいアプリケーション レベルの機能を作成するには、サービスまたはクライアントのランタイム (それぞれディスパッチャーとチャネル ファクトリ) を拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-125">To create new application-level functionality, you must extend the service or client runtime (dispatchers and channel factories, respectively).</span></span> <span data-ttu-id="d4ac0-126">アプリケーションランタイムの拡張の詳細については、「 [ServiceHost とサービスモデルレイヤーの拡張](./extending/extending-servicehost-and-the-service-model-layer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-126">For more information about extending the application runtime, see [Extending ServiceHost and the Service Model Layer](./extending/extending-servicehost-and-the-service-model-layer.md).</span></span>  
  
#### <a name="extending-security"></a><span data-ttu-id="d4ac0-127">セキュリティの拡張</span><span class="sxs-lookup"><span data-stu-id="d4ac0-127">Extending Security</span></span>  

 <span data-ttu-id="d4ac0-128">トークンや資格情報などのカスタム セキュリティ機構を作成するには、セキュリティ システムを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-128">To build custom security mechanisms such as tokens and credentials, you must extend the security system.</span></span> <span data-ttu-id="d4ac0-129">詳細については、「 [セキュリティの拡張](./extending/extending-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-129">For more information, see [Extending Security](./extending/extending-security.md).</span></span>  
  
#### <a name="extending-metadata"></a><span data-ttu-id="d4ac0-130">メタデータの拡張</span><span class="sxs-lookup"><span data-stu-id="d4ac0-130">Extending Metadata</span></span>  

 <span data-ttu-id="d4ac0-131">メタデータを既定以外の方法で公開するには、メタデータ システムを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-131">To expose your metadata in differently than the default, you must extend the metadata system.</span></span> <span data-ttu-id="d4ac0-132">詳細については、「 [メタデータシステムの拡張](./extending/extending-the-metadata-system.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-132">For more information, see [Extending the Metadata System](./extending/extending-the-metadata-system.md).</span></span>  
  
#### <a name="extending-serialization"></a><span data-ttu-id="d4ac0-133">シリアル化の拡張</span><span class="sxs-lookup"><span data-stu-id="d4ac0-133">Extending Serialization</span></span>  

 <span data-ttu-id="d4ac0-134">カスタム エンコーダーの作成、データ サロゲートの提供、または転送されるデータのカスタマイズに関するその他の作業を行うには、シリアル化システムを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-134">To build custom encoders, provide data surrogates, or other work involving the customization of transferred data, you must extend the serialization system.</span></span> <span data-ttu-id="d4ac0-135">詳細については、「 [エンコーダーとシリアライザーの拡張](./extending/extending-encoders-and-serializers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-135">For more information, see [Extending Encoders and Serializers](./extending/extending-encoders-and-serializers.md).</span></span>  
  
#### <a name="extending-bindings"></a><span data-ttu-id="d4ac0-136">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="d4ac0-136">Extending Bindings</span></span>  

 <span data-ttu-id="d4ac0-137">トランスポート チャネルまたはプロトコル チャネルをアプリケーション層に関連付けるには、バインディング システムを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-137">To associate transport or protocol channels with the application layer, you must extend the binding system.</span></span> <span data-ttu-id="d4ac0-138">詳細については、「 [バインディングの拡張](./extending/extending-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-138">For more information, see [Extending Bindings](./extending/extending-bindings.md).</span></span>  
  
### <a name="extending-the-channel-system"></a><span data-ttu-id="d4ac0-139">チャネル システムの拡張</span><span class="sxs-lookup"><span data-stu-id="d4ac0-139">Extending the Channel System</span></span>  

 <span data-ttu-id="d4ac0-140">カスタムトランスポートまたはプロトコル機能をサポートするチャネルを作成するには、「 [チャネルレイヤーの拡張](./extending/extending-the-channel-layer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-140">To create channels that support custom transports or protocol functionality, see [Extending the Channel Layer](./extending/extending-the-channel-layer.md).</span></span>  
  
### <a name="extending-the-service-hosting-system"></a><span data-ttu-id="d4ac0-141">サービス ホスト システムの拡張</span><span class="sxs-lookup"><span data-stu-id="d4ac0-141">Extending the Service Hosting System</span></span>  

 <span data-ttu-id="d4ac0-142">サービス全体のアプリケーション モデルを変更するには、<xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> クラスを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-142">To modify the service-wide application model, you must extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d4ac0-143">詳細については、「 [ServiceHost とサービスモデルレイヤーの拡張](./extending/extending-servicehost-and-the-service-model-layer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-143">For more information, see [Extending ServiceHost and the Service Model Layer](./extending/extending-servicehost-and-the-service-model-layer.md).</span></span>  
  
 <span data-ttu-id="d4ac0-144">ホスト アプリケーション ドメインとサービス ホストとの関係を変更するには、<xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> クラスを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-144">To modify the relationship between the hosting application domain and the service host, you must extend the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d4ac0-145">詳細については、「 [ServiceHostFactory を使用したホストの拡張](./extending/extending-hosting-using-servicehostfactory.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ac0-145">For more information, see [Extending Hosting Using ServiceHostFactory](./extending/extending-hosting-using-servicehostfactory.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ac0-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4ac0-146">See also</span></span>

- [<span data-ttu-id="d4ac0-147">WCF の拡張</span><span class="sxs-lookup"><span data-stu-id="d4ac0-147">Extending WCF</span></span>](./extending/index.md)
