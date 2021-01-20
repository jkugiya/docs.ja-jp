---
title: Windows 10 の移行
description: パッケージ化や XAML アイランドなどの Windows 10 の機能の詳細について説明します。
ms.date: 12/29/2020
ms.openlocfilehash: 139a8f2354803dafeb0178b4dbfb57a95c4ddb34
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615946"
---
# <a name="windows-10-migration"></a><span data-ttu-id="1afc3-103">Windows 10 の移行</span><span class="sxs-lookup"><span data-stu-id="1afc3-103">Windows 10 migration</span></span>

<span data-ttu-id="1afc3-104">次のような状況が考えられます。 Windows 7 日以内に開発された動作中のデスクトップアプリケーションがあるとします。</span><span class="sxs-lookup"><span data-stu-id="1afc3-104">Consider the following situation: You have a working desktop application that was developed in the Windows 7 days.</span></span> <span data-ttu-id="1afc3-105">その時点で利用可能な WPF テクノロジを使用しており、問題なく動作しますが、Windows 10 で実行したときの UI と動作が古くなっています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-105">It's using WPF technology available at that time and working fine but it has an outdated UI and behaviors when you run it on Windows 10.</span></span> <span data-ttu-id="1afc3-106">これは、マトリックスなどの futuristic 映画を視聴し、Nokia 8110 デバイスを使用して Neo を表示する場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-106">It is like when you watch a futuristic movie like Matrix and you see Neo using the Nokia 8110 device.</span></span> <span data-ttu-id="1afc3-107">フィルムは20年後にうまく機能しますが、デバイスの最新化によるメリットが得られます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-107">The film works great after 20 years but it would rather benefit from a device modernization.</span></span>

<span data-ttu-id="1afc3-108">Windows 10 のリリースでは、タブレットやタッチデバイスのようなシナリオをサポートする多くのイノベーションが導入され、Microsoft オペレーティングシステムのユーザーに最適なエクスペリエンスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-108">With the release of Windows 10, Microsoft introduced many innovations to support scenarios like tablets and touch devices and to provide the best experience for users for a Microsoft operating system ever.</span></span> <span data-ttu-id="1afc3-109">たとえば、次のように操作できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-109">For example, you can:</span></span>

- <span data-ttu-id="1afc3-110">Windows Hello を使用して顔でサインインします。</span><span class="sxs-lookup"><span data-stu-id="1afc3-110">Sign in with your face using Windows Hello.</span></span>
- <span data-ttu-id="1afc3-111">ペンを使用して、自動的に認識され、digitalized されるテキストを描画または手書き入力します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-111">Use a pen to draw or handwrite text that is automatically recognized and digitalized.</span></span>
- <span data-ttu-id="1afc3-112">WinML を使用して、クラウド上に構築されたローカルでカスタマイズされた AI モデルを実行します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-112">Run locally customized AI models built on the cloud using WinML.</span></span>

<span data-ttu-id="1afc3-113">これらのすべての機能は、Windows ランタイム (WinRT) ライブラリを通じて Windows 開発者に対して有効になっています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-113">All these features are enabled for Windows developers through Windows Runtime (WinRT) libraries.</span></span> <span data-ttu-id="1afc3-114">これらの機能は、既存のデスクトップアプリで利用できます。これは、ライブラリが .NET Framework と .NET の両方にも公開されているためです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-114">You can take advantage of these features in your existing desktop apps because the libraries are exposed to both the .NET Framework and .NET as well.</span></span> <span data-ttu-id="1afc3-115">XAML アイランドを使用して UI を最新化し、時間に従ってアプリのビジュアルと動作を向上させることもできます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-115">You can even modernize your UI with the use of XAML Islands and improve the visuals and behavior of your apps according to the times.</span></span>

<span data-ttu-id="1afc3-116">ここで注意すべき重要な点の1つは、この近代化パスに従うために .NET Framework テクノロジを破棄する必要がないことです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-116">One important thing to note here is that you don't need to abandon .NET Framework technology to follow this modernization path.</span></span> <span data-ttu-id="1afc3-117">.NET に移行しなくても、Windows 10 のすべての利点を活用して、その機能を維持することができます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-117">You can safely stay on there and have all the benefits of Windows 10 without the pressure to migrate to .NET.</span></span> <span data-ttu-id="1afc3-118">そのため、最新化パスを選択するための能力と柔軟性が得られます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-118">So, you get both the power and the flexibility to choose your modernization path.</span></span>

## <a name="winrt-apis"></a><span data-ttu-id="1afc3-119">WinRT Api</span><span class="sxs-lookup"><span data-stu-id="1afc3-119">WinRT APIs</span></span>

<span data-ttu-id="1afc3-120">WinRT Api は、オブジェクト指向の適切に構造化されたアプリケーションプログラミングインターフェイス (Api) です。これにより、Windows 10 開発者は、オペレーティングシステムが提供するすべての機能にアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-120">WinRT APIs are object-oriented, well-structured application programming interfaces (APIs) that give Windows 10 developers access to everything the operating system has to offer.</span></span> <span data-ttu-id="1afc3-121">WinRT Api を使用して、プッシュ通知、デバイス Api、Microsoft Ink、WinML などの機能をデスクトップアプリに統合できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-121">Through WinRT APIs, you can integrate functionalities like Push Notifications, Device APIs, Microsoft Ink, and WinML, among others on your desktop apps.</span></span>

<span data-ttu-id="1afc3-122">一般に、WinRT Api は従来のデスクトップアプリから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-122">In general, WinRT APIs can be called from a classic desktop app.</span></span> <span data-ttu-id="1afc3-123">ただし、次の2つの主な領域には、この規則の例外があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-123">However, two main areas present an exception to this rule:</span></span>

* <span data-ttu-id="1afc3-124">パッケージ id を必要とする Api。</span><span class="sxs-lookup"><span data-stu-id="1afc3-124">APIs that require a package identity.</span></span>
* <span data-ttu-id="1afc3-125">XAML やコンポジションなどの視覚化を必要とする Api。</span><span class="sxs-lookup"><span data-stu-id="1afc3-125">APIs that require visualization like XAML or Composition.</span></span>

### <a name="universal-windows-platform-uwp-packages"></a><span data-ttu-id="1afc3-126">ユニバーサル Windows プラットフォーム (UWP) パッケージ</span><span class="sxs-lookup"><span data-stu-id="1afc3-126">Universal Windows Platform (UWP) packages</span></span>

#### <a name="application-package-identity"></a><span data-ttu-id="1afc3-127">アプリケーションパッケージ Id</span><span class="sxs-lookup"><span data-stu-id="1afc3-127">Application Package Identity</span></span>

