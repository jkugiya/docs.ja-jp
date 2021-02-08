---
description: '詳細情報: COM アプリケーションとの統合の概要'
title: COM アプリケーションとの統合の概要
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: a179fd73c8065fff1e16d3f86202d717df155b81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802815"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="05b9a-103">COM アプリケーションとの統合の概要</span><span class="sxs-lookup"><span data-stu-id="05b9a-103">Integrating with COM Applications Overview</span></span>

<span data-ttu-id="05b9a-104">Windows Communication Foundation (WCF) を使用すると、マネージコード開発者は、接続されたアプリケーションを作成するための豊富な環境を提供できます。</span><span class="sxs-lookup"><span data-stu-id="05b9a-104">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="05b9a-105">ただし、アンマネージ COM ベースのコードに多大な投資をしていて、移行したくない場合でも、wcf サービスモニカーを使用して、WCF Web サービスを既存のコードに直接統合できます。</span><span class="sxs-lookup"><span data-stu-id="05b9a-105">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="05b9a-106">サービス モニカーは Office VBA、Visual Basic 6.0、または Visual C++ 6.0 などの幅広い COM ベースの開発環境で使用可能です。</span><span class="sxs-lookup"><span data-stu-id="05b9a-106">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>

> [!NOTE]
> <span data-ttu-id="05b9a-107">サービスモニカーは、すべての通信に WCF 通信チャネルを使用します。</span><span class="sxs-lookup"><span data-stu-id="05b9a-107">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="05b9a-108">このチャネルのセキュリティ メカニズムと識別メカニズムは、標準の COM および DCOM プロキシで使用されるものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="05b9a-108">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="05b9a-109">また、サービスモニカーでは WCF 通信チャネルが使用されるため、すべての呼び出しで既定のタイムアウト期間は1分です。</span><span class="sxs-lookup"><span data-stu-id="05b9a-109">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>

<span data-ttu-id="05b9a-110">サービスモニカーは、関数と共に使用して、 `GetObject` アンマネージ開発者に、WCF Web サービスを呼び出すための厳密に型指定された COM 固有のアプローチを提供します。</span><span class="sxs-lookup"><span data-stu-id="05b9a-110">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="05b9a-111">これには、WCF Web サービスコントラクトと使用するバインディングの、COM から参照できるローカルな定義が必要です。</span><span class="sxs-lookup"><span data-stu-id="05b9a-111">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="05b9a-112">他の WCF クライアントと同様に、サービスモニカーは、サービスへの型指定されたチャネルを構築する必要があります。ただし、このチャネルの構築は、最初のメソッド呼び出しで COM プログラマに透過的に行われます。</span><span class="sxs-lookup"><span data-stu-id="05b9a-112">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>

<span data-ttu-id="05b9a-113">他の WCF クライアントとの共通点として、モニカーを使用する場合、アプリケーションは、サービスと通信するためのアドレス、バインディング、およびコントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="05b9a-113">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="05b9a-114">コントラクトは、次のいずれかの方法で指定できます。</span><span class="sxs-lookup"><span data-stu-id="05b9a-114">The contract can be specified in one of the following ways:</span></span>

- <span data-ttu-id="05b9a-115">型指定のあるコントラクト - クライアント コンピューターで COM から参照できる型として登録されます。</span><span class="sxs-lookup"><span data-stu-id="05b9a-115">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>

- <span data-ttu-id="05b9a-116">WSDL コントラクト - WSDL ドキュメントという形で供給されます。</span><span class="sxs-lookup"><span data-stu-id="05b9a-116">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>

- <span data-ttu-id="05b9a-117">MEX コントラクト - 実行時に Metadata Exchange (MEX) エンドポイントから取得されます。</span><span class="sxs-lookup"><span data-stu-id="05b9a-117">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>

## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="05b9a-118">サービス モニカーでサポートされるパラメーター</span><span class="sxs-lookup"><span data-stu-id="05b9a-118">Parameters Supported by the Service Moniker</span></span>

<span data-ttu-id="05b9a-119">サービス モニカーでサポートされるパラメーターを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="05b9a-119">The following table shows the parameters that are supported by the service moniker.</span></span>

