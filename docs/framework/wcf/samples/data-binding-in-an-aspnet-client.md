---
description: 詳細については、ASP.NET クライアントでのデータバインディングに関するページを参照してください。
title: ASP.NET クライアントでのデータ バインディング
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 9615c34805d406bb382ab252f317156e1750bed1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755864"
---
# <a name="data-binding-in-an-aspnet-client"></a><span data-ttu-id="fcc0a-103">ASP.NET クライアントでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="fcc0a-103">Data Binding in an ASP.NET Client</span></span>

<span data-ttu-id="fcc0a-104">このサンプルでは、一般的な Windows Communication Foundation (WCF) サービスによって返されたデータを Web フォームアプリケーションにバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-104">This sample demonstrates how to bind data returned by a typical Windows Communication Foundation (WCF) service in a Web Forms application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcc0a-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fcc0a-106">このサンプルでは、要求/応答通信パターンを定義するコントラクトを実装するサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-106">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="fcc0a-107">このサンプルは、ブラウザーからアクセスできるクライアント Web フォームアプリケーションと、インターネットインフォメーションサービス (IIS) でホストされる WCF サービスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-107">The sample consists of a client Web Forms application accessible from a browser and a WCF service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="fcc0a-108">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-108">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="fcc0a-109">コントラクトは `IWeatherService` インターフェイスによって定義されます。このインターフェイスでは、`GetWeatherData` という名前の操作が公開されます。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-109">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="fcc0a-110">この操作は都市名の配列を受け付け、各都市の予想最高気温と最低気温を表す `WeatherData` オブジェクトの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-110">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="fcc0a-111">ASP.NET の .aspx ページでは、DataGrid Web コントロールが定義されています。これには、サービスによって返されるデータのグラフィック表示が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-111">On the ASP.NET client .aspx page, a DataGrid Web control is defined, which contains the graphical representation of the data returned by the service.</span></span> <span data-ttu-id="fcc0a-112">.Aspx ページのコードは、気象データの WCF サービスを呼び出し、オブジェクトの配列にデータを返し `WeatherData` ます。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-112">Code on the .aspx page calls the WCF service for weather data and returns the data to an array of `WeatherData` objects.</span></span> <span data-ttu-id="fcc0a-113">DataGrid の `DataSource` プロパティをこの配列に設定することにより、データを取得する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-113">The DataGrid specifies where to get its data from by setting its `DataSource` property to that array.</span></span> <span data-ttu-id="fcc0a-114">データ バインディングは、DataGrid の `DataBind` メソッドが呼び出されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-114">The data binding occurs with a call to the DataGrid's `DataBind` method.</span></span> <span data-ttu-id="fcc0a-115">このコードはすべて、内に含まれています。`aspx`</span><span class="sxs-lookup"><span data-stu-id="fcc0a-115">All of this code is contained inside the .`aspx`</span></span> <span data-ttu-id="fcc0a-116">ページの `Page_Load` メソッド。ユーザーがブラウザーページを更新するたびに、DataGrid のデータが更新されます。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-116">page's `Page_Load` method, so every time the user refreshes the browser page, the data is updated in the DataGrid.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fcc0a-117">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="fcc0a-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fcc0a-118">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fcc0a-119">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fcc0a-120">このサンプルのクライアントは、開発用 Web サーバーで実行される Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-120">This sample's client is a Web site that runs under a development Web server.</span></span> <span data-ttu-id="fcc0a-121">開発 Web サーバーを起動するには、コマンドプロンプトで「」と入力し `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client` ます。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-121">To launch the development Web server, type the following at the command prompt: `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span></span> <span data-ttu-id="fcc0a-122">次に、を参照し `http://localhost:8000/client` ます。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-122">Then browse to `http://localhost:8000/client`.</span></span> <span data-ttu-id="fcc0a-123">このサンプルを複数のコンピューターで実行するには、クライアントの Web.config ファイル内の `localhost` へのすべての参照をサーバーのコンピューター名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-123">To run this sample across computers, replace all references to `localhost` in the client's Web.config file with the computer name of the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fcc0a-124">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fcc0a-125">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fcc0a-126">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fcc0a-127">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="fcc0a-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
