---
title: WCF Web Service Reference を追加する
description: .NET Framework プロジェクトのサービス参照の追加と同様に、.NET Core プロジェクトと ASP.NET Core プロジェクトの機能を追加する Microsoft WCF Web Service Reference Provider Tool の概要。
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc
ms.openlocfilehash: fcb7695c904e80d3fcb5ea68cba7ea198b3905f3
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872978"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="bdf1f-103">WCF Web Service Reference Provider ツールを使用する</span><span class="sxs-lookup"><span data-stu-id="bdf1f-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="bdf1f-104">長年にわたり、多くの Visual Studio 開発者は、.NET Framework プロジェクトが Web サービスにアクセスする必要があるときに、[**サービス参照の追加**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)ツールが提供する生産性を利用してきました。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="bdf1f-105">**WCF Web Service Reference** ツールは、.NET Core および ASP.NET Core プロジェクトのサービス参照の追加機能のようなエクスペリエンスを提供する、Visual Studio に接続されたサービス拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="bdf1f-106">このツールは現在のソリューションの Web サービスから、ネットワーク上の場所で、あるいは WSDL ファイルからメタデータを取得し、Web サービスのアクセスに使用できる Windows Communication Foundation (WCF) クライアント プロキシ コードを含む、.NET Core 互換ソース ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdf1f-107">信頼できるソースのサービスのみを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="bdf1f-108">信頼できないソースの参照を追加すると、セキュリティが損なわれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bdf1f-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="bdf1f-109">Prerequisites</span></span>