<span data-ttu-id="1afc3-128">UWP アプリには、OS がアプリケーションのインストールとアンインストールを管理する展開システムがあります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-128">UWP apps have a deployment system where the OS manages the installation and uninstallation of application.</span></span> <span data-ttu-id="1afc3-129">この場合、インストールは宣言型である必要があります。つまり、インストール中にユーザーコードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="1afc3-129">That requires the installation to be declarative, meaning that no user code is executed during install.</span></span> <span data-ttu-id="1afc3-130">その代わりに、アプリがシステムと統合する必要があるすべてのもの (プロトコル、ファイルの種類、拡張機能など) は、アプリケーションマニフェストで宣言されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-130">Instead, everything the app wants to integrate with the system, such as protocols, file types, and extensions, is declared in the application manifest.</span></span> <span data-ttu-id="1afc3-131">配置時には、配置パイプラインによって統合ポイントが構成されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-131">At deployment time, the deployment pipeline configures those integration points.</span></span> <span data-ttu-id="1afc3-132">OS がすべての機能を管理し、それを追跡する唯一の方法は、"パッケージ" ごとに、アプリケーションの一意の識別子である id を持つことです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-132">The only way for the OS to manage all this functionality and keep track of it is for each 'package' to have an identity, a unique identifier for the application.</span></span>

<span data-ttu-id="1afc3-133">一部の WinRT Api では、このパッケージ id が想定どおりに動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-133">Some WinRT APIs require this package identity to work as expected.</span></span> <span data-ttu-id="1afc3-134">ただし、ネイティブ C++ や .NET アプリなどの従来のデスクトップアプリでは、パッケージ id を必要としない異なる展開システムを使用します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-134">However, classic desktop apps like native C++ or .NET apps, use different deployment systems that don't require a package identity.</span></span> <span data-ttu-id="1afc3-135">これらの WinRT Api をデスクトップアプリケーションで使用する場合は、パッケージ id を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-135">If you want to use these WinRT APIs in your desktop application, you need to provide them a package identity.</span></span>

<span data-ttu-id="1afc3-136">続行する1つの方法は、追加のパッケージプロジェクトをビルドすることです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-136">One way to proceed is to build an additional packaging project.</span></span> <span data-ttu-id="1afc3-137">パッケージプロジェクト内で、元のソースコードプロジェクトをポイントし、提供する Id 情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-137">Inside the packaging project, you point to the original source code project and specify the Identity information you want to provide.</span></span> <span data-ttu-id="1afc3-138">パッケージをインストールし、インストールされているアプリを実行すると、Id を必要とするすべての WinRT Api をコードで呼び出すことができるように自動的に識別されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-138">If you install the package and run the installed app, it will automatically get an identify enabling your code to call all WinRT APIs requiring Identity.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

<span data-ttu-id="1afc3-139">API を含む型が [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) 属性でマークされているかどうかを調べることによって、パッケージ化されたアプリケーション id を必要とする api を確認できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-139">You can check which APIs need a packaged application identity by inspecting if the type that contains the API is marked with the [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) attribute.</span></span> <span data-ttu-id="1afc3-140">そうであれば、従来のデスクトップアプリからの場合はを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-140">If it is, you can call if from an unpackaged traditional desktop app.</span></span> <span data-ttu-id="1afc3-141">それ以外の場合は、パッケージプロジェクトのヘルプを使用して、クラシックデスクトップアプリを UWP に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-141">Otherwise, you must convert your classic desktop app to a UWP with the help of a packaging project.</span></span>

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a><span data-ttu-id="1afc3-142">パッケージ化の利点</span><span class="sxs-lookup"><span data-stu-id="1afc3-142">Benefits of packaging</span></span>

<span data-ttu-id="1afc3-143">これらの Api へのアクセスを提供するだけでなく、次のようなデスクトップアプリケーション用の Windows アプリパッケージを作成することによって、いくつかの利点を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-143">Besides giving you access to these APIs, you get some additional benefits by creating a Windows App package for your desktop application including:</span></span>

* <span data-ttu-id="1afc3-144">**展開の合理化**。</span><span class="sxs-lookup"><span data-stu-id="1afc3-144">**Streamlined deployment**.</span></span> <span data-ttu-id="1afc3-145">アプリには、ユーザーが信頼性の高い方法でアプリケーションをインストールして更新できるようにするための、優れた展開エクスペリエンスがあります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-145">Apps have a great deployment experience ensuring that users can confidently install an application and update it.</span></span> <span data-ttu-id="1afc3-146">ユーザーがアプリをアンインストールすることを選択した場合、そのアプリは完全に削除され、Windows の問題を回避するためのトレースは残されていません。</span><span class="sxs-lookup"><span data-stu-id="1afc3-146">If a user chooses to uninstall the app, it's removed completely with no trace left behind preventing the Windows rot problem.</span></span>

* <span data-ttu-id="1afc3-147">**自動更新とライセンス**。</span><span class="sxs-lookup"><span data-stu-id="1afc3-147">**Automatic updates and licensing**.</span></span> <span data-ttu-id="1afc3-148">アプリケーションは、Microsoft Store の組み込みのライセンスと自動更新機能に参加できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-148">Your application can participate in the Microsoft Store's built-in licensing and automatic update facilities.</span></span> <span data-ttu-id="1afc3-149">自動更新機能は、ファイルの変更された部分だけがダウンロードされるため、非常に信頼性が高く効率的なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-149">Automatic update is a highly reliable and efficient mechanism, because only the changed parts of files are downloaded.</span></span>

* <span data-ttu-id="1afc3-150">**リーチの拡大とシンプルな決済**。</span><span class="sxs-lookup"><span data-stu-id="1afc3-150">**Increased reach and simplified monetization**.</span></span> <span data-ttu-id="1afc3-151">そうではないかもしれませんが、Microsoft Store にアプリケーションを配布することを選択した場合は、何百万もの Windows 10 ユーザーに届きます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-151">Maybe not your case but if you choose to distribute your application through the Microsoft Store you reach millions of Windows 10 users.</span></span>

* <span data-ttu-id="1afc3-152">**UWP 機能の追加**。</span><span class="sxs-lookup"><span data-stu-id="1afc3-152">**Add UWP features**.</span></span> <span data-ttu-id="1afc3-153">UWP 機能は、自分のペースでアプリのパッケージに追加できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-153">You can add UWP features to your app's package at your own pace.</span></span>

#### <a name="prepare-for-packaging"></a><span data-ttu-id="1afc3-154">パッケージ化の準備</span><span class="sxs-lookup"><span data-stu-id="1afc3-154">Prepare for packaging</span></span>

<span data-ttu-id="1afc3-155">デスクトップアプリケーションのパッケージ化に進む前に、プロセスを開始する前に対処する必要があるポイントがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-155">Before proceeding to package your desktop application, there are some points you have to address before starting the process.</span></span> <span data-ttu-id="1afc3-156">アプリケーションは、Microsoft Store の規則とポリシーを尊重し、UWP アプリケーションモデルで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-156">Your application must respect any of the Microsoft Store rules and policies and run in the UWP application model.</span></span> <span data-ttu-id="1afc3-157">たとえば、4.6.2 以降の .NET Framework で実行し、レジストリハイブに書き込む必要があり `HKEY_CURRENT_USER` ます。また、AppData フォルダーはユーザー固有のアプリローカルの場所に仮想化されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-157">For example, it has to run on the .NET Framework 4.6.2 or later and writes to the `HKEY_CURRENT_USER` registry hive and the AppData folders will be virtualized to a user-specific app-local location.</span></span>