|<span data-ttu-id="05b9a-120">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05b9a-120">Parameter</span></span>|<span data-ttu-id="05b9a-121">説明</span><span class="sxs-lookup"><span data-stu-id="05b9a-121">Description</span></span>|
|---------------|-----------------|
|`address`|<span data-ttu-id="05b9a-122">サービスの URL 位置。</span><span class="sxs-lookup"><span data-stu-id="05b9a-122">URL location of the service.</span></span>|
|`binding`|<span data-ttu-id="05b9a-123">アプリケーション構成のバインディング セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="05b9a-123">Binding section name from the application configuration.</span></span>|
|`bindingConfiguration`|<span data-ttu-id="05b9a-124">名前付きバインディング セクション内の名前付きバインディング インスタンス。</span><span class="sxs-lookup"><span data-stu-id="05b9a-124">Named binding instance from within the named binding section.</span></span>|
|`contract`|<span data-ttu-id="05b9a-125">サービス コントラクトまたは (MEX の) コントラクト名を表すインターフェイス識別子 (IID)。</span><span class="sxs-lookup"><span data-stu-id="05b9a-125">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|
|`wsdl`|<span data-ttu-id="05b9a-126">代替形式のコントラクト定義を提供する WSDL ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="05b9a-126">WSDL document that provides an alternative form of contract definition.</span></span>|
|`spnIdentity`|<span data-ttu-id="05b9a-127">サービスとの通信に使用するサーバー プリンシパル名 (SPN) ID。</span><span class="sxs-lookup"><span data-stu-id="05b9a-127">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|
|`upnIdentity`|<span data-ttu-id="05b9a-128">サービスとの通信に使用するユーザー プリンシパル名 (UPN) ID。</span><span class="sxs-lookup"><span data-stu-id="05b9a-128">User principal name (UPN) identity to be used to communicate with the service.</span></span>|
|`dnsIdentity`|<span data-ttu-id="05b9a-129">サービスとの通信に使用する DNS ID。</span><span class="sxs-lookup"><span data-stu-id="05b9a-129">DNS identity to be used to communicate with the service.</span></span>|
|`mexAddress`|<span data-ttu-id="05b9a-130">サービスの Metadata Exchange (MEX) エンドポイントの URL 位置。</span><span class="sxs-lookup"><span data-stu-id="05b9a-130">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|
|`mexBinding`|<span data-ttu-id="05b9a-131">MEX エンドポイントと接続するための、アプリケーション構成のバインディング セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="05b9a-131">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|
|`mexBindingConfiguration`|<span data-ttu-id="05b9a-132">MEX エンドポイントと接続する名前付きバインディング セクション内の名前付きバインディング インスタンス。</span><span class="sxs-lookup"><span data-stu-id="05b9a-132">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|
|`bindingNamespace`|<span data-ttu-id="05b9a-133">取得する MEX のバインディング セクション名の名前空間。</span><span class="sxs-lookup"><span data-stu-id="05b9a-133">Namespace of the binding section name from the retrieved MEX.</span></span>|
|`contractNamespace`|<span data-ttu-id="05b9a-134">取得する MEX のコントラクトの名前空間。</span><span class="sxs-lookup"><span data-stu-id="05b9a-134">Namespace of the contract from the retrieved MEX.</span></span>|
|`mexSpnIdentity`|<span data-ttu-id="05b9a-135">MEX エンドポイントとの通信に使用するサーバー プリンシパル名 (SPN) ID。</span><span class="sxs-lookup"><span data-stu-id="05b9a-135">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexUpnIdentity`|<span data-ttu-id="05b9a-136">MEX エンドポイントとの通信に使用するユーザー プリンシパル名 (UPN) ID。</span><span class="sxs-lookup"><span data-stu-id="05b9a-136">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexDnsIdentity`|<span data-ttu-id="05b9a-137">MEX エンドポイントとの通信に使用する DNS ID。</span><span class="sxs-lookup"><span data-stu-id="05b9a-137">DNS identity to be used to communicate with the MEX endpoint.</span></span>|
|`serializer`|<span data-ttu-id="05b9a-138">"XML" シリアライザーと "datacontract" シリアライザーのいずれを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="05b9a-138">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|

> [!NOTE]
> <span data-ttu-id="05b9a-139">すべての COM ベースのクライアントで使用されている場合でも、サービスモニカーを使用するには WCF およびサポート .NET Framework 2.0 がクライアントコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="05b9a-139">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="05b9a-140">また、サービス モニカーを使用するクライアント アプリケーションには、適切なバージョンの .NET Framework ランタイムが読み込まれていることが重要です。</span><span class="sxs-lookup"><span data-stu-id="05b9a-140">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="05b9a-141">Office アプリケーション内でモニカーを使用する場合、構成ファイルに、正しいフレームワーク バージョンが読み込まれていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05b9a-141">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="05b9a-142">たとえば Excel の場合、Excel.exe ファイルと同じディレクトリにある Excel.exe.config というファイルに、次のテキストが記述されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="05b9a-142">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> <span data-ttu-id="05b9a-143">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="05b9a-143">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a><span data-ttu-id="05b9a-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="05b9a-144">See also</span></span>

- [<span data-ttu-id="05b9a-145">方法: サービス モニカーを登録および構成する</span><span class="sxs-lookup"><span data-stu-id="05b9a-145">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)