- <span data-ttu-id="bdf1f-110">[Visual Studio 2017 バージョン 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="bdf1f-111">拡張機能の使用方法</span><span class="sxs-lookup"><span data-stu-id="bdf1f-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="bdf1f-112">**[WCF Web Service Reference]** オプションは、次のプロジェクト テンプレートを使用して作成されたプロジェクトに適用されます。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="bdf1f-113">**Visual C#**  >  **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="bdf1f-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="bdf1f-114">**Visual C#**  >  **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="bdf1f-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="bdf1f-115">**Visual C#**  > **Web** > **ASP.NET Core Web Application**</span><span class="sxs-lookup"><span data-stu-id="bdf1f-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="bdf1f-116">この記事では、**ASP.NET Core Web Application** プロジェクト テンプレートを例として、WCF サービス参照をプロジェクトに追加する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="bdf1f-117">ソリューション エクスプローラーで、プロジェクトの **[接続済みサービス]** ノードをダブルクリックします (.NET Core または .NET Standard プロジェクトの場合、ソリューション エクスプローラーでプロジェクトの **[依存関係]** ノードを右クリックすると、このオプションを使用できます)。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="bdf1f-118">次の図に示すように、 **[接続済みサービス]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![Visual Studio の .NET Core の [接続済みサービス] タブ](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="bdf1f-120">**[接続済みサービス]** ページで、 **[Microsoft WCF Web Service Reference Provider]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="bdf1f-121">**[WCF Web Service Reference の構成]** ウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![Visual Studio の .NET Core の [サービス エンドポイント] タブ](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="bdf1f-123">サービスを選択します。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-123">Select a service.</span></span>

    <span data-ttu-id="bdf1f-124">3a.</span><span class="sxs-lookup"><span data-stu-id="bdf1f-124">3a.</span></span> <span data-ttu-id="bdf1f-125">**[WCF Web Service Reference の構成]** ウィザードでは、いくつかのサービス検索オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="bdf1f-126">現在のソリューションに定義されているサービスを検索するには、 **[探索]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="bdf1f-127">指定したアドレスでホストされているサービスを検索するには、 **[アドレス]** ボックスにサービス URL を入力し、 **[検索]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="bdf1f-128">Web サービスのメタデータ情報を含む WSDL ファイルを選択するには、 **[参照]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="bdf1f-129">3b.</span><span class="sxs-lookup"><span data-stu-id="bdf1f-129">3b.</span></span> <span data-ttu-id="bdf1f-130">**[サービス]** ボックスの検索結果一覧からサービスを選択します。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="bdf1f-131">必要に応じて、生成されたコードの名前空間を対応する **[名前空間]** テキスト ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="bdf1f-132">3c.</span><span class="sxs-lookup"><span data-stu-id="bdf1f-132">3c.</span></span> <span data-ttu-id="bdf1f-133">**[次へ]** ボタンをクリックし、 **[データ型のオプション]** と **[クライアント オプション]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="bdf1f-134">または、既定のオプションを使用するには、 **[完了]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="bdf1f-135">**[データ型のオプション]** フォームを使用すると、生成されるサービス参照の構成設定を絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![Visual Studio の .NET Core の [データ型のオプション] タブ](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="bdf1f-137">**[参照されたアセンブリで型を再利用]** チェック ボックス オプションは、サービス参照コードの生成に必要なデータ型がプロジェクトの参照されているアセンブリのいずれかで定義されている場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="bdf1f-138">このような既存のデータ型を再利用して、コンパイル時の型の不整合や実行時の問題を回避することが重要です。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="bdf1f-139">プロジェクトの依存関係の数やその他のシステム パフォーマンスの要因によっては、型の情報が読み込まれるときに遅延が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="bdf1f-140">**[参照されたアセンブリで型を再利用]** チェック ボックスがオフになっていないと、 **[完了]** ボタンは読み込み中に無効になります。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="bdf1f-141">完了したら、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="bdf1f-142">進行状況を表示している間、ツールでは以下の処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="bdf1f-143">WCF サービスからメタデータをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="bdf1f-144">*reference.cs* というファイルにサービス参照コードを生成し、プロジェクトの **[接続済みサービス]** ノードの下に追加します。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="bdf1f-145">ターゲット プラットフォームでのコンパイルと実行に必要な NuGet パッケージ参照でプロジェクト ファイル (.csproj) を更新します。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Visual Studio の進行状況ウィンドウ](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="bdf1f-147">これらのプロセスが完了すると、生成された WCF クライアントの種類のインスタンスを作成し、サービス操作を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdf1f-148">参照</span><span class="sxs-lookup"><span data-stu-id="bdf1f-148">See also</span></span>

- [<span data-ttu-id="bdf1f-149">Windows Communication Foundation アプリケーション入門</span><span class="sxs-lookup"><span data-stu-id="bdf1f-149">Get started with Windows Communication Foundation applications</span></span>](../../framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="bdf1f-150">Visual Studio での Windows Communication Foundation サービスと WCF データ サービス</span><span class="sxs-lookup"><span data-stu-id="bdf1f-150">Windows Communication Foundation services and WCF data services in Visual Studio</span></span>](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- <span data-ttu-id="bdf1f-151">[WCF supported features on .NET Core](https://github.com/dotnet/wcf/blob/main/release-notes/SupportedFeatures-v2.1.0.md) (.NET Core でサポートされる WCF の機能)</span><span class="sxs-lookup"><span data-stu-id="bdf1f-151">[WCF supported features on .NET Core](https://github.com/dotnet/wcf/blob/main/release-notes/SupportedFeatures-v2.1.0.md)</span></span>

## <a name="feedback--questions"></a><span data-ttu-id="bdf1f-152">フィードバックと質問</span><span class="sxs-lookup"><span data-stu-id="bdf1f-152">Feedback & questions</span></span>

<span data-ttu-id="bdf1f-153">製品に関するフィードバックがある場合は、[Developer Community](https://aka.ms/feedback/report?space=61) で[問題の報告](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) ツールを使用して報告してください。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-153">If you have any product feedback, report it at [Developer Community](https://aka.ms/feedback/report?space=61) using the [Report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) tool.</span></span>

## <a name="release-notes"></a><span data-ttu-id="bdf1f-154">リリース ノート</span><span class="sxs-lookup"><span data-stu-id="bdf1f-154">Release notes</span></span>

- <span data-ttu-id="bdf1f-155">既知の問題を含む最新のリリース情報については、[リリース ノート](https://github.com/dotnet/wcf/blob/main/release-notes/WCF-Web-Service-Reference-notes.md)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdf1f-155">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/main/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>
