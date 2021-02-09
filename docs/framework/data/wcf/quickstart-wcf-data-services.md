---
description: '詳細情報: クイック スタート (WCF Data Services)'
title: クイック スタート (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: 92a1b8882f6a7db2ed33f032ad434efd06400421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794950"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="540a6-103">クイック スタート (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="540a6-103">Quickstart (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="540a6-104">このクイックスタートでは、「[はじめに](getting-started-with-wcf-data-services.md)」のトピックをサポートする一連のタスクを通して WCF Data Services と Open Data Protocol (OData) を学習することができます。</span><span class="sxs-lookup"><span data-stu-id="540a6-104">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="540a6-105">学習内容</span><span class="sxs-lookup"><span data-stu-id="540a6-105">What you'll learn</span></span>

<span data-ttu-id="540a6-106">このクイックスタートの最初のタスクでは、データ サービスを作成し、Northwind サンプル データベースの OData フィードを公開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="540a6-106">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="540a6-107">後半のトピックでは、Web ブラウザーを使用して OData フィードにアクセスします。また、クライアント ライブラリを使用して OData フィードを使用する Windows Presentation Foundation (WPF) クライアント アプリケーションも作成します。</span><span class="sxs-lookup"><span data-stu-id="540a6-107">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="540a6-108">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="540a6-108">Prerequisites</span></span>

<span data-ttu-id="540a6-109">このクイックスタートを最後まで行うには、次のコンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="540a6-109">To complete this quickstart, install the following components:</span></span>

- <span data-ttu-id="540a6-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="540a6-110">Visual Studio</span></span>

- <span data-ttu-id="540a6-111">SQL Server のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="540a6-111">An instance of SQL Server.</span></span> <span data-ttu-id="540a6-112">これには SQL Server Express が含まれます。これは、Visual Studio 2015 の既定のインストールに含まれているか、または Visual Studio 2017 以降の **データ ストレージおよび処理** ワークロードの一部として含まれています。</span><span class="sxs-lookup"><span data-stu-id="540a6-112">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="540a6-113">Northwind サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="540a6-113">The Northwind sample database.</span></span> <span data-ttu-id="540a6-114">データベースをインストールするには、[Microsoft SQL Serverの Northwind および pubs サンプル データベース](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)から Transact-SQL スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="540a6-114">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="540a6-115">WCF Data Services クイックスタートのタスク</span><span class="sxs-lookup"><span data-stu-id="540a6-115">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="540a6-116">データ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="540a6-116">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="540a6-117">ASP.NET アプリケーションの定義、データ モデルの定義、データ サービスの作成、およびリソースへのアクセスの有効化を行います。</span><span class="sxs-lookup"><span data-stu-id="540a6-117">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="540a6-118">Web ブラウザーからサービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="540a6-118">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="540a6-119">Visual Studio からサービスを開始し、公開されているフィードに対して Web ブラウザーから HTTP GET 要求を送信してサービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="540a6-119">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="540a6-120">.NET Framework クライアント アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="540a6-120">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="540a6-121">WPF アプリを作成して、OData フィードの使用、Windows コントロールへのデータのバインド、バインドされたコントロールのデータの変更、およびデータ サービスへの変更内容の送信を行います。</span><span class="sxs-lookup"><span data-stu-id="540a6-121">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="540a6-122">クイックスタートの完了バージョンからのプロジェクト ファイルは、[GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)) からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="540a6-122">Project files from a completed version of the quickstart can be downloaded from [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span></span>

## <a name="next-steps"></a><span data-ttu-id="540a6-123">次の手順</span><span class="sxs-lookup"><span data-stu-id="540a6-123">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="540a6-124">クイックスタートの開始</span><span class="sxs-lookup"><span data-stu-id="540a6-124">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="540a6-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="540a6-125">See also</span></span>

- [<span data-ttu-id="540a6-126">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="540a6-126">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