<span data-ttu-id="1afc3-158">パッケージ化の設計目標は、他のアプリとの互換性を維持しながら、アプリケーションの状態をシステム状態から分離することです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-158">The design goal for packaging is to separate the application state from system state while maintaining compatibility with other apps.</span></span> <span data-ttu-id="1afc3-159">Windows 10 では、アプリケーションを UWP パッケージ内に配置することによって、この目標を達成しています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-159">Windows 10 accomplishes this goal by placing the application inside a UWP package.</span></span> <span data-ttu-id="1afc3-160">実行時にファイルシステムとレジストリにいくつかの変更を検出してリダイレクトすることで、パッケージ化によって提供されるアプリケーションの信頼されたクリーンインストールとアンインストールの動作が保証されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-160">It detects and redirects some changes to the file system and registry at run time to fulfill the promise of a trusted and clean install and uninstall behavior of an application provided by packaging.</span></span>

<span data-ttu-id="1afc3-161">デスクトップアプリケーション用に作成したパッケージは、デスクトップのみの完全に信頼されたアプリケーションであり、およびへの書き込み用にアプリに適用される軽量の仮想化があり `HKCU` `AppData` ます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-161">Packages that you create for your desktop application are desktop-only, full-trust applications that aren't sandboxed, although there's lightweight virtualization applied to the app for writes to `HKCU` and `AppData`.</span></span> <span data-ttu-id="1afc3-162">この仮想化により、従来のデスクトップアプリケーションと同じように、他のアプリと対話することができます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-162">This virtualization allows them to interact with other apps the same way classic desktop applications do.</span></span>

##### <a name="installation"></a><span data-ttu-id="1afc3-163">インストール</span><span class="sxs-lookup"><span data-stu-id="1afc3-163">Installation</span></span>

<span data-ttu-id="1afc3-164">アプリパッケージは *% ProgramFiles% \\ windowsapps \\ package_name* にインストールされます。実行可能ファイルはという名前 `app_name.exe` です。</span><span class="sxs-lookup"><span data-stu-id="1afc3-164">App packages are installed under *%ProgramFiles%\\WindowsApps\\package_name*, with the executable titled `app_name.exe`.</span></span> <span data-ttu-id="1afc3-165">各パッケージフォルダーには、パッケージ `AppxManifest.xml` アプリの特別な XML 名前空間を含むという名前のマニフェストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-165">Each package folder contains a manifest (named `AppxManifest.xml`) that contains a special XML namespace for packaged apps.</span></span> <span data-ttu-id="1afc3-166">マニフェスト ファイル内の `<EntryPoint>` 要素で、完全信頼アプリを参照します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-166">Inside that manifest file is an `<EntryPoint>` element, which references the full-trust app.</span></span> <span data-ttu-id="1afc3-167">アプリケーションが起動されると、アプリコンテナー内で実行されるのではなく、通常どおりユーザーとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-167">When that application is launched, it doesn't run inside an app container, but instead it runs as the user as it normally would.</span></span>

<span data-ttu-id="1afc3-168">展開後、パッケージ ファイルは読み取り専用としてマークされ、オペレーティング システムによって厳重にロックダウンされます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-168">After deployment, package files are marked read-only and heavily locked down by the operating system.</span></span> <span data-ttu-id="1afc3-169">これらのファイルが改ざんされると、Windows によりアプリの起動が回避されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-169">Windows prevents apps from launching if these files are tampered with.</span></span>

##### <a name="file-system"></a><span data-ttu-id="1afc3-170">ファイル システム</span><span class="sxs-lookup"><span data-stu-id="1afc3-170">File system</span></span>

<span data-ttu-id="1afc3-171">OS は、フォルダーの場所に応じて、パッケージデスクトップアプリケーションに対してさまざまなレベルのファイルシステム操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="1afc3-171">The OS supports different levels of file system operations for packaged desktop applications, depending on the folder location.</span></span>

<span data-ttu-id="1afc3-172">ユーザーの *AppData* フォルダーにアクセスしようとすると、システムによって、ユーザーごと、アプリごとのプライベートな場所がバックグラウンドで作成されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-172">When trying to access the user's *AppData* folder, the system creates a private per-user, per-app location behind the scenes.</span></span> <span data-ttu-id="1afc3-173">これにより、実際にプライベートコピーを変更しているときに、パッケージ化されたアプリケーションが実際の *AppData* を編集していると錯覚します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-173">This creates the illusion that the packaged application is editing the real *AppData* when it's actually modifying a private copy.</span></span> <span data-ttu-id="1afc3-174">このように書き込みのリダイレクトを行うことで、アプリによって行われたすべてのファイル変更をシステムで追跡できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-174">By redirecting writes this way, the system can track all file modifications made by the app.</span></span> <span data-ttu-id="1afc3-175">その後、システム "rot" を削除し、ユーザーのアプリケーションの削除エクスペリエンスを向上させるために、これらのファイルをすべてクリーンアップできます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-175">It can then clean all those files when uninstalling reducing system "rot" and providing a better application removal experience for the user.</span></span>

##### <a name="registry"></a><span data-ttu-id="1afc3-176">レジストリ</span><span class="sxs-lookup"><span data-stu-id="1afc3-176">Registry</span></span>

<span data-ttu-id="1afc3-177">アプリケーションパッケージには、実際のレジストリのと同等のものとして機能する、レジストリの .dat ファイルが含まれています。 `HKLM\Software`</span><span class="sxs-lookup"><span data-stu-id="1afc3-177">App packages contain a registry.dat file, which serves as the logical equivalent of `HKLM\Software` in the real registry.</span></span> <span data-ttu-id="1afc3-178">実行時には、この仮想レジストリのハイブの内容がネイティブ システム ハイブにマージされ、両方が一括して表示されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-178">At runtime, this virtual registry merges the contents of this hive into the native system hive to provide a singular view of both.</span></span>

<span data-ttu-id="1afc3-179">すべての書き込みはパッケージのアップグレード中に保持され、アプリケーションがアンインストールされると削除されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-179">All writes are kept during package upgrade and only deleted when the application is uninstalled.</span></span>

##### <a name="uninstallation"></a><span data-ttu-id="1afc3-180">アンインストール</span><span class="sxs-lookup"><span data-stu-id="1afc3-180">Uninstallation</span></span>

<span data-ttu-id="1afc3-181">ユーザーがパッケージをアンインストールすると、の下にあるすべてのファイルとフォルダー `C:\Program Files\WindowsApps\package_name` が削除されます。また、AppData またはプロセス中にキャプチャされたレジストリへのリダイレクトされた書き込みもすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-181">When the user uninstalls a package, all files and folders located under `C:\Program Files\WindowsApps\package_name` are removed, as well as any redirected writes to AppData or the registry that were captured during the process.</span></span>

<span data-ttu-id="1afc3-182">パッケージ化されたアプリケーションがインストール、ファイルアクセス、レジストリ、およびアンインストールを処理する方法の詳細については、「」を参照してください <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> 。</span><span class="sxs-lookup"><span data-stu-id="1afc3-182">For details about how a packaged application handles installation, file access, registry, and uninstallation, see <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes>.</span></span>

<span data-ttu-id="1afc3-183">確認する項目の完全な一覧を取得でき <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> ます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-183">You can get a complete list of things to check on <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare>.</span></span>

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a><span data-ttu-id="1afc3-184">デスクトッププロジェクトに WinRT Api を追加する方法</span><span class="sxs-lookup"><span data-stu-id="1afc3-184">How to add WinRT APIs to your desktop project</span></span>

