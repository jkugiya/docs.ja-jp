---
title: Azure SDK for .NET の概要
description: Azure SDK for .NET の概要と、.NET アプリケーションで SDK を使用するための基本的な手順を示します。
ms.date: 11/30/2020
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: b547e105b13d380ffae049ab55e76aa25abe8cc3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189201"
---
# <a name="azure-sdk-for-net-overview"></a><span data-ttu-id="febdd-103">Azure SDK for .NET の概要</span><span class="sxs-lookup"><span data-stu-id="febdd-103">Azure SDK for .NET overview</span></span>

## <a name="what-is-the-azure-sdk-for-net"></a><span data-ttu-id="febdd-104">Azure SDK for .NET とは</span><span class="sxs-lookup"><span data-stu-id="febdd-104">What is the Azure SDK for .NET</span></span>

<span data-ttu-id="febdd-105">**Azure SDK for .NET** は、.NET アプリケーションから Azure サービスを簡単に使用できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="febdd-105">The **Azure SDK for .NET** is designed to make it easy to use Azure services from your .NET applications.</span></span>  <span data-ttu-id="febdd-106">BLOB ストレージにファイルをアップロードおよびダウンロードする場合も、Azure Key Vault からアプリケーション シークレットを取得する場合も、Azure Event Hubs からの通知を処理する場合も、Azure SDK for .NET では、Azure サービスにアクセスするための一貫性のある使いやすいインターフェイスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="febdd-106">Whether it is uploading and downloading files to Blob Storage, retrieving application secrets from Azure Key Vault, or processing notifications from Azure Event Hubs, the Azure SDK for .NET provides a consistent and familiar interface to access Azure services.</span></span>  

<span data-ttu-id="febdd-107">Azure SDK for .NET は、.NET Core (2.1 以降) と .NET Framework (4.6.1 以上) のアプリケーションの両方で使用できる一連の NuGet パッケージとして提供されています。</span><span class="sxs-lookup"><span data-stu-id="febdd-107">The Azure SDK for .NET is available as series of NuGet packages that can be used in both .NET Core (2.1 and higher) and .NET Framework (4.6.1 and higher) applications.</span></span>

![.NET アプリケーションで Azure SDK を使用して Azure サービスにアクセスする方法を示す図](./media/azure-sdk-for-dotnet-overview.png)

## <a name="use-the-azure-sdk-for-net-in-your-applications"></a><span data-ttu-id="febdd-109">アプリケーションで Azure SDK for .NET を使用する</span><span class="sxs-lookup"><span data-stu-id="febdd-109">Use the Azure SDK for .NET in your applications</span></span>

<span data-ttu-id="febdd-110">いずれかの .NET アプリケーションで Azure SDK パッケージを使用するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="febdd-110">To use an Azure SDK package in one of your .NET applications, you want to follow these steps.</span></span>

1. <span data-ttu-id="febdd-111">**適切な SDK パッケージを見つける -** [パッケージの一覧](../packages.md)を使用して、使用している Azure サービスに適したパッケージを見つけます。</span><span class="sxs-lookup"><span data-stu-id="febdd-111">**Locate the appropriate SDK package -** Use the [package list](../packages.md) to find the appropriate package for the Azure service you are working with.</span></span>  <span data-ttu-id="febdd-112">ほとんどのサービスには、サービスを使用するためのクライアント パッケージと、サービスのインスタンスを作成および管理するための管理パッケージがあります。</span><span class="sxs-lookup"><span data-stu-id="febdd-112">Be advised that most services have a client package for working with the service and a management package for creating and managing instances of the service.</span></span>  <span data-ttu-id="febdd-113">ほとんどの場合、クライアント パッケージが必要になります。</span><span class="sxs-lookup"><span data-stu-id="febdd-113">In most cases, you will want the client package.</span></span>  <span data-ttu-id="febdd-114">NuGet を使用して、このパッケージをアプリケーションにインストールします。</span><span class="sxs-lookup"><span data-stu-id="febdd-114">Install this package in your application using NuGet.</span></span>

2. <span data-ttu-id="febdd-115">**アプリケーションの認証を設定する -** Azure リソースにアクセスするには、Azure でアプリケーションに適切な資格情報とアクセス権が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="febdd-115">**Set up authentication for your application -** To access Azure resources, your application will need to have the appropriate credentials and access rights assigned in Azure.</span></span>  <span data-ttu-id="febdd-116">認証を構成する方法については、[Azure への .NET アプリケーションの認証](../authentication.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="febdd-116">Learn how to configure authentication in [Authenticating .NET applications to Azure](../authentication.md).</span></span>

3. <span data-ttu-id="febdd-117">**アプリケーションで SDK を使用してコードを記述する -** Azure サービスを使用する場合は、コードによって、まずサービスと連携するクライアント オブジェクトが作成されてから、そのクライアント オブジェクトでサービスとやり取りするためのメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="febdd-117">**Write code using the SDK in your application -** When working with Azure services, your code will first create a client object to work with the service and then call methods on that client object to interact with the service.</span></span>  <span data-ttu-id="febdd-118">同期メソッドと非同期メソッドの両方が用意されています。</span><span class="sxs-lookup"><span data-stu-id="febdd-118">Both synchronous and asynchronous methods are provided.</span></span>  <span data-ttu-id="febdd-119">個々の SDK パッケージを使用する例については、Azure ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="febdd-119">Examples of using each individual SDK package are provided throughout the Azure documentation.</span></span>

4. <span data-ttu-id="febdd-120">**SDK のログを構成する (省略可能) -** アプリケーションと Azure の間の問題を診断する必要がある場合は、[Azure SDK for .NET でログを有効にする](../logging.md)ことができます。</span><span class="sxs-lookup"><span data-stu-id="febdd-120">**Configure logging for the SDK (optional) -** If you need to diagnose issues between your application and Azure, you can [enable logging in the Azure SDK for .NET](../logging.md).</span></span>
