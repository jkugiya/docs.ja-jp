---
description: 詳細については、「Windows フォームクライアントでのデータバインディング」を参照してください。
title: Windows フォーム クライアントのデータ バインディング
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: e82bd9eff7c6e8ad132235f5e705b814225aec2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755890"
---
# <a name="data-binding-in-a-windows-forms-client"></a><span data-ttu-id="db8b6-103">Windows フォーム クライアントのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="db8b6-103">Data Binding in a Windows Forms Client</span></span>

<span data-ttu-id="db8b6-104">このサンプルでは、Windows フォームアプリケーションの Windows Communication Foundation (WCF) サービスによって返されるデータにバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="db8b6-104">This sample demonstrates how to bind to data returned by a Windows Communication Foundation (WCF) service in a Windows Forms application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db8b6-105">このサンプルのセットアップ手順とビルド手順については、この記事の最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db8b6-105">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>  
  
 <span data-ttu-id="db8b6-106">このサンプルでは、要求/応答通信パターンを定義するコントラクトを実装するサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="db8b6-106">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="db8b6-107">このサンプルは、クライアント Windows フォームアプリケーション (.exe) と、インターネットインフォメーションサービス (IIS) によってホストされる WCF サービスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="db8b6-107">The sample consists of a client Windows Forms application (.exe) and a WCF service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="db8b6-108">コントラクトは `IWeatherService` インターフェイスによって定義されます。このインターフェイスでは、`GetWeatherData` という名前の操作が公開されます。</span><span class="sxs-lookup"><span data-stu-id="db8b6-108">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="db8b6-109">この操作は都市名の配列を受け付け、各都市の予想最高気温と最低気温を表す `WeatherData` オブジェクトの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="db8b6-109">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="db8b6-110">データ バインディングは、Windows フォーム アプリケーションのクライアントで発生します。</span><span class="sxs-lookup"><span data-stu-id="db8b6-110">The data binding occurs on the client in the Windows Forms application.</span></span> <span data-ttu-id="db8b6-111">`DataGridView` は Windows フォーム デザイナで定義し、データをグラフィック表示します。</span><span class="sxs-lookup"><span data-stu-id="db8b6-111">A `DataGridView` is defined in the Windows Forms designer, which is a graphical representation of the data.</span></span> <span data-ttu-id="db8b6-112">さらに、`BindingSource` という中継局も作成されます。</span><span class="sxs-lookup"><span data-stu-id="db8b6-112">An intermediary named `BindingSource` is also created.</span></span> <span data-ttu-id="db8b6-113">`BindingSource` のデータ ソースは、サービスによって返されるデータ配列に設定されます。</span><span class="sxs-lookup"><span data-stu-id="db8b6-113">The data source of `BindingSource` is set to the data array returned by the service.</span></span> <span data-ttu-id="db8b6-114">`BindingSource` の目的は、データとデータ ビュー間を間接化するレイヤを提供することです。</span><span class="sxs-lookup"><span data-stu-id="db8b6-114">The purpose of the `BindingSource` is to provide a layer of indirection between the data and the data view.</span></span> <span data-ttu-id="db8b6-115">データとの対話 (移動、並べ替え、フィルタ処理、更新など) はすべて、`BindingSource` コンポーネントを呼び出すことによって実行します。</span><span class="sxs-lookup"><span data-stu-id="db8b6-115">All interaction with the data, such as navigating, sorting, filtering, and updating, is accomplished with calls to the `BindingSource` component.</span></span> <span data-ttu-id="db8b6-116">`DataGridView` へのデータ バインディングを行うには、`datasource` の `DataGridView` を `BindingSource` オブジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="db8b6-116">To accomplish data binding to the `DataGridView`, the `datasource` of the `DataGridView` is then set to the `BindingSource` object.</span></span> <span data-ttu-id="db8b6-117">WCF サービスから返されたすべてのデータが、グラフィカルにユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="db8b6-117">All of the data returned from the WCF service is then displayed graphically to the user.</span></span>  <span data-ttu-id="db8b6-118">ユーザーがボタンをクリックするたびに、返されたデータはデータ バインドされた `DataGridView` で自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="db8b6-118">Every time the user clicks the button, the returned data is automatically updated in the data-bound `DataGridView`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="db8b6-119">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="db8b6-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="db8b6-120">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="db8b6-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="db8b6-121">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="db8b6-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="db8b6-122">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="db8b6-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="db8b6-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="db8b6-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="db8b6-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="db8b6-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="db8b6-125">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="db8b6-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="db8b6-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="db8b6-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