<span data-ttu-id="1afc3-185">このセクションでは、既存の WPF アプリケーションでトースト通知を統合する方法に関するチュートリアルを紹介します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-185">In this section, you can find a walkthrough on how to integrate Toast Notifications in an existing WPF application.</span></span> <span data-ttu-id="1afc3-186">コードの観点からは単純ですが、プロセス全体を示すのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-186">Although it's simple from the code perspective, it helps illustrate the whole process.</span></span> <span data-ttu-id="1afc3-187">通知は、.NET アプリで使用できる多数の利用可能な WinRT Api の1つです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-187">Notifications are one of the many available WinRT APIs available that you can use in .NET app.</span></span> <span data-ttu-id="1afc3-188">この場合、API にはパッケージ Id が必要です。</span><span class="sxs-lookup"><span data-stu-id="1afc3-188">In this case, the API requires a Package Identity.</span></span> <span data-ttu-id="1afc3-189">Api でパッケージ Id が不要な場合、このプロセスはより簡単です。</span><span class="sxs-lookup"><span data-stu-id="1afc3-189">This process is more straightforward if the APIs don't require Package Identity.</span></span>

<span data-ttu-id="1afc3-190">ファイルを読み取り、その内容を画面に表示する既存の WPF サンプルアプリを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="1afc3-190">Let's take an existing WPF sample app that reads files and shows its contents on the screen.</span></span> <span data-ttu-id="1afc3-191">目標は、アプリケーションの起動時にトースト通知を表示することです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-191">The goal is to display a Toast Notification when the application starts.</span></span>

![サンプルアプリケーションを実行しているスクリーンショット](./media/windows-migration/sample-application.png)

<span data-ttu-id="1afc3-193">最初に、使用する Windows 10 API にパッケージ Id が必要かどうかについて、次のリンクをチェックインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-193">First, you should check in the following link whether the Windows 10 API that you'll use requires a Package Identity:</span></span>

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

<span data-ttu-id="1afc3-194">このサンプルでは、 <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> パッケージ化された id を必要とする API を使用します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-194">Our sample will use the <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> API that requires a packaged identity:</span></span>

![Microsoft ドキュメントの Notification クラス](./media/windows-migration/notification-class-documentation.png)

<span data-ttu-id="1afc3-196">WinRT API にアクセスするには、NuGet パッケージへの参照を追加 `Microsoft.Windows.SDK.Contracts` します。このパッケージは、バックグラウンドでマジックを実行します (詳細については、「」を参照してください <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> )。</span><span class="sxs-lookup"><span data-stu-id="1afc3-196">To access the WinRT API, add a reference to the `Microsoft.Windows.SDK.Contracts` NuGet package and this package will do the magic behind the scenes (see details at <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/>).</span></span>

<span data-ttu-id="1afc3-197">これで、コードの追加を開始する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="1afc3-197">You're now prepared to start adding some code.</span></span>

<span data-ttu-id="1afc3-198">`ShowToastNotification`アプリケーションの起動時に呼び出されるメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-198">Create a `ShowToastNotification` method that will be called on application startup.</span></span> <span data-ttu-id="1afc3-199">XML パターンからトースト通知を構築するだけです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-199">It just builds a toast notification from an XML pattern:</span></span>

