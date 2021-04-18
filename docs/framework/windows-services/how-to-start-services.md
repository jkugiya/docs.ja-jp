---
title: '方法: サービスを開始する'
description: サービスを開始するいくつかの方法について学習します。 サービスをインストールした後で、サービスを起動します。 開始することで、サービス クラスの OnStart メソッドが呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
ms.openlocfilehash: bf1a4f676c3c7789036cc3650169e04892c2a191
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494546"
---
# <a name="how-to-start-services"></a><span data-ttu-id="5d8d1-105">方法: サービスを開始する</span><span class="sxs-lookup"><span data-stu-id="5d8d1-105">How to: Start Services</span></span>

<span data-ttu-id="5d8d1-106">サービスをインストールした後で、サービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-106">After a service is installed, it must be started.</span></span> <span data-ttu-id="5d8d1-107">起動することで、サービス クラスの <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-107">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="5d8d1-108">通常、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドにはサービスが本来行う処理を定義します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-108">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="5d8d1-109">サービスの起動後は、手動で一時停止または停止するまで、アクティブの状態を維持します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-109">After a service starts, it remains active until it is manually paused or stopped.</span></span>

<span data-ttu-id="5d8d1-110">サービスを自動で起動するか手動で起動するかを設定できます。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-110">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="5d8d1-111">自動的に起動するサービスは、そのサービスがインストールされているコンピューターを再起動したとき、または初めて電源を入れたときに起動します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-111">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="5d8d1-112">手動で起動するサービスは、ユーザーが起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-112">A user must start a service that starts manually.</span></span>

> [!NOTE]
> <span data-ttu-id="5d8d1-113">既定では、Visual Studio で作成されたサービスは手動で起動するように設定されます。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-113">By default, services created with Visual Studio are set to start manually.</span></span>

<span data-ttu-id="5d8d1-114">サービスを手動で起動するには、**サーバー エクスプローラー** または **サービス コントロール マネージャー** を使用します。<xref:System.ServiceProcess.ServiceController> コンポーネントを使ってコードによって起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-114">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>

<span data-ttu-id="5d8d1-115"><xref:System.ServiceProcess.ServiceInstaller.StartType%2A> クラスの <xref:System.ServiceProcess.ServiceInstaller> プロパティを設定し、サービスを手動で起動するか自動で起動するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-115">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>

## <a name="specify-how-a-service-should-start"></a><span data-ttu-id="5d8d1-116">サービスの起動方法を指定する</span><span class="sxs-lookup"><span data-stu-id="5d8d1-116">Specify how a service should start</span></span>

1. <span data-ttu-id="5d8d1-117">サービスの作成後、必要なインストーラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-117">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="5d8d1-118">詳細については、[サービス アプリケーションにインストーラーを追加する](how-to-add-installers-to-your-service-application.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-118">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>

2. <span data-ttu-id="5d8d1-119">デザイナーで、対象となるサービスのインストーラーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-119">In the designer, click the service installer for the service you are working with.</span></span>

3. <span data-ttu-id="5d8d1-120">**[プロパティ]** ウィンドウで、<xref:System.ServiceProcess.ServiceInstaller.StartType%2A> プロパティに次のいずれかの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-120">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>

    |<span data-ttu-id="5d8d1-121">サービスを起動するタイミング</span><span class="sxs-lookup"><span data-stu-id="5d8d1-121">To have your service install</span></span>|<span data-ttu-id="5d8d1-122">設定値</span><span class="sxs-lookup"><span data-stu-id="5d8d1-122">Set this value</span></span>|
    |----------------------------------|--------------------|
    |<span data-ttu-id="5d8d1-123">コンピューターを再起動したとき。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-123">When the computer is restarted</span></span>|<span data-ttu-id="5d8d1-124">**自動**</span><span class="sxs-lookup"><span data-stu-id="5d8d1-124">**Automatic**</span></span>|
    |<span data-ttu-id="5d8d1-125">明示的なユーザー アクションによってサービスを開始するとき。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-125">When an explicit user action starts the service</span></span>|<span data-ttu-id="5d8d1-126">**手動**</span><span class="sxs-lookup"><span data-stu-id="5d8d1-126">**Manual**</span></span>|

    > [!TIP]
    > <span data-ttu-id="5d8d1-127">サービスが起動しないようにするには、<xref:System.ServiceProcess.ServiceInstaller.StartType%2A> プロパティを **[無効]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-127">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="5d8d1-128">サーバーを数回再起動することが見込まれる場合は、サービスを自動的に起動しないように設定することで、再起動の時間を短縮できます。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-128">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5d8d1-129">以上のプロパティやその他のプロパティの設定は、サービスのインストール後に変更できます。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-129">These and other properties can be changed after your service is installed.</span></span>

    <span data-ttu-id="5d8d1-130"><xref:System.ServiceProcess.ServiceInstaller.StartType%2A> プロパティが **[手動]** に設定されているサービスを起動するには、**サーバー エクスプローラー** または **Windows サービス コントロール マネージャー** を使います。また、コードで起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-130">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="5d8d1-131">起動方法によっては、**サービス コントロール マネージャー** のコンテキストではサービスを起動しません。**サーバー エクスプローラー** によるサービスの起動とコードによるサービスの起動の場合は、実際にはコントローラーを操作しています。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-131">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>

## <a name="start-a-service-from-server-explorer"></a><span data-ttu-id="5d8d1-132">サーバー エクスプローラーでサービスを起動する</span><span class="sxs-lookup"><span data-stu-id="5d8d1-132">Start a service from Server Explorer</span></span>

1. <span data-ttu-id="5d8d1-133">サーバーが **サーバー エクスプローラー** の一覧にない場合は追加します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-133">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="5d8d1-134">詳細については、「方法:サーバー エクスプローラー/データベース エクスプローラーにアクセスして初期化する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-134">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>

2. <span data-ttu-id="5d8d1-135">**[サービス]** ノードを展開し、開始するサービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-135">Expand the **Services** node, and then locate the service you want to start.</span></span>

3. <span data-ttu-id="5d8d1-136">サービス名を右クリックし、 **[開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-136">Right-click the name of the service, and then select **Start**.</span></span>

### <a name="start-a-service-from-services"></a><span data-ttu-id="5d8d1-137">Services からサービスを開始する</span><span class="sxs-lookup"><span data-stu-id="5d8d1-137">Start a service from Services</span></span>

1. <span data-ttu-id="5d8d1-138">**[Services]** アプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-138">Open the **Services** app.</span></span>

2. <span data-ttu-id="5d8d1-139">一覧で目的のサービスを右クリックし、 **[開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-139">Select your service in the list, right-click it, and then select **Start**.</span></span>

## <a name="start-a-service-from-code"></a><span data-ttu-id="5d8d1-140">コードからサービスを開始する</span><span class="sxs-lookup"><span data-stu-id="5d8d1-140">Start a service from code</span></span>

1. <span data-ttu-id="5d8d1-141"><xref:System.ServiceProcess.ServiceController> クラスのインスタンスを作成し、管理対象となるサービスと対話するように設定します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-141">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>

2. <span data-ttu-id="5d8d1-142"><xref:System.ServiceProcess.ServiceController.Start%2A> メソッドを呼び出してサービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="5d8d1-142">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d8d1-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d8d1-143">See also</span></span>

- [<span data-ttu-id="5d8d1-144">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="5d8d1-144">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="5d8d1-145">方法: Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="5d8d1-145">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="5d8d1-146">方法: サービス アプリケーションにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="5d8d1-146">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