```csharp
private void ShowNotification(string title, string content, string image)
{
    string xmlString = $@"<toast><visual><binding template = 'ToastGeneric'><text>{title}</text><text>{content}</text><image src=>'{image}'</image></binding></visual></toast>";
    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);
    ToastNotification toast = new ToastNotification(toastXml);
    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

<span data-ttu-id="1afc3-200">プロジェクトがビルドされますが、通知 API にはパッケージ Id が必要であり、提供されていないため、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-200">Although the project builds, there are errors because the Notifications API requires a Package Identity and you didn't provide it.</span></span> <span data-ttu-id="1afc3-201">Windows パッケージングプロジェクトをソリューションに追加すると、問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-201">Adding a Windows Packaging Project to the solution will fix the issue:</span></span>

![Visual Studio の [新しいプロジェクトの追加] ダイアログのスクリーンショット](./media/windows-migration/add-packaging-project.png)

<span data-ttu-id="1afc3-203">サポートする Windows の最小バージョンとターゲットとするバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-203">Select the minimum Windows version you want to support and the version you're targeting.</span></span> <span data-ttu-id="1afc3-204">すべての WinRT Api がすべての Windows 10 バージョンでサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="1afc3-204">Not all the WinRT APIs are supported in all Windows 10 versions.</span></span> <span data-ttu-id="1afc3-205">Windows 10 の更新プログラムごとに、このバージョンでのみ使用できる新しい Api が追加されます。下位レベルのサポートは使用できません。</span><span class="sxs-lookup"><span data-stu-id="1afc3-205">Each Windows 10 update adds new APIs that are only available from this version; down-level support isn't available.</span></span>

![Windows の最小バージョンの選択](./media/windows-migration/select-versions.png)

<span data-ttu-id="1afc3-207">次の手順では、プロジェクト参照を追加して WPF アプリケーションを Windows パッケージプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-207">Next step is to add the WPF application to the Windows Packaging Project by adding a project reference:</span></span>

![Windows パッケージプロジェクトへの WPF アプリケーションの追加](./media/windows-migration/add-application.png)

![参照マネージャー](./media/windows-migration/reference-manager.png)

<span data-ttu-id="1afc3-210">Windows パッケージプロジェクトでは、いくつかのアプリをパッケージ化できるため、エントリポイントを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-210">A Windows Packaging Project can package several apps so you should set which one is the Entry Point:</span></span>

![エントリポイントの設定](./media/windows-migration/set-entry-point.png)

<span data-ttu-id="1afc3-212">次の手順では、ソリューション構成で WPF プロジェクトをスタートアッププロジェクトとして設定します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-212">Next step is to set the WPF Project as the startup Project in the solution configuration.</span></span> <span data-ttu-id="1afc3-213">F5 キーを押すと、コンパイルしてビルドし、結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-213">You can press F5 to compile and build and see the results.</span></span>

![実行中のサンプルアプリケーションと結果の表示](./media/windows-migration/sample-app-result.png)

<span data-ttu-id="1afc3-215">アプリをインストールできるようにパッケージを生成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="1afc3-215">Let's generate the package so you can install your app.</span></span> <span data-ttu-id="1afc3-216">ストアの [   >  **アプリパッケージの作成**] を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="1afc3-216">Right click on **Store** > **Create App Packages**.</span></span>

![アプリパッケージの作成ダイアログ](./media/windows-migration/create-app-packages.png)

<span data-ttu-id="1afc3-218">サイドローディングオプションを選択して、コンピューターからアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-218">Select the sideloading option to deploy the app from your machine:</span></span>

![サイドローディングオプションの選択](./media/windows-migration/select-sideloading-option.png)

<span data-ttu-id="1afc3-220">アプリのアプリケーションアーキテクチャを選択します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-220">Select the application architecture of your app:</span></span>

![アプリケーションアーキテクチャの選択](./media/windows-migration/select-app-architecture.png)

<span data-ttu-id="1afc3-222">最後に、[ **作成**] をクリックしてパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-222">Finally, create the package by clicking on **Create**.</span></span>

## <a name="xaml-islands"></a><span data-ttu-id="1afc3-223">XAML Islands</span><span class="sxs-lookup"><span data-stu-id="1afc3-223">XAML Islands</span></span>

<span data-ttu-id="1afc3-224">XAML アイランドは、Windows デスクトップ開発者が既存の Win32 アプリケーション (Windows フォームや WPF など) で UWP XAML コントロールを使用できるようにする一連のコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-224">XAML Islands are a set of components that enable Windows desktop developers to use UWP XAML controls on their existing Win32 applications, including Windows Forms and WPF.</span></span>

![XAML アイランドの構造](./media/windows-migration/xaml-islands.png)

<span data-ttu-id="1afc3-226">Win32 アプリには、標準のコントロールと、最新の世界のコントロールを含む UWP UI の "アイランド" を使用してイメージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-226">You can image your Win32 app with your standard controls and among them an "island" of UWP UI containing controls from the modern world.</span></span> <span data-ttu-id="1afc3-227">概念は、のコンテンツを表示する web ページ内に iFrame がある場合と似ています。 `different page.`</span><span class="sxs-lookup"><span data-stu-id="1afc3-227">The concept is similar as having an iFrame inside a web page that shows content from a `different page.`</span></span>

<span data-ttu-id="1afc3-228">Windows 10 Api から機能を追加するだけでなく、XAML アイランドを使用してアプリ内に UWP XAML の部分を追加できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-228">Besides adding functionality from the Windows 10 APIs, you can add pieces of UWP XAML inside of your app using XAML Islands.</span></span>

<span data-ttu-id="1afc3-229">Windows 10 1903 update では、Win32 ウィンドウで UWP XAML コンテンツをホストできるようにする一連の Api が導入されています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-229">Windows 10 1903 update introduces a set of APIs that allows hosting UWP XAML content in Win32 windows.</span></span> <span data-ttu-id="1afc3-230">XAML アイランドを使用できるのは、Windows 10 1903 で実行されているアプリのみです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-230">Only apps running on Windows 10 1903 can use XAML Islands.</span></span>

### <a name="the-road-to-xaml-islands"></a><span data-ttu-id="1afc3-231">XAML アイランドへの道路</span><span class="sxs-lookup"><span data-stu-id="1afc3-231">The road to XAML Islands</span></span>

<span data-ttu-id="1afc3-232">XAML アイランドへの道路は、Microsoft が Win32 アプリ (Windows フォーム、WPF、およびネイティブの Win32 アプリ) を最新化するためのフレームワークとして WinRT Api を導入したときに、2012で開始されました。</span><span class="sxs-lookup"><span data-stu-id="1afc3-232">The road to XAML Islands started in 2012 when Microsoft introduced the WinRT APIs as a framework to modernize the Win32 apps (Windows Forms, WPF, and native Win32 apps).</span></span> <span data-ttu-id="1afc3-233">ただし、WinRT 内の新しい UI コントロールは、新しいアプリケーションでは使用できましたが、既存のアプリケーションでは使用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1afc3-233">However, the new UI controls inside WinRT were available for new applications but not for existing ones.</span></span>

<span data-ttu-id="1afc3-234">2015では、Windows 10 と共に UWP が生まれました。</span><span class="sxs-lookup"><span data-stu-id="1afc3-234">In 2015, along with Windows 10, UWP was born.</span></span> <span data-ttu-id="1afc3-235">UWP を使用すると、XBox、Mobile、Desktop などの Windows デバイス間で動作するアプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-235">UWP allows you to create apps that work across Windows devices like XBox, Mobile, and Desktop.</span></span> <span data-ttu-id="1afc3-236">1年後、Microsoft はデスクトップブリッジ (旧称 Project Centennial) を発表しました。</span><span class="sxs-lookup"><span data-stu-id="1afc3-236">One year later, Microsoft announced Desktop Bridge (formerly known as Project Centennial).</span></span> <span data-ttu-id="1afc3-237">デスクトップブリッジは、開発者が既存の Win32 アプリを Microsoft Store に持ち込むことを可能にする一連のツールです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-237">Desktop Bridge is a set of tools that allowed developers to bring their existing Win32 apps to the Microsoft Store.</span></span> <span data-ttu-id="1afc3-238">より多くの機能が2017に追加されたため、開発者は、アクションセンターでのライブタイルや通知など、新しい Windows 10 Api を活用して Win32 アプリを強化できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-238">More capabilities were added in 2017, allowing developers to enhance their Win32 apps leveraging some of the new Windows 10 APIs, like live tiles and notifications on the action center.</span></span> <span data-ttu-id="1afc3-239">でも、新しい UI コントロールはありません。</span><span class="sxs-lookup"><span data-stu-id="1afc3-239">But still, no new UI controls.</span></span>

<span data-ttu-id="1afc3-240">ビルド2018では、開発者が新しい Windows 10 XAML コントロールを現在の Win32 アプリに使用する方法を発表しました。アプリを UWP に完全に移行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1afc3-240">At Build 2018, Microsoft announced a way for developers to use the new Windows 10 XAML controls into their current Win32 apps, without fully migrating their apps to UWP.</span></span> <span data-ttu-id="1afc3-241">UWP XAML アイランドとしてブランド化されていました。</span><span class="sxs-lookup"><span data-stu-id="1afc3-241">It was branded as UWP XAML Islands.</span></span>

### <a name="how-it-works"></a><span data-ttu-id="1afc3-242">しくみ</span><span class="sxs-lookup"><span data-stu-id="1afc3-242">How it works</span></span>

<span data-ttu-id="1afc3-243">Windows 10 1903 更新プログラムでは、いくつかの XAML ホスティング Api が導入されています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-243">The Windows 10 1903 update introduces several XAML hosting APIs.</span></span> <span data-ttu-id="1afc3-244">そのうちの2つは `WindowsXamlManager` 、と `DesktopWindowXamlSource` です。</span><span class="sxs-lookup"><span data-stu-id="1afc3-244">Two of them are `WindowsXamlManager` and `DesktopWindowXamlSource`.</span></span>

<span data-ttu-id="1afc3-245">クラスは、 `WindowsXamlManager` UWP XAML フレームワークを処理します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-245">The `WindowsXamlManager` class handles the UWP XAML Framework.</span></span> <span data-ttu-id="1afc3-246">この `InitializeForCurrentThread` メソッドは、Win32 アプリの現在のスレッド内の UWP XAML フレームワークを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-246">Its `InitializeForCurrentThread` method loads the UWP XAML Framework inside the current thread of the Win32 app.</span></span>

<span data-ttu-id="1afc3-247">`DesktopWindowXamlSource`は、XAML アイランドコンテンツのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-247">The `DesktopWindowXamlSource` is the instance of your XAML Island content.</span></span> <span data-ttu-id="1afc3-248">このプロパティには、を `Content` インスタンス化して設定するためのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-248">It has the `Content` property, which you're responsible for instantiating and setting.</span></span> <span data-ttu-id="1afc3-249">は、 `DesktopWindowXamlSource` HWND からの入力をレンダリングして取得します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-249">The `DesktopWindowXamlSource` renders and gets its input from an HWND.</span></span> <span data-ttu-id="1afc3-250">XAML アイランドのどの HWND がアタッチされるかを把握しておく必要があります。また、親の HWND のサイズと位置を決定します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-250">It needs to know to which other HWND it will attach the XAML Island's one, and you're responsible for sizing and positioning the parent's HWND.</span></span>

<span data-ttu-id="1afc3-251">WPF や Windows フォーム開発者は、通常は HWND をコード内に処理しないので、HWND ポインターや、Win32 および UWP ワールドを通信するための基になる配線について理解し、処理するのは困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-251">WPF or Windows Forms developers don't usually deal with HWND inside their code, so it may be hard to understand and handle HWND pointers and the underlying wiring stuff to communicate Win32 and UWP worlds.</span></span>

#### <a name="the-xaml-islands-net-wrappers"></a><span data-ttu-id="1afc3-252">XAML アイランド .NET ラッパー</span><span class="sxs-lookup"><span data-stu-id="1afc3-252">The XAML Islands .NET Wrappers</span></span>

<span data-ttu-id="1afc3-253">Windows Community Toolkit には、xaml アイランドを簡単に使用できるようにする WPF または Windows フォーム用の XAML アイランド .NET ラッパーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-253">The Windows Community Toolkit has a set the XAML Islands .NET wrappers for WPF or Windows Forms that make easier to use XAML Islands.</span></span> <span data-ttu-id="1afc3-254">これらのラッパーは、Hwnd、フォーカス管理などを管理します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-254">These wrappers manage the HWNDs, the focus management, among other things.</span></span> <span data-ttu-id="1afc3-255">Windows フォーム WPF 開発者は、これらのラッパーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-255">Windows Forms and WPF developers should use these wrappers.</span></span>

<span data-ttu-id="1afc3-256">Windows Community Toolkit には、ラップされたコントロールとホストコントロールの2種類のコントロールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-256">The Windows Community Toolkit offers two types of controls: Wrapped Controls and Hosting Controls.</span></span>

##### <a name="wrapped-controls"></a><span data-ttu-id="1afc3-257">ラップされたコントロール</span><span class="sxs-lookup"><span data-stu-id="1afc3-257">Wrapped Controls</span></span>

<span data-ttu-id="1afc3-258">これらのラップされたコントロールは、いくつかの UWP コントロールを Windows フォームまたは WPF コントロールにラップし、開発者の UWP の概念を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="1afc3-258">These wrapped controls wrap some UWP controls into Windows Forms or WPF controls, hiding UWP concepts for those developers.</span></span> <span data-ttu-id="1afc3-259">これらのコントロールは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-259">These controls are:</span></span>

* <span data-ttu-id="1afc3-260">WebView と WebViewCompatible</span><span class="sxs-lookup"><span data-stu-id="1afc3-260">WebView and WebViewCompatible</span></span>
* <span data-ttu-id="1afc3-261">System.windows.controls.inkcanvas> と InkToolbar</span><span class="sxs-lookup"><span data-stu-id="1afc3-261">InkCanvas and InkToolbar</span></span>
* <span data-ttu-id="1afc3-262">MediaPlayerElement</span><span class="sxs-lookup"><span data-stu-id="1afc3-262">MediaPlayerElement</span></span>
* <span data-ttu-id="1afc3-263">MapControl</span><span class="sxs-lookup"><span data-stu-id="1afc3-263">MapControl</span></span>

<span data-ttu-id="1afc3-264">パッケージを `Microsoft.Toolkit.Wpf.UI.Controls` プロジェクトに追加し、名前空間への参照を含め、使用を開始します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-264">Add the `Microsoft.Toolkit.Wpf.UI.Controls` package to your project, include the reference to the namespace, and start using them.</span></span>

```xml
<Window
        ...
        xmlns:uwpControls="clr-namespace:Microsoft.Toolkit.Wpf.UI.Controls;assembly=Microsoft.Toolkit.Wpf.UI.Controls">
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="\*"/>
    </Grid.RowDefinitions>
    <uwpControls:InkToolbar TargetInkCanvas="{x:Reference Name=inkCanvas}"/>
    <uwpControls:InkCanvas Grid.Row="1" x:Name="inkCanvas" />
</Grid>
```

##### <a name="hosting-controls"></a><span data-ttu-id="1afc3-265">ホスト (コントロールを)</span><span class="sxs-lookup"><span data-stu-id="1afc3-265">Hosting controls</span></span>

<span data-ttu-id="1afc3-266">XAML アイランドの機能は、ほとんどのファーストパーティ製のコントロール、サードパーティのコントロール、および UWP 用に開発されたカスタムコントロールに拡張され、完全に機能する UI を備えた "アイランド" として Windows フォームおよび WPF に統合できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-266">The power of XAML Islands extends to most first-party controls, third-party controls, and custom controls developed for UWP, which can be integrated into Windows Forms and WPF as "Islands" with fully functional UI.</span></span> <span data-ttu-id="1afc3-267">`WindowsXamlHost`WPF と Windows フォームのコントロールを使用すると、この操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-267">The `WindowsXamlHost` control for WPF and Windows Forms allows doing this.</span></span>

<span data-ttu-id="1afc3-268">たとえば、WPF でコントロールを使用するには、 `WindowsXamlHost` `Microsoft.Toolkit.Wpf.UI.XamlHost` Windows Community Toolkit によって提供されるパッケージへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-268">For example, to use the `WindowsXamlHost` control in WPF, add a reference to the `Microsoft.Toolkit.Wpf.UI.XamlHost` package provided by the Windows Community Toolkit.</span></span>

<span data-ttu-id="1afc3-269">を `WindowsXamlHost` UI コードに配置したら、読み込む UWP の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-269">Once you've placed your `WindowsXamlHost` into your UI code, specify which UWP type you want to load.</span></span> <span data-ttu-id="1afc3-270">`Button`カスタム UWP コントロールである複数の異なるコントロールによって構成される、、またはより複雑なコントロールを使用するように選択できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-270">You can choose to use a wrapped control like a `Button` or a more complex one composed by several different controls, which are a custom UWP control.</span></span>

<span data-ttu-id="1afc3-271">次の例は、UWP を追加する方法を示してい `Button` ます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-271">The following example shows how to add a UWP `Button`:</span></span>

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

<span data-ttu-id="1afc3-272">これにアプローチする方法について明確な推奨事項があります。また、1つのコントロールに複数のアイランドを持たせるよりも、カスタム複合コントロールを含む1つの大きな XAML アイランドを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1afc3-272">There's a clear recommendation on how to approach this and it's better to have one single and bigger XAML Island containing a custom composite control than to have several islands with one control on each.</span></span>

<span data-ttu-id="1afc3-273">XAML のコア機能の1つはバインドであり、Win32 コードと島の間で機能します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-273">One of the core features of XAML is binding and it works between your Win32 code and the island.</span></span> <span data-ttu-id="1afc3-274">そのため、たとえば、UWP と共に Win32 をバインドでき `Textbox` `Textbox` ます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-274">So, you can bind, for instance, a Win32 `Textbox` with a UWP `Textbox`.</span></span> <span data-ttu-id="1afc3-275">考慮すべき重要な点の1つとして、これらのバインディングは UWP から Win32 までの一方向のバインディングであるため、XAML アイランド内でを更新すると、 `Textbox` Win32 のテキストボックスが更新されますが、その他の方法は更新されません。</span><span class="sxs-lookup"><span data-stu-id="1afc3-275">One important thing to consider is that these bindings are one-way bindings, from UWP to Win32, so if you update the `Textbox` inside the XAML Island the Win32 Textbox will be updated, but not the other way around.</span></span>

<span data-ttu-id="1afc3-276">XAML アイランドの使用方法に関するチュートリアルについては、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1afc3-276">To see a walkthrough about how to use XAML Islands, see:</span></span>

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a><span data-ttu-id="1afc3-277">UWP XAML カスタムコントロールの追加</span><span class="sxs-lookup"><span data-stu-id="1afc3-277">Adding UWP XAML custom controls</span></span>

<span data-ttu-id="1afc3-278">XAML カスタムコントロールは、ユーザーまたはサードパーティ (WinUI 2.x コントロールを含む) によって作成されたコントロール (またはユーザーコントロール) です。</span><span class="sxs-lookup"><span data-stu-id="1afc3-278">A XAML custom control is a control (or user control) created by you or by third parties (including WinUI 2.x controls).</span></span> <span data-ttu-id="1afc3-279">Windows フォームまたは WPF アプリでカスタム UWP コントロールをホストするには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="1afc3-279">To host a custom UWP control in a Windows Forms or WPF app, you'll need:</span></span>

- <span data-ttu-id="1afc3-280">`WindowsXamlHost`.Net アプリで UWP コントロールを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="1afc3-280">To use the `WindowsXamlHost` UWP control in your .NET app.</span></span>
- <span data-ttu-id="1afc3-281">オブジェクトを定義する UWP アプリプロジェクトを作成するには `XamlApplication`</span><span class="sxs-lookup"><span data-stu-id="1afc3-281">To create a UWP app project that defines a `XamlApplication` object.</span></span>

<span data-ttu-id="1afc3-282">WPF または Windows フォームプロジェクトは、 `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` Windows Community Toolkit によって提供されるクラスのインスタンスにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-282">Your WPF or Windows Forms project must have access to an instance of the `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` class provided by the Windows Community Toolkit.</span></span> <span data-ttu-id="1afc3-283">このオブジェクトは、アプリケーションの現在のディレクトリにあるアセンブリ内のカスタム UWP XAML 型のメタデータを読み込むためのルートメタデータプロバイダーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-283">This object acts as a root metadata provider for loading metadata for custom UWP XAML types in assemblies in the current directory of your application.</span></span> <span data-ttu-id="1afc3-284">これを行うには、WPF または Windows フォームプロジェクトと同じソリューションに空のアプリ (ユニバーサル Windows) プロジェクトを追加し、このプロジェクトの既定のアプリクラスを変更します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-284">The recommended way to do this is to add a Blank App (Universal Windows) project to the same solution as your WPF or Windows Forms project and revise the default App class in this project.</span></span>

<span data-ttu-id="1afc3-285">カスタム UWP XAML コントロールは、この UWP アプリまたは WPF または Windows フォームプロジェクトと同じソリューションで参照する独立した UWP クラスライブラリプロジェクトに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-285">The custom UWP XAML control can be included on this UWP app or in an independent UWP Class Library project that you reference in the same solution as your WPF or Windows Forms project.</span></span>

<span data-ttu-id="1afc3-286">詳細な手順については、「」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1afc3-286">You can check a detailed step-by-step process description at:</span></span>

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a><span data-ttu-id="1afc3-287">Windows UI ライブラリ (WinUI 2)</span><span class="sxs-lookup"><span data-stu-id="1afc3-287">The Windows UI Library (WinUI 2)</span></span>

<span data-ttu-id="1afc3-288">OS に付属する受信トレイの Windows 10 コントロール以外にも、同じ UWP XAML チームが Windows UI ライブラリ (**WinUI 2**) で追加のコントロールを提供します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-288">Besides the inbox Windows 10 controls that comes with the OS, the same UWP XAML team also deliver additional controls in the Windows UI Library (**WinUI 2**).</span></span> <span data-ttu-id="1afc3-289">WinUI 2 は、Windows UWP アプリ用のネイティブな Microsoft UI コントロールおよび機能を提供します。これらのコントロールは、XAML アイランドの内部で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-289">WinUI 2 provides official native Microsoft UI controls and features for Windows UWP apps and these controls can be used inside of XAML Islands.</span></span>

<span data-ttu-id="1afc3-290">WinUI 2 はオープンソースであり、に関する情報を見つけることができ <https://github.com/microsoft/microsoft-ui-xaml> ます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-290">WinUI 2 is open source and you can find information at <https://github.com/microsoft/microsoft-ui-xaml>.</span></span>

<span data-ttu-id="1afc3-291">次の記事では、WinUI 2 ライブラリから UWP XAML コントロールをホストする方法について説明します。 <https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands></span><span class="sxs-lookup"><span data-stu-id="1afc3-291">The following article demonstrates how to host a UWP XAML control from the WinUI 2 library: <https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands></span></span>

### <a name="do-you-need-xaml-islands"></a><span data-ttu-id="1afc3-292">XAML アイランドが必要です</span><span class="sxs-lookup"><span data-stu-id="1afc3-292">Do you need XAML Islands</span></span>

<span data-ttu-id="1afc3-293">XAML アイランドは、アプリを完全に書き換えずに新しい UWP コントロールと動作を利用することで、ユーザーエクスペリエンスを向上させる既存の Win32 アプリを対象としています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-293">XAML Islands are intended for existing Win32 apps that want to improve their user experience by leveraging new UWP controls and behaviors without a full rewrite of the app.</span></span> <span data-ttu-id="1afc3-294">[Windows 10 api](/windows/uwp/porting/desktop-to-uwp-enhance)は既に利用できますが、XAML アイランドまでは UI に関連しない api のみを利用できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-294">You could already [leverage Windows 10 APIs](/windows/uwp/porting/desktop-to-uwp-enhance), but up until XAML Islands, only non-UI related APIs.</span></span>

<span data-ttu-id="1afc3-295">新しい Windows アプリを開発している場合は、 [UWP アプリ](/windows/uwp/get-started/universal-application-platform-guide) が適切な方法であると思います。</span><span class="sxs-lookup"><span data-stu-id="1afc3-295">If you're developing a new Windows App, a [UWP App](/windows/uwp/get-started/universal-application-platform-guide) is probably the right approach.</span></span>

### <a name="the-road-ahead-xaml-islands-winui-30"></a><span data-ttu-id="1afc3-296">先行する XAML アイランド: WinUI 3.0</span><span class="sxs-lookup"><span data-stu-id="1afc3-296">The road ahead XAML Islands: WinUI 3.0</span></span>

<span data-ttu-id="1afc3-297">Windows 8 以降では、windows UI プラットフォーム (XAML UI フレームワーク、ビジュアルコンポジションレイヤー、入力処理など) が Windows の不可欠な部分として出荷されています。</span><span class="sxs-lookup"><span data-stu-id="1afc3-297">Since Windows 8, the Windows UI platform, including the XAML UI framework, visual composition layer, and input processing has been shipped as an integral part of Windows.</span></span> <span data-ttu-id="1afc3-298">これは、UI テクノロジの最新の機能強化を活用するために、最新バージョンの UI にアップグレードする必要があることを意味します。これにより、アプリの開発時にイノベーションの速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-298">This means that to benefit from the latest improvements on UI technologies, you must upgrade to the latest version of the UI, slowing down the pace of innovation when you develop your apps.</span></span> <span data-ttu-id="1afc3-299">この2つの進化サイクルを分離し、イノベーションを促進するために、Microsoft は、WinUI プロジェクトに積極的に取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-299">To decouple these two evolution cycles and foster innovation, Microsoft is actively working on the WinUI project.</span></span>

<span data-ttu-id="1afc3-300">2018年2月2日以降、Microsoft は、UWP SDK に基づいて構築された別の NuGet パッケージとして、いくつかの新しい XAML UI コントロールと機能の配布を開始しました。</span><span class="sxs-lookup"><span data-stu-id="1afc3-300">Starting with WinUI 2 in 2018, Microsoft started shipping some new XAML UI controls and features as separate NuGet packages that build on top of the UWP SDK.</span></span>

![WinUI 2.0 の構造](./media/windows-migration/winui2.png)

<span data-ttu-id="1afc3-302">WinUI 3 は、アクティブな開発中であり、WinUI の範囲を大幅に拡大して、UWP SDK から完全に分離される完全な UI プラットフォームを追加します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-302">WinUI 3 is under active development and will greatly expand the scope of WinUI to include the full UI platform, which will be fully decoupled from the UWP SDK:</span></span>

![WinUI 3.0 の構造](./media/windows-migration/winui3.png)

<span data-ttu-id="1afc3-304">XAML フレームワークは、GitHub で開発され、 [NuGet](/nuget/what-is-nuget) パッケージとして帯域外で出荷されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1afc3-304">XAML framework will now be developed on GitHub and shipped out of band as [NuGet](/nuget/what-is-nuget) packages.</span></span>

<span data-ttu-id="1afc3-305">OS の一部として同梱されている既存の UWP XAML API に対して、新しい機能更新プログラムが提供されることはなくなります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-305">The existing UWP XAML APIs that ship as part of the OS will no longer receive new feature updates.</span></span> <span data-ttu-id="1afc3-306">Windows 10 のサポートライフサイクルに従って、セキュリティ更新プログラムと重要な修正プログラムが引き続き提供されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-306">They will still receive security updates and critical fixes according to the Windows 10 support lifecycle.</span></span>

<span data-ttu-id="1afc3-307">ユニバーサル Windows プラットフォームには、XAML フレームワークだけでなく (アプリケーションとセキュリティモデル、メディアパイプライン、Xbox と Windows 10 シェルの統合、広範なデバイスのサポート) が含まれており、進化し続ける予定です。</span><span class="sxs-lookup"><span data-stu-id="1afc3-307">The Universal Windows Platform contains more than just the XAML framework (for example, application and security model, media pipeline, Xbox and Windows 10 shell integrations, broad device support) and will continue to evolve.</span></span> <span data-ttu-id="1afc3-308">新しい XAML 機能はすべて、代わりに WinUI の一部として開発および出荷されます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-308">All new XAML features will just be developed and ship as part of WinUI instead.</span></span>

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a><span data-ttu-id="1afc3-309">デスクトップアプリと WinUI XAML アイランドの WinUI 3</span><span class="sxs-lookup"><span data-stu-id="1afc3-309">WinUI 3 in desktop app and WinUI XAML Islands</span></span>

<span data-ttu-id="1afc3-310">ご覧のように、WinUI 3 は UWP XAML の進化であり、UWP アプリモデルとすべての要件 (MSIX パッケージ ID、サンドボックス、CoreWindow など) で自然に機能します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-310">As you can see, WinUI 3 is the evolution of UWP XAML and it works naturally within the UWP app model and all its requirements (MSIX packaged ID, sandbox, CoreWindow, and so on.</span></span> <span data-ttu-id="1afc3-311">Win32 アプリモデルで WinUI 3 だけを使用するには、winui **XAML アイランド** を使用して、winui コンテンツを別の UI フレームワーク (WINDOWS フォーム、WPF など) でホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-311">To use just WinUI 3 in a Win32 app model, the WinUI content should be hosted by another UI Framework (Windows Forms, WPF, and so on) using **WinUI XAML Islands**.</span></span> <span data-ttu-id="1afc3-312">これは、アプリを進化させ、テクノロジを混在させる場合の正しいパスです。</span><span class="sxs-lookup"><span data-stu-id="1afc3-312">This is the right path if you want to evolve your app and mix technologies.</span></span> <span data-ttu-id="1afc3-313">ただし、WinUI の古い UI 全体を置き換える場合、アプリでは、WinUI をホストするための UI フレームワークを読み込まないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1afc3-313">However, if you want to replace your entire old UI for WinUI, your app shouldn't load UI Frameworks for just hosting WinUI.</span></span>

<span data-ttu-id="1afc3-314">WinUI 3 は **、デスクトップアプリでの winui の追加に** 関するこの重要なフィードバックに対処します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-314">WinUI 3 will address this critical feedback adding **WinUI in desktop apps**.</span></span> <span data-ttu-id="1afc3-315">これにより、Win32 アプリは、スタンドアロン UI フレームワークとして、WinUI 3 を使用できるようになります。Windows フォームまたは WPF を読み込む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1afc3-315">This will allow that Win32 apps can use WinUI 3 as standalone UI Framework; no need to load Windows Forms or WPF.</span></span>

<span data-ttu-id="1afc3-316">この集計では、WinUI 3 を使用すると、開発者は次のような組み合わせを簡単に組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-316">Within this aggregation, WinUI 3 will let developers easily mix and match the right combination of:</span></span>

* <span data-ttu-id="1afc3-317">アプリモデル: UWP、Win32</span><span class="sxs-lookup"><span data-stu-id="1afc3-317">App model: UWP, Win32</span></span>
* <span data-ttu-id="1afc3-318">プラットフォーム: .NET またはネイティブ</span><span class="sxs-lookup"><span data-stu-id="1afc3-318">Platform: .NET or Native</span></span>
* <span data-ttu-id="1afc3-319">言語: .NET (C \# 、Visual Basic)、標準 C++</span><span class="sxs-lookup"><span data-stu-id="1afc3-319">Language: .NET (C\#, Visual Basic), standard C++</span></span>
* <span data-ttu-id="1afc3-320">パッケージング: MSIX、Microsoft Store の AppX、パッケージ化されていません。</span><span class="sxs-lookup"><span data-stu-id="1afc3-320">Packaging: MSIX, AppX for the Microsoft Store, unpackaged</span></span>
* <span data-ttu-id="1afc3-321">相互運用: winui 3 を使用して、既存の WPF、WinForms、および MFC アプリを、WinUI XAML アイランドを使用して拡張します。</span><span class="sxs-lookup"><span data-stu-id="1afc3-321">Interop: use WinUI 3 to extend existing WPF, WinForms, and MFC apps using WinUI XAML Islands.</span></span>

<span data-ttu-id="1afc3-322">詳細を知りたい場合は、Microsoft がこのロードマップをで共有してい <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> ます。</span><span class="sxs-lookup"><span data-stu-id="1afc3-322">If you want to know more details, Microsoft is sharing this roadmap in <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1afc3-323">[前へ](migrate-modern-applications.md)
>[次へ](example-migration.md)</span><span class="sxs-lookup"><span data-stu-id="1afc3-323">[Previous](migrate-modern-applications.md)
[Next](example-migration.md)</span></span>
