---
title: Windows 10 の移行
description: パッケージ化や XAML Islands などの Windows 10 の機能について詳しく説明します。
ms.date: 12/29/2020
ms.openlocfilehash: 139a8f2354803dafeb0178b4dbfb57a95c4ddb34
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "98615946"
---
# <a name="windows-10-migration"></a><span data-ttu-id="57044-103">Windows 10 の移行</span><span class="sxs-lookup"><span data-stu-id="57044-103">Windows 10 migration</span></span>

<span data-ttu-id="57044-104">次のような状況を考えてみます。Windows 7 時代に開発された動作中のデスクトップ アプリケーションがあります。</span><span class="sxs-lookup"><span data-stu-id="57044-104">Consider the following situation: You have a working desktop application that was developed in the Windows 7 days.</span></span> <span data-ttu-id="57044-105">当時利用可能な WPF テクノロジが使われており、問題なく動作しますが、Windows 10 で実行した場合に、UI と動作が古くなっています。</span><span class="sxs-lookup"><span data-stu-id="57044-105">It's using WPF technology available at that time and working fine but it has an outdated UI and behaviors when you run it on Windows 10.</span></span> <span data-ttu-id="57044-106">これは、マトリックスなどの未来的な映画を鑑賞していて、ネオが Nokia 8110 デバイスを使用しているのに気付くようなものです。</span><span class="sxs-lookup"><span data-stu-id="57044-106">It is like when you watch a futuristic movie like Matrix and you see Neo using the Nokia 8110 device.</span></span> <span data-ttu-id="57044-107">映画は 20 年後でも十分に有効ですが、デバイスを現代化した方がメリットがあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="57044-107">The film works great after 20 years but it would rather benefit from a device modernization.</span></span>

<span data-ttu-id="57044-108">Windows 10 のリリースによって、Microsoft では、これまで、タブレットやタッチ デバイスのようなシナリオをサポートし、Microsoft オペレーティング システムのユーザーに最高のエクスペリエンスを提供するために、多くのイノベーションを導入してきました。</span><span class="sxs-lookup"><span data-stu-id="57044-108">With the release of Windows 10, Microsoft introduced many innovations to support scenarios like tablets and touch devices and to provide the best experience for users for a Microsoft operating system ever.</span></span> <span data-ttu-id="57044-109">たとえば、次のようなことができます。</span><span class="sxs-lookup"><span data-stu-id="57044-109">For example, you can:</span></span>

- <span data-ttu-id="57044-110">Windows Hello を使用して顔でサインインする。</span><span class="sxs-lookup"><span data-stu-id="57044-110">Sign in with your face using Windows Hello.</span></span>
- <span data-ttu-id="57044-111">ペンを使用して、テキストを描画または手書き入力すると、自動的に認識され、デジタル化される。</span><span class="sxs-lookup"><span data-stu-id="57044-111">Use a pen to draw or handwrite text that is automatically recognized and digitalized.</span></span>
- <span data-ttu-id="57044-112">WinML を使用して、クラウドに構築されたローカルでカスタマイズされた AI モデルを実行する。</span><span class="sxs-lookup"><span data-stu-id="57044-112">Run locally customized AI models built on the cloud using WinML.</span></span>

<span data-ttu-id="57044-113">これらのすべての機能は、Windows ランタイム (WinRT) ライブラリを通じて Windows 開発者が使用できます。</span><span class="sxs-lookup"><span data-stu-id="57044-113">All these features are enabled for Windows developers through Windows Runtime (WinRT) libraries.</span></span> <span data-ttu-id="57044-114">ライブラリは .NET Framework と .NET の両方に公開されているため、これらの機能を既存のデスクトップ アプリで利用できます。</span><span class="sxs-lookup"><span data-stu-id="57044-114">You can take advantage of these features in your existing desktop apps because the libraries are exposed to both the .NET Framework and .NET as well.</span></span> <span data-ttu-id="57044-115">XAML Islands を使用して UI を現代化し、時代に即してアプリのビジュアルと動作を改善することもできます。</span><span class="sxs-lookup"><span data-stu-id="57044-115">You can even modernize your UI with the use of XAML Islands and improve the visuals and behavior of your apps according to the times.</span></span>

<span data-ttu-id="57044-116">ここで注意すべき重要な点の 1 つは、この現代化のパスに従うために、.NET Framework テクノロジを捨てる必要がないことです。</span><span class="sxs-lookup"><span data-stu-id="57044-116">One important thing to note here is that you don't need to abandon .NET Framework technology to follow this modernization path.</span></span> <span data-ttu-id="57044-117">.NET に移行する負担もなく、安全に現在の状態に留まり、Windows 10 のすべての利点を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="57044-117">You can safely stay on there and have all the benefits of Windows 10 without the pressure to migrate to .NET.</span></span> <span data-ttu-id="57044-118">そのように、現代化のパスを選択する能力と柔軟性の両方が得られます。</span><span class="sxs-lookup"><span data-stu-id="57044-118">So, you get both the power and the flexibility to choose your modernization path.</span></span>

## <a name="winrt-apis"></a><span data-ttu-id="57044-119">WinRT API</span><span class="sxs-lookup"><span data-stu-id="57044-119">WinRT APIs</span></span>

<span data-ttu-id="57044-120">WinRT API は、Windows 10 開発者が、オペレーティング システムで提供する必要があるすべてのものにアクセスできるようにする、オブジェクト指向の適切に構造化されたアプリケーション プログラミング インターフェイス (API) です。</span><span class="sxs-lookup"><span data-stu-id="57044-120">WinRT APIs are object-oriented, well-structured application programming interfaces (APIs) that give Windows 10 developers access to everything the operating system has to offer.</span></span> <span data-ttu-id="57044-121">WinRT API を使用して、特に、プッシュ通知、デバイス API、Microsoft Ink、WinML などの機能をデスクトップ アプリに組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="57044-121">Through WinRT APIs, you can integrate functionalities like Push Notifications, Device APIs, Microsoft Ink, and WinML, among others on your desktop apps.</span></span>

<span data-ttu-id="57044-122">一般に、WinRT API は従来のデスクトップ アプリから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="57044-122">In general, WinRT APIs can be called from a classic desktop app.</span></span> <span data-ttu-id="57044-123">ただし、次の 2 つの主な領域に、この規則の例外が存在します。</span><span class="sxs-lookup"><span data-stu-id="57044-123">However, two main areas present an exception to this rule:</span></span>

* <span data-ttu-id="57044-124">パッケージ ID が必要な API。</span><span class="sxs-lookup"><span data-stu-id="57044-124">APIs that require a package identity.</span></span>
* <span data-ttu-id="57044-125">XAML や Composition などの視覚化を必要とする API。</span><span class="sxs-lookup"><span data-stu-id="57044-125">APIs that require visualization like XAML or Composition.</span></span>

### <a name="universal-windows-platform-uwp-packages"></a><span data-ttu-id="57044-126">ユニバーサル Windows プラットフォーム (UWP) パッケージ</span><span class="sxs-lookup"><span data-stu-id="57044-126">Universal Windows Platform (UWP) packages</span></span>

#### <a name="application-package-identity"></a><span data-ttu-id="57044-127">アプリケーション パッケージ ID</span><span class="sxs-lookup"><span data-stu-id="57044-127">Application Package Identity</span></span>

<span data-ttu-id="57044-128">UWP アプリには、OS によってアプリケーションのインストールとアンインストールを管理するデプロイ システムがあります。</span><span class="sxs-lookup"><span data-stu-id="57044-128">UWP apps have a deployment system where the OS manages the installation and uninstallation of application.</span></span> <span data-ttu-id="57044-129">それには、インストールを宣言型にする必要があります。つまり、インストール中にユーザー コードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="57044-129">That requires the installation to be declarative, meaning that no user code is executed during install.</span></span> <span data-ttu-id="57044-130">代わりに、アプリでシステムと統合する必要があるすべてのもの (プロトコル、ファイルの種類、拡張機能など) をアプリケーション マニフェストで宣言します。</span><span class="sxs-lookup"><span data-stu-id="57044-130">Instead, everything the app wants to integrate with the system, such as protocols, file types, and extensions, is declared in the application manifest.</span></span> <span data-ttu-id="57044-131">デプロイ時に、デプロイ パイプラインによってそれらの統合ポイントが構成されます。</span><span class="sxs-lookup"><span data-stu-id="57044-131">At deployment time, the deployment pipeline configures those integration points.</span></span> <span data-ttu-id="57044-132">OS でこのすべての機能を管理し、それを追跡する唯一の方法は、"パッケージ" ごとに、アプリケーションの一意の識別子である ID を持つことです。</span><span class="sxs-lookup"><span data-stu-id="57044-132">The only way for the OS to manage all this functionality and keep track of it is for each 'package' to have an identity, a unique identifier for the application.</span></span>

<span data-ttu-id="57044-133">一部の WinRT API では、このパッケージ ID が想定どおりに動作することを必要とします。</span><span class="sxs-lookup"><span data-stu-id="57044-133">Some WinRT APIs require this package identity to work as expected.</span></span> <span data-ttu-id="57044-134">ただし、ネイティブ C++ や .NET アプリなどの従来のデスクトップ アプリでは、パッケージ ID を必要としない異なるデプロイ システムが使用されています。</span><span class="sxs-lookup"><span data-stu-id="57044-134">However, classic desktop apps like native C++ or .NET apps, use different deployment systems that don't require a package identity.</span></span> <span data-ttu-id="57044-135">これらの WinRT API をデスクトップ アプリケーションで使用する場合は、それらにパッケージ ID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57044-135">If you want to use these WinRT APIs in your desktop application, you need to provide them a package identity.</span></span>

<span data-ttu-id="57044-136">続行する 1 つの方法は、追加のパッケージ化プロジェクトを構築することです。</span><span class="sxs-lookup"><span data-stu-id="57044-136">One way to proceed is to build an additional packaging project.</span></span> <span data-ttu-id="57044-137">パッケージ化プロジェクト内で、元のソース コード プロジェクトを指し、提供する ID 情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="57044-137">Inside the packaging project, you point to the original source code project and specify the Identity information you want to provide.</span></span> <span data-ttu-id="57044-138">パッケージをインストールし、インストールされたアプリを実行すると、自動的に ID が取得され、ID を必要とするすべての WinRT API をコードで呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="57044-138">If you install the package and run the installed app, it will automatically get an identify enabling your code to call all WinRT APIs requiring Identity.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

<span data-ttu-id="57044-139">どの API でパッケージ化されたアプリケーション ID を必要とするかをチェックするには、API を含む型が [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) 属性でマークされているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="57044-139">You can check which APIs need a packaged application identity by inspecting if the type that contains the API is marked with the [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) attribute.</span></span> <span data-ttu-id="57044-140">そうであれば、パッケージ化されていない従来のデスクトップ アプリからそれを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="57044-140">If it is, you can call if from an unpackaged traditional desktop app.</span></span> <span data-ttu-id="57044-141">そうでない場合は、パッケージ化プロジェクトを使用して、従来のデスクトップ アプリを UWP に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57044-141">Otherwise, you must convert your classic desktop app to a UWP with the help of a packaging project.</span></span>

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a><span data-ttu-id="57044-142">パッケージ化の利点</span><span class="sxs-lookup"><span data-stu-id="57044-142">Benefits of packaging</span></span>

<span data-ttu-id="57044-143">これらの API へのアクセスを提供するだけでなく、次のようなデスクトップ アプリケーション用の Windows アプリ パッケージを作成することによって、いくつかの追加の利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="57044-143">Besides giving you access to these APIs, you get some additional benefits by creating a Windows App package for your desktop application including:</span></span>

* <span data-ttu-id="57044-144">**効率的なデプロイ**。</span><span class="sxs-lookup"><span data-stu-id="57044-144">**Streamlined deployment**.</span></span> <span data-ttu-id="57044-145">アプリには、ユーザーが自信を持ってアプリケーションをインストールして更新できるようにするための優れたデプロイ エクスペリエンスがあります。</span><span class="sxs-lookup"><span data-stu-id="57044-145">Apps have a great deployment experience ensuring that users can confidently install an application and update it.</span></span> <span data-ttu-id="57044-146">ユーザーがアプリをアンインストールすることを選択した場合、それは跡形もなく完全に削除され、Windows の rot (腐敗) 問題を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="57044-146">If a user chooses to uninstall the app, it's removed completely with no trace left behind preventing the Windows rot problem.</span></span>

* <span data-ttu-id="57044-147">**自動更新とライセンス**。</span><span class="sxs-lookup"><span data-stu-id="57044-147">**Automatic updates and licensing**.</span></span> <span data-ttu-id="57044-148">アプリケーションは、Microsoft Store の組み込みライセンスと自動更新機能に参加できます。</span><span class="sxs-lookup"><span data-stu-id="57044-148">Your application can participate in the Microsoft Store's built-in licensing and automatic update facilities.</span></span> <span data-ttu-id="57044-149">自動更新機能は、ファイルの変更された部分だけがダウンロードされるため、非常に信頼性が高く効率的なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="57044-149">Automatic update is a highly reliable and efficient mechanism, because only the changed parts of files are downloaded.</span></span>

* <span data-ttu-id="57044-150">**リーチの拡大とシンプルな決済**。</span><span class="sxs-lookup"><span data-stu-id="57044-150">**Increased reach and simplified monetization**.</span></span> <span data-ttu-id="57044-151">当てはまらないかもしれませんが、Microsoft Store を通じてアプリケーションを配布することを選択すると、何百万もの Windows 10 ユーザーに到達できます。</span><span class="sxs-lookup"><span data-stu-id="57044-151">Maybe not your case but if you choose to distribute your application through the Microsoft Store you reach millions of Windows 10 users.</span></span>

* <span data-ttu-id="57044-152">**UWP 機能の追加**。</span><span class="sxs-lookup"><span data-stu-id="57044-152">**Add UWP features**.</span></span> <span data-ttu-id="57044-153">UWP 機能は、自分のペースでアプリのパッケージに追加できます。</span><span class="sxs-lookup"><span data-stu-id="57044-153">You can add UWP features to your app's package at your own pace.</span></span>

#### <a name="prepare-for-packaging"></a><span data-ttu-id="57044-154">パッケージ化の準備</span><span class="sxs-lookup"><span data-stu-id="57044-154">Prepare for packaging</span></span>

<span data-ttu-id="57044-155">デスクトップ アプリケーションのパッケージ化に進む前に、プロセスを開始する前に対処する必要があるポイントがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="57044-155">Before proceeding to package your desktop application, there are some points you have to address before starting the process.</span></span> <span data-ttu-id="57044-156">アプリケーションでは、Microsoft Store のすべての規則とポリシーを遵守し、UWP アプリケーション モデルで実行される必要があります。</span><span class="sxs-lookup"><span data-stu-id="57044-156">Your application must respect any of the Microsoft Store rules and policies and run in the UWP application model.</span></span> <span data-ttu-id="57044-157">たとえば、それは 4.6.2 以降の .NET Framework で実行され、`HKEY_CURRENT_USER` レジストリ ハイブに書き込まれる必要があるため、AppData フォルダーはユーザー固有のアプリローカルの場所に仮想化されます。</span><span class="sxs-lookup"><span data-stu-id="57044-157">For example, it has to run on the .NET Framework 4.6.2 or later and writes to the `HKEY_CURRENT_USER` registry hive and the AppData folders will be virtualized to a user-specific app-local location.</span></span>

<span data-ttu-id="57044-158">パッケージ化の設計目標は、他のアプリとの互換性を維持しながら、アプリケーションの状態をシステム状態から分離することです。</span><span class="sxs-lookup"><span data-stu-id="57044-158">The design goal for packaging is to separate the application state from system state while maintaining compatibility with other apps.</span></span> <span data-ttu-id="57044-159">Windows 10 では、アプリケーションを UWP パッケージ内に配置することによって、この目標を達成しています。</span><span class="sxs-lookup"><span data-stu-id="57044-159">Windows 10 accomplishes this goal by placing the application inside a UWP package.</span></span> <span data-ttu-id="57044-160">実行時にファイル システムとレジストリへのいくつかの変更が検出され、リダイレクトされることで、パッケージ化によって提供されるアプリケーションの信頼されたクリーン インストールとアンインストールの動作の約束が果たされます。</span><span class="sxs-lookup"><span data-stu-id="57044-160">It detects and redirects some changes to the file system and registry at run time to fulfill the promise of a trusted and clean install and uninstall behavior of an application provided by packaging.</span></span>

<span data-ttu-id="57044-161">デスクトップ アプリケーション用に作成したパッケージは、サンドボックス化されないデスクトップ専用の完全に信頼できるアプリケーションですが、`HKCU` および `AppData` への書き込みに、軽量の仮想化がアプリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="57044-161">Packages that you create for your desktop application are desktop-only, full-trust applications that aren't sandboxed, although there's lightweight virtualization applied to the app for writes to `HKCU` and `AppData`.</span></span> <span data-ttu-id="57044-162">この仮想化により、従来のデスクトップ アプリケーションと同じように、他のアプリと連携することができます。</span><span class="sxs-lookup"><span data-stu-id="57044-162">This virtualization allows them to interact with other apps the same way classic desktop applications do.</span></span>

##### <a name="installation"></a><span data-ttu-id="57044-163">インストール</span><span class="sxs-lookup"><span data-stu-id="57044-163">Installation</span></span>

<span data-ttu-id="57044-164">アプリ パッケージは、`app_name.exe` という名前の実行可能ファイルで、 *%ProgramFiles%\\WindowsApps\\package_name* の下にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="57044-164">App packages are installed under *%ProgramFiles%\\WindowsApps\\package_name*, with the executable titled `app_name.exe`.</span></span> <span data-ttu-id="57044-165">各パッケージ フォルダーには、パッケージ化されたアプリの特別な XML 名前空間を含む `AppxManifest.xml` という名前のマニフェストが格納されます。</span><span class="sxs-lookup"><span data-stu-id="57044-165">Each package folder contains a manifest (named `AppxManifest.xml`) that contains a special XML namespace for packaged apps.</span></span> <span data-ttu-id="57044-166">マニフェスト ファイル内の `<EntryPoint>` 要素で、完全信頼アプリを参照します。</span><span class="sxs-lookup"><span data-stu-id="57044-166">Inside that manifest file is an `<EntryPoint>` element, which references the full-trust app.</span></span> <span data-ttu-id="57044-167">そのアプリケーションが起動されると、アプリ コンテナー内で実行されるのではなく、通常どおりユーザーとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="57044-167">When that application is launched, it doesn't run inside an app container, but instead it runs as the user as it normally would.</span></span>

<span data-ttu-id="57044-168">展開後、パッケージ ファイルは読み取り専用としてマークされ、オペレーティング システムによって厳重にロックダウンされます。</span><span class="sxs-lookup"><span data-stu-id="57044-168">After deployment, package files are marked read-only and heavily locked down by the operating system.</span></span> <span data-ttu-id="57044-169">これらのファイルが改ざんされると、Windows によりアプリの起動が回避されます。</span><span class="sxs-lookup"><span data-stu-id="57044-169">Windows prevents apps from launching if these files are tampered with.</span></span>

##### <a name="file-system"></a><span data-ttu-id="57044-170">ファイル システム</span><span class="sxs-lookup"><span data-stu-id="57044-170">File system</span></span>

<span data-ttu-id="57044-171">OS では、フォルダーの場所に応じて、パッケージ化されたデスクトップ アプリケーションに対してさまざまなレベルのファイル システム操作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="57044-171">The OS supports different levels of file system operations for packaged desktop applications, depending on the folder location.</span></span>

<span data-ttu-id="57044-172">ユーザーの *AppData* フォルダーにアクセスしようとすると、システムによって、バックグラウンドでユーザーごと、アプリごとの場所が作成されます。</span><span class="sxs-lookup"><span data-stu-id="57044-172">When trying to access the user's *AppData* folder, the system creates a private per-user, per-app location behind the scenes.</span></span> <span data-ttu-id="57044-173">これにより、パッケージ化されたアプリケーションによって、実際にはプライベート コピーを変更しているときに、実際の *AppData* を編集しているという錯覚が生まれます。</span><span class="sxs-lookup"><span data-stu-id="57044-173">This creates the illusion that the packaged application is editing the real *AppData* when it's actually modifying a private copy.</span></span> <span data-ttu-id="57044-174">このように書き込みのリダイレクトを行うことで、アプリによって行われたすべてのファイル変更をシステムで追跡できます。</span><span class="sxs-lookup"><span data-stu-id="57044-174">By redirecting writes this way, the system can track all file modifications made by the app.</span></span> <span data-ttu-id="57044-175">それにより、アンインストール時にそれらのすべてのファイルをクリーンアップして、システムの "rot (腐敗)" を軽減し、ユーザーのアプリケーション削除エクスペリエンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="57044-175">It can then clean all those files when uninstalling reducing system "rot" and providing a better application removal experience for the user.</span></span>

##### <a name="registry"></a><span data-ttu-id="57044-176">レジストリ</span><span class="sxs-lookup"><span data-stu-id="57044-176">Registry</span></span>

<span data-ttu-id="57044-177">アプリ パッケージには、実際のレジストリ内の `HKLM\Software` と論理的に同等なものとして機能する、registry.dat ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="57044-177">App packages contain a registry.dat file, which serves as the logical equivalent of `HKLM\Software` in the real registry.</span></span> <span data-ttu-id="57044-178">実行時には、この仮想レジストリのハイブの内容がネイティブ システム ハイブにマージされ、両方が一括して表示されます。</span><span class="sxs-lookup"><span data-stu-id="57044-178">At runtime, this virtual registry merges the contents of this hive into the native system hive to provide a singular view of both.</span></span>

<span data-ttu-id="57044-179">パッケージのアップグレード時にすべての書き込みが保持され、アプリケーションのアンインストール時にのみ削除されます。</span><span class="sxs-lookup"><span data-stu-id="57044-179">All writes are kept during package upgrade and only deleted when the application is uninstalled.</span></span>

##### <a name="uninstallation"></a><span data-ttu-id="57044-180">アンインストール</span><span class="sxs-lookup"><span data-stu-id="57044-180">Uninstallation</span></span>

<span data-ttu-id="57044-181">ユーザーがパッケージをアンインストールすると、`C:\Program Files\WindowsApps\package_name` 下にあるすべてのファイルとフォルダーが削除されるほか、プロセス中にキャプチャされた AppData またはレジストリへのリダイレクトされた書き込みもすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="57044-181">When the user uninstalls a package, all files and folders located under `C:\Program Files\WindowsApps\package_name` are removed, as well as any redirected writes to AppData or the registry that were captured during the process.</span></span>

<span data-ttu-id="57044-182">パッケージ化されたアプリケーションで、インストール、ファイル アクセス、レジストリ、およびアンインストールが処理される方法の詳細については、<https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57044-182">For details about how a packaged application handles installation, file access, registry, and uninstallation, see <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes>.</span></span>

<span data-ttu-id="57044-183">チェックすべき項目の完全な一覧は、<https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> で取得できます。</span><span class="sxs-lookup"><span data-stu-id="57044-183">You can get a complete list of things to check on <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare>.</span></span>

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a><span data-ttu-id="57044-184">デスクトップ プロジェクトに WinRT API を追加する方法</span><span class="sxs-lookup"><span data-stu-id="57044-184">How to add WinRT APIs to your desktop project</span></span>

<span data-ttu-id="57044-185">このセクションでは、既存の WPF アプリケーションでトースト通知を統合する方法に関するチュートリアルを紹介します。</span><span class="sxs-lookup"><span data-stu-id="57044-185">In this section, you can find a walkthrough on how to integrate Toast Notifications in an existing WPF application.</span></span> <span data-ttu-id="57044-186">コードの観点からは単純ですが、プロセス全体を明らかにするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="57044-186">Although it's simple from the code perspective, it helps illustrate the whole process.</span></span> <span data-ttu-id="57044-187">通知は、.NET アプリで使用できる多数の利用可能な WinRT API の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="57044-187">Notifications are one of the many available WinRT APIs available that you can use in .NET app.</span></span> <span data-ttu-id="57044-188">この場合、API にはパッケージ ID が必要です。</span><span class="sxs-lookup"><span data-stu-id="57044-188">In this case, the API requires a Package Identity.</span></span> <span data-ttu-id="57044-189">API でパッケージ ID が不要な場合、このプロセスはさらに簡単になります。</span><span class="sxs-lookup"><span data-stu-id="57044-189">This process is more straightforward if the APIs don't require Package Identity.</span></span>

<span data-ttu-id="57044-190">ファイルを読み取り、その内容を画面に表示する既存の WPF サンプル アプリを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="57044-190">Let's take an existing WPF sample app that reads files and shows its contents on the screen.</span></span> <span data-ttu-id="57044-191">目標は、アプリケーションの起動時にトースト通知を表示することです。</span><span class="sxs-lookup"><span data-stu-id="57044-191">The goal is to display a Toast Notification when the application starts.</span></span>

![サンプル アプリケーションが実行しているスクリーンショット](./media/windows-migration/sample-application.png)

<span data-ttu-id="57044-193">最初に、使用する Windows 10 API にパッケージ ID が必要かどうかについて、次のリンクでチェックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57044-193">First, you should check in the following link whether the Windows 10 API that you'll use requires a Package Identity:</span></span>

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

<span data-ttu-id="57044-194">このサンプルでは、パッケージ化された ID を必要とする <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> API を使用します。</span><span class="sxs-lookup"><span data-stu-id="57044-194">Our sample will use the <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> API that requires a packaged identity:</span></span>

![Microsoft ドキュメントの通知クラス](./media/windows-migration/notification-class-documentation.png)

<span data-ttu-id="57044-196">WinRT API にアクセスするには、`Microsoft.Windows.SDK.Contracts` NuGet パッケージへの参照を追加すると、このパッケージによって、バックグラウンドで魔法が使われます (詳細については、<https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="57044-196">To access the WinRT API, add a reference to the `Microsoft.Windows.SDK.Contracts` NuGet package and this package will do the magic behind the scenes (see details at <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/>).</span></span>

<span data-ttu-id="57044-197">これで、何らかのコードの追加を開始する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="57044-197">You're now prepared to start adding some code.</span></span>

<span data-ttu-id="57044-198">アプリケーションの起動時に呼び出される `ShowToastNotification` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="57044-198">Create a `ShowToastNotification` method that will be called on application startup.</span></span> <span data-ttu-id="57044-199">それは、XML パターンからトースト通知を構築するだけです。</span><span class="sxs-lookup"><span data-stu-id="57044-199">It just builds a toast notification from an XML pattern:</span></span>

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

<span data-ttu-id="57044-200">プロジェクトが構築されますが、通知 API にはパッケージ ID が必要ですが、提供していないため、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="57044-200">Although the project builds, there are errors because the Notifications API requires a Package Identity and you didn't provide it.</span></span> <span data-ttu-id="57044-201">Windows パッケージ化プロジェクトをソリューションに追加すると、問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="57044-201">Adding a Windows Packaging Project to the solution will fix the issue:</span></span>

![Visual Studio の [新しいプロジェクトの追加] ダイアログ ボックスのスクリーンショット](./media/windows-migration/add-packaging-project.png)

<span data-ttu-id="57044-203">サポートする Windows の最小バージョンとターゲットとするバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="57044-203">Select the minimum Windows version you want to support and the version you're targeting.</span></span> <span data-ttu-id="57044-204">すべての WinRT API がすべての Windows 10 バージョンでサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="57044-204">Not all the WinRT APIs are supported in all Windows 10 versions.</span></span> <span data-ttu-id="57044-205">Windows 10 の更新プログラムごとに、このバージョンからのみ使用できる新しい API が追加されます。下位レベルのサポートは使用できません。</span><span class="sxs-lookup"><span data-stu-id="57044-205">Each Windows 10 update adds new APIs that are only available from this version; down-level support isn't available.</span></span>

![Windows の最小バージョンの選択](./media/windows-migration/select-versions.png)

<span data-ttu-id="57044-207">次の手順は、プロジェクト参照を追加して WPF アプリケーションを Windows パッケージ化プロジェクトに追加することです。</span><span class="sxs-lookup"><span data-stu-id="57044-207">Next step is to add the WPF application to the Windows Packaging Project by adding a project reference:</span></span>

![Windows パッケージ化プロジェクトへの WPF アプリケーションの追加](./media/windows-migration/add-application.png)

![参照マネージャー](./media/windows-migration/reference-manager.png)

<span data-ttu-id="57044-210">Windows パッケージ化プロジェクトでは、複数のアプリをパッケージ化できるため、どれをエントリ ポイントにするかを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57044-210">A Windows Packaging Project can package several apps so you should set which one is the Entry Point:</span></span>

![エントリ ポイントの設定](./media/windows-migration/set-entry-point.png)

<span data-ttu-id="57044-212">次の手順は、ソリューション構成で WPF プロジェクトをスタートアップ プロジェクトとして設定することです。</span><span class="sxs-lookup"><span data-stu-id="57044-212">Next step is to set the WPF Project as the startup Project in the solution configuration.</span></span> <span data-ttu-id="57044-213">F5 キーを押して、コンパイルしてビルドし、結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="57044-213">You can press F5 to compile and build and see the results.</span></span>

![実行して結果が表示されているサンプル アプリケーション](./media/windows-migration/sample-app-result.png)

<span data-ttu-id="57044-215">アプリをインストールできるようにパッケージを生成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="57044-215">Let's generate the package so you can install your app.</span></span> <span data-ttu-id="57044-216">**[ストア]**  >  **[アプリ パッケージの作成]** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="57044-216">Right click on **Store** > **Create App Packages**.</span></span>

![[アプリ パッケージの作成] ダイアログ](./media/windows-migration/create-app-packages.png)

<span data-ttu-id="57044-218">サイドローディング オプションを選択して、コンピューターからアプリをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="57044-218">Select the sideloading option to deploy the app from your machine:</span></span>

![サイドローディング オプションの選択](./media/windows-migration/select-sideloading-option.png)

<span data-ttu-id="57044-220">アプリのアプリケーション アーキテクチャを選択します。</span><span class="sxs-lookup"><span data-stu-id="57044-220">Select the application architecture of your app:</span></span>

![アプリケーション アーキテクチャの選択](./media/windows-migration/select-app-architecture.png)

<span data-ttu-id="57044-222">最後に、 **[作成]** をクリックしてパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="57044-222">Finally, create the package by clicking on **Create**.</span></span>

## <a name="xaml-islands"></a><span data-ttu-id="57044-223">XAML Islands</span><span class="sxs-lookup"><span data-stu-id="57044-223">XAML Islands</span></span>

<span data-ttu-id="57044-224">XAML Islands は、Windows デスクトップ開発者が既存の Win32 アプリケーション (Windows Forms や WPF など) で UWP XAML コントロールを使用できるようにする一連のコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="57044-224">XAML Islands are a set of components that enable Windows desktop developers to use UWP XAML controls on their existing Win32 applications, including Windows Forms and WPF.</span></span>

![XAML Islands の構造](./media/windows-migration/xaml-islands.png)

<span data-ttu-id="57044-226">標準のコントロールと、それらの中でも最新のコントロールを含む UWP UI の "アイランド" を使用した Win32 アプリを想像できます。</span><span class="sxs-lookup"><span data-stu-id="57044-226">You can image your Win32 app with your standard controls and among them an "island" of UWP UI containing controls from the modern world.</span></span> <span data-ttu-id="57044-227">この概念は、Web ページ内に `different page.` のコンテンツを表示する iFrame があることと似ています</span><span class="sxs-lookup"><span data-stu-id="57044-227">The concept is similar as having an iFrame inside a web page that shows content from a `different page.`</span></span>

<span data-ttu-id="57044-228">Windows 10 API からの機能を追加するだけでなく、XAML Islands を使用して、アプリ内に UWP XAML を追加できます。</span><span class="sxs-lookup"><span data-stu-id="57044-228">Besides adding functionality from the Windows 10 APIs, you can add pieces of UWP XAML inside of your app using XAML Islands.</span></span>

<span data-ttu-id="57044-229">Windows 10 1903 更新プログラムでは、Win32 ウィンドウで UWP XAML コンテンツをホストできるようにする一連の API が導入されています。</span><span class="sxs-lookup"><span data-stu-id="57044-229">Windows 10 1903 update introduces a set of APIs that allows hosting UWP XAML content in Win32 windows.</span></span> <span data-ttu-id="57044-230">XAML Islands を使用できるのは、Windows 10 1903 で実行されているアプリのみです。</span><span class="sxs-lookup"><span data-stu-id="57044-230">Only apps running on Windows 10 1903 can use XAML Islands.</span></span>

### <a name="the-road-to-xaml-islands"></a><span data-ttu-id="57044-231">XAML Islands への道</span><span class="sxs-lookup"><span data-stu-id="57044-231">The road to XAML Islands</span></span>

<span data-ttu-id="57044-232">XAML Islands への道は 2012 年から始まり、そのときに Microsoft では Win32 アプリを現代化するためのフレームワーク (Windows Forms、WPF、およびネイティブ Win32 アプリ) として WinRT API を導入しました。</span><span class="sxs-lookup"><span data-stu-id="57044-232">The road to XAML Islands started in 2012 when Microsoft introduced the WinRT APIs as a framework to modernize the Win32 apps (Windows Forms, WPF, and native Win32 apps).</span></span> <span data-ttu-id="57044-233">ただし、WinRT 内の新しい UI コントロールは、新しいアプリケーションでは使用できましたが、既存のアプリケーションでは使用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="57044-233">However, the new UI controls inside WinRT were available for new applications but not for existing ones.</span></span>

<span data-ttu-id="57044-234">2015 年に、Windows 10 と共に UWP が誕生しました。</span><span class="sxs-lookup"><span data-stu-id="57044-234">In 2015, along with Windows 10, UWP was born.</span></span> <span data-ttu-id="57044-235">UWP により、XBox、Mobile、Desktop などの Windows デバイス全体で動作するアプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="57044-235">UWP allows you to create apps that work across Windows devices like XBox, Mobile, and Desktop.</span></span> <span data-ttu-id="57044-236">1 年後、Microsoft はデスクトップ ブリッジ (旧称 Project Centennial) を発表しました。</span><span class="sxs-lookup"><span data-stu-id="57044-236">One year later, Microsoft announced Desktop Bridge (formerly known as Project Centennial).</span></span> <span data-ttu-id="57044-237">デスクトップ ブリッジは、開発者が既存の Win32 アプリを Microsoft Store に持ち込めるようにする一連のツールです。</span><span class="sxs-lookup"><span data-stu-id="57044-237">Desktop Bridge is a set of tools that allowed developers to bring their existing Win32 apps to the Microsoft Store.</span></span> <span data-ttu-id="57044-238">2017 年にさらに機能が追加され、開発者は、アクション センターのライブ タイルや通知など、新しい Windows 10 API を利用して、Win32 アプリを拡張できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="57044-238">More capabilities were added in 2017, allowing developers to enhance their Win32 apps leveraging some of the new Windows 10 APIs, like live tiles and notifications on the action center.</span></span> <span data-ttu-id="57044-239">しかしまだ、新しい UI コントロールはありませんでした。</span><span class="sxs-lookup"><span data-stu-id="57044-239">But still, no new UI controls.</span></span>

<span data-ttu-id="57044-240">ビルド 2018 で、Microsoft は、開発者がアプリを UWP に完全に移行することなく、新しい Windows 10 XAML コントロールを現在の Win32 アプリに組み込む方法を発表しました。</span><span class="sxs-lookup"><span data-stu-id="57044-240">At Build 2018, Microsoft announced a way for developers to use the new Windows 10 XAML controls into their current Win32 apps, without fully migrating their apps to UWP.</span></span> <span data-ttu-id="57044-241">それは、UWP XAML Islands としてブランド化されました。</span><span class="sxs-lookup"><span data-stu-id="57044-241">It was branded as UWP XAML Islands.</span></span>

### <a name="how-it-works"></a><span data-ttu-id="57044-242">しくみ</span><span class="sxs-lookup"><span data-stu-id="57044-242">How it works</span></span>

<span data-ttu-id="57044-243">Windows 10 1903 更新プログラムでは、いくつかの XAML ホスティング API が導入されています。</span><span class="sxs-lookup"><span data-stu-id="57044-243">The Windows 10 1903 update introduces several XAML hosting APIs.</span></span> <span data-ttu-id="57044-244">そのうちの 2 つは `WindowsXamlManager` と `DesktopWindowXamlSource` です。</span><span class="sxs-lookup"><span data-stu-id="57044-244">Two of them are `WindowsXamlManager` and `DesktopWindowXamlSource`.</span></span>

<span data-ttu-id="57044-245">`WindowsXamlManager` クラスで、UWP XAML フレームワークを処理します。</span><span class="sxs-lookup"><span data-stu-id="57044-245">The `WindowsXamlManager` class handles the UWP XAML Framework.</span></span> <span data-ttu-id="57044-246">その `InitializeForCurrentThread` メソッドで、Win32 アプリの現在のスレッド内に UWP XAML フレームワークを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="57044-246">Its `InitializeForCurrentThread` method loads the UWP XAML Framework inside the current thread of the Win32 app.</span></span>

<span data-ttu-id="57044-247">`DesktopWindowXamlSource` は、XAML Island コンテンツのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="57044-247">The `DesktopWindowXamlSource` is the instance of your XAML Island content.</span></span> <span data-ttu-id="57044-248">それには、`Content` プロパティがあり、ユーザーがインスタンス化して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57044-248">It has the `Content` property, which you're responsible for instantiating and setting.</span></span> <span data-ttu-id="57044-249">`DesktopWindowXamlSource` では、HWND からその入力をレンダリングして取得します。</span><span class="sxs-lookup"><span data-stu-id="57044-249">The `DesktopWindowXamlSource` renders and gets its input from an HWND.</span></span> <span data-ttu-id="57044-250">それは、XAML Island の HWND のアタッチ先となる他の HWND を認識している必要があります。また、ユーザーが親の HWND のサイズと配置を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57044-250">It needs to know to which other HWND it will attach the XAML Island's one, and you're responsible for sizing and positioning the parent's HWND.</span></span>

<span data-ttu-id="57044-251">WPF や Windows Forms の開発者は、通常コード内で HWND を処理しないので、HWND ポインターや、Win32 や UWP の世界と通信するための基になる接続に関する事項を理解し、処理するのは困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="57044-251">WPF or Windows Forms developers don't usually deal with HWND inside their code, so it may be hard to understand and handle HWND pointers and the underlying wiring stuff to communicate Win32 and UWP worlds.</span></span>

#### <a name="the-xaml-islands-net-wrappers"></a><span data-ttu-id="57044-252">XAML Islands .NET ラッパー</span><span class="sxs-lookup"><span data-stu-id="57044-252">The XAML Islands .NET Wrappers</span></span>

<span data-ttu-id="57044-253">Windows Community Toolkit には、XAML Islands を使いやすくする WPF または Windows Forms 用の XAML Islands .NET ラッパー セットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="57044-253">The Windows Community Toolkit has a set the XAML Islands .NET wrappers for WPF or Windows Forms that make easier to use XAML Islands.</span></span> <span data-ttu-id="57044-254">これらのラッパーによって、HWND、フォーカス管理などを管理します。</span><span class="sxs-lookup"><span data-stu-id="57044-254">These wrappers manage the HWNDs, the focus management, among other things.</span></span> <span data-ttu-id="57044-255">Windows Forms および WPF 開発者は、これらのラッパーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57044-255">Windows Forms and WPF developers should use these wrappers.</span></span>

<span data-ttu-id="57044-256">Windows Community Toolkit には、ラップされたコントロールとホスティング コントロールの 2 種類のコントロールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="57044-256">The Windows Community Toolkit offers two types of controls: Wrapped Controls and Hosting Controls.</span></span>

##### <a name="wrapped-controls"></a><span data-ttu-id="57044-257">ラップされたコントロール</span><span class="sxs-lookup"><span data-stu-id="57044-257">Wrapped Controls</span></span>

<span data-ttu-id="57044-258">これらのラップされたコントロールによって、いくつかの UWP コントロールが Windows Forms または WPF コントロールにラップされ、それらの開発者に UWP の概念が隠されます。</span><span class="sxs-lookup"><span data-stu-id="57044-258">These wrapped controls wrap some UWP controls into Windows Forms or WPF controls, hiding UWP concepts for those developers.</span></span> <span data-ttu-id="57044-259">これらのコントロールは:</span><span class="sxs-lookup"><span data-stu-id="57044-259">These controls are:</span></span>

* <span data-ttu-id="57044-260">WebView と WebViewCompatible</span><span class="sxs-lookup"><span data-stu-id="57044-260">WebView and WebViewCompatible</span></span>
* <span data-ttu-id="57044-261">InkCanvas と InkToolbar</span><span class="sxs-lookup"><span data-stu-id="57044-261">InkCanvas and InkToolbar</span></span>
* <span data-ttu-id="57044-262">MediaPlayerElement</span><span class="sxs-lookup"><span data-stu-id="57044-262">MediaPlayerElement</span></span>
* <span data-ttu-id="57044-263">MapControl</span><span class="sxs-lookup"><span data-stu-id="57044-263">MapControl</span></span>

<span data-ttu-id="57044-264">`Microsoft.Toolkit.Wpf.UI.Controls` パッケージをプロジェクトに追加し、名前空間に参照を含めて、それらの使用を開始します。</span><span class="sxs-lookup"><span data-stu-id="57044-264">Add the `Microsoft.Toolkit.Wpf.UI.Controls` package to your project, include the reference to the namespace, and start using them.</span></span>

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

##### <a name="hosting-controls"></a><span data-ttu-id="57044-265">ホスティング コントロール</span><span class="sxs-lookup"><span data-stu-id="57044-265">Hosting controls</span></span>

<span data-ttu-id="57044-266">XAML Islands の機能は、ほとんどのファーストパーティ コントロール、サードパーティ コントロール、および UWP 用に開発されたカスタム コントロールに拡張され、完全に機能する UI を含む "アイランド" として Windows Forms および WPF に統合できます。</span><span class="sxs-lookup"><span data-stu-id="57044-266">The power of XAML Islands extends to most first-party controls, third-party controls, and custom controls developed for UWP, which can be integrated into Windows Forms and WPF as "Islands" with fully functional UI.</span></span> <span data-ttu-id="57044-267">WPF と Windows Forms の `WindowsXamlHost` コントロールにより、これを実行できます。</span><span class="sxs-lookup"><span data-stu-id="57044-267">The `WindowsXamlHost` control for WPF and Windows Forms allows doing this.</span></span>

<span data-ttu-id="57044-268">たとえば、WPF で `WindowsXamlHost` コントロールを使用するには、Windows Community Toolkit によって提供される `Microsoft.Toolkit.Wpf.UI.XamlHost` パッケージへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="57044-268">For example, to use the `WindowsXamlHost` control in WPF, add a reference to the `Microsoft.Toolkit.Wpf.UI.XamlHost` package provided by the Windows Community Toolkit.</span></span>

<span data-ttu-id="57044-269">`WindowsXamlHost` を UI コードに配置したら、読み込む UWP の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="57044-269">Once you've placed your `WindowsXamlHost` into your UI code, specify which UWP type you want to load.</span></span> <span data-ttu-id="57044-270">`Button` のようなラップされたコントロールまたは、カスタム UWP コントロールである複数の異なるコントロールによって構成されるより複雑なコントロールを使用することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="57044-270">You can choose to use a wrapped control like a `Button` or a more complex one composed by several different controls, which are a custom UWP control.</span></span>

<span data-ttu-id="57044-271">次の例に、UWP `Button` ボタンを追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="57044-271">The following example shows how to add a UWP `Button`:</span></span>

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

<span data-ttu-id="57044-272">このアプローチ方法については明確な推奨事項があり、それぞれ 1 つのコントロールを含む複数のアイランドを使用するよりも、カスタム複合コントロールを含む 1 つの大きな XAML アイランドを使用する方が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="57044-272">There's a clear recommendation on how to approach this and it's better to have one single and bigger XAML Island containing a custom composite control than to have several islands with one control on each.</span></span>

<span data-ttu-id="57044-273">XAML のコア機能の 1 つがバインディングであり、Win32 コードとアイランドの間で機能します。</span><span class="sxs-lookup"><span data-stu-id="57044-273">One of the core features of XAML is binding and it works between your Win32 code and the island.</span></span> <span data-ttu-id="57044-274">そのため、たとえば、Win32 `Textbox` と UWP `Textbox` をバインドできます。</span><span class="sxs-lookup"><span data-stu-id="57044-274">So, you can bind, for instance, a Win32 `Textbox` with a UWP `Textbox`.</span></span> <span data-ttu-id="57044-275">考慮すべき重要な点の 1 つとして、これらのバインディングは UWP から Win32 への一方向のバインディングであるため、XAML Island 内で `Textbox` を更新すると、Win32 テキストボックスが更新されますが、その逆は更新されません。</span><span class="sxs-lookup"><span data-stu-id="57044-275">One important thing to consider is that these bindings are one-way bindings, from UWP to Win32, so if you update the `Textbox` inside the XAML Island the Win32 Textbox will be updated, but not the other way around.</span></span>

<span data-ttu-id="57044-276">XAML Islands の使用方法に関するチュートリアルについては、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57044-276">To see a walkthrough about how to use XAML Islands, see:</span></span>

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a><span data-ttu-id="57044-277">UWP XAML カスタム コントロールの追加</span><span class="sxs-lookup"><span data-stu-id="57044-277">Adding UWP XAML custom controls</span></span>

<span data-ttu-id="57044-278">XAML カスタム コントロールは、ユーザーまたはサードパーティ (WinUI 2.x コントロールを含む) によって作成されたコントロール (またはユーザー コントロール) です。</span><span class="sxs-lookup"><span data-stu-id="57044-278">A XAML custom control is a control (or user control) created by you or by third parties (including WinUI 2.x controls).</span></span> <span data-ttu-id="57044-279">Windows Forms または WPF アプリでカスタム UWP コントロールをホストするには、次が必要です。</span><span class="sxs-lookup"><span data-stu-id="57044-279">To host a custom UWP control in a Windows Forms or WPF app, you'll need:</span></span>

- <span data-ttu-id="57044-280">.NET アプリで `WindowsXamlHost` UWP コントロールを使用する。</span><span class="sxs-lookup"><span data-stu-id="57044-280">To use the `WindowsXamlHost` UWP control in your .NET app.</span></span>
- <span data-ttu-id="57044-281">`XamlApplication` オブジェクトを定義する UWP アプリ プロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="57044-281">To create a UWP app project that defines a `XamlApplication` object.</span></span>

<span data-ttu-id="57044-282">WPF または Windows Forms プロジェクトでは、Windows Community Toolkit によって提供される `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` クラスのインスタンスにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="57044-282">Your WPF or Windows Forms project must have access to an instance of the `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` class provided by the Windows Community Toolkit.</span></span> <span data-ttu-id="57044-283">このオブジェクトは、アプリケーションの現在のディレクトリにあるアセンブリにカスタム UWP XAML 型のメタデータを読み込むためのルート メタデータ プロバイダーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="57044-283">This object acts as a root metadata provider for loading metadata for custom UWP XAML types in assemblies in the current directory of your application.</span></span> <span data-ttu-id="57044-284">これを行うために推奨される方法は、WPF または Windows Forms プロジェクトと同じソリューションに空のアプリ (ユニバーサル Windows) プロジェクトを追加し、このプロジェクトの既定のアプリ クラスを変更することです。</span><span class="sxs-lookup"><span data-stu-id="57044-284">The recommended way to do this is to add a Blank App (Universal Windows) project to the same solution as your WPF or Windows Forms project and revise the default App class in this project.</span></span>

<span data-ttu-id="57044-285">カスタム UWP XAML コントロールは、この UWP アプリか、または WPF や Windows Forms プロジェクトと同じソリューションで参照する独立した UWP クラス ライブラリ プロジェクトに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="57044-285">The custom UWP XAML control can be included on this UWP app or in an independent UWP Class Library project that you reference in the same solution as your WPF or Windows Forms project.</span></span>

<span data-ttu-id="57044-286">次で詳細な手順を追ったプロセスの説明を確認できます。</span><span class="sxs-lookup"><span data-stu-id="57044-286">You can check a detailed step-by-step process description at:</span></span>

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a><span data-ttu-id="57044-287">Windows UI ライブラリ (WinUI 2)</span><span class="sxs-lookup"><span data-stu-id="57044-287">The Windows UI Library (WinUI 2)</span></span>

<span data-ttu-id="57044-288">OS に付属する受信トレイ Windows 10 コントロール以外にも、同じ UWP XAML チームが Windows UI ライブラリ (**WinUI 2**) に追加のコントロールを提供しています。</span><span class="sxs-lookup"><span data-stu-id="57044-288">Besides the inbox Windows 10 controls that comes with the OS, the same UWP XAML team also deliver additional controls in the Windows UI Library (**WinUI 2**).</span></span> <span data-ttu-id="57044-289">WinUI 2 には、Windows UWP アプリ用のネイティブ Microsoft UI コントロールおよび機能が用意されており、これらのコントロールは、XAML Islands 内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="57044-289">WinUI 2 provides official native Microsoft UI controls and features for Windows UWP apps and these controls can be used inside of XAML Islands.</span></span>

<span data-ttu-id="57044-290">WinUI 2 はオープン ソースであり、<https://github.com/microsoft/microsoft-ui-xaml> で、情報を見つけることができ ます。</span><span class="sxs-lookup"><span data-stu-id="57044-290">WinUI 2 is open source and you can find information at <https://github.com/microsoft/microsoft-ui-xaml>.</span></span>

<span data-ttu-id="57044-291">次の記事で、WinUI 2 ライブラリの UWP コントロールをホストする方法について説明しています。<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands></span><span class="sxs-lookup"><span data-stu-id="57044-291">The following article demonstrates how to host a UWP XAML control from the WinUI 2 library: <https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands></span></span>

### <a name="do-you-need-xaml-islands"></a><span data-ttu-id="57044-292">XAML Islands が必要か</span><span class="sxs-lookup"><span data-stu-id="57044-292">Do you need XAML Islands</span></span>

<span data-ttu-id="57044-293">XAML Islands は、アプリを完全に書き換えずに新しい UWP コントロールと動作を利用することで、ユーザー エクスペリエンスを向上させる必要がある既存の Win32 アプリを対象としています。</span><span class="sxs-lookup"><span data-stu-id="57044-293">XAML Islands are intended for existing Win32 apps that want to improve their user experience by leveraging new UWP controls and behaviors without a full rewrite of the app.</span></span> <span data-ttu-id="57044-294">既に [Windows 10 API を利用](/windows/uwp/porting/desktop-to-uwp-enhance)できますが、XAML Islands までは UI に関連しない API のみを利用できます。</span><span class="sxs-lookup"><span data-stu-id="57044-294">You could already [leverage Windows 10 APIs](/windows/uwp/porting/desktop-to-uwp-enhance), but up until XAML Islands, only non-UI related APIs.</span></span>

<span data-ttu-id="57044-295">新しい Windows アプリを開発している場合、[UWP アプリ](/windows/uwp/get-started/universal-application-platform-guide)が適切なアプローチであると考えられます。</span><span class="sxs-lookup"><span data-stu-id="57044-295">If you're developing a new Windows App, a [UWP App](/windows/uwp/get-started/universal-application-platform-guide) is probably the right approach.</span></span>

### <a name="the-road-ahead-xaml-islands-winui-30"></a><span data-ttu-id="57044-296">XAML Islands への道: WinUI 3.0</span><span class="sxs-lookup"><span data-stu-id="57044-296">The road ahead XAML Islands: WinUI 3.0</span></span>

<span data-ttu-id="57044-297">Windows 8 以降、Windows UI プラットフォーム (XAML UI フレームワーク、ビジュアル コンポジション レイヤー、入力処理など) が Windows の不可欠な部分として出荷されています。</span><span class="sxs-lookup"><span data-stu-id="57044-297">Since Windows 8, the Windows UI platform, including the XAML UI framework, visual composition layer, and input processing has been shipped as an integral part of Windows.</span></span> <span data-ttu-id="57044-298">これは、UI テクノロジの最新の機能強化から利点を得るためには、最新バージョンの UI にアップグレードする必要があり、アプリの開発時にイノベーションのペースが低下することを意味します。</span><span class="sxs-lookup"><span data-stu-id="57044-298">This means that to benefit from the latest improvements on UI technologies, you must upgrade to the latest version of the UI, slowing down the pace of innovation when you develop your apps.</span></span> <span data-ttu-id="57044-299">これらの 2 つの発展サイクルを分離し、イノベーションを促進するために、Microsoft は、WinUI プロジェクトに積極的に取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="57044-299">To decouple these two evolution cycles and foster innovation, Microsoft is actively working on the WinUI project.</span></span>

<span data-ttu-id="57044-300">2018 年の WinUI 2 以降、Microsoft は、UWP SDK に基づいて構築された個別の NuGet パッケージとして、いくつかの新しい XAML UI コントロールと機能の出荷を開始しました。</span><span class="sxs-lookup"><span data-stu-id="57044-300">Starting with WinUI 2 in 2018, Microsoft started shipping some new XAML UI controls and features as separate NuGet packages that build on top of the UWP SDK.</span></span>

![WinUI 2.0 の構造](./media/windows-migration/winui2.png)

<span data-ttu-id="57044-302">WinUI 3 は、活発な開発段階にあり、完全な UI プラットフォームを含めるように、WinUI の範囲を大幅に拡大しており、UWP SDK から完全に分離されます。</span><span class="sxs-lookup"><span data-stu-id="57044-302">WinUI 3 is under active development and will greatly expand the scope of WinUI to include the full UI platform, which will be fully decoupled from the UWP SDK:</span></span>

![WinUI 3.0 の構造](./media/windows-migration/winui3.png)

<span data-ttu-id="57044-304">XAML フレームワークは、GitHub で開発され、[NuGet](/nuget/what-is-nuget) パッケージとしてアウトオブバンドで出荷されるようになります。</span><span class="sxs-lookup"><span data-stu-id="57044-304">XAML framework will now be developed on GitHub and shipped out of band as [NuGet](/nuget/what-is-nuget) packages.</span></span>

<span data-ttu-id="57044-305">OS の一部として同梱されている既存の UWP XAML API に対して、新しい機能更新プログラムが提供されることはなくなります。</span><span class="sxs-lookup"><span data-stu-id="57044-305">The existing UWP XAML APIs that ship as part of the OS will no longer receive new feature updates.</span></span> <span data-ttu-id="57044-306">それらには、Windows 10 のサポート ライフサイクルに従って、セキュリティ更新プログラムと重要な修正プログラムが引き続き提供されます。</span><span class="sxs-lookup"><span data-stu-id="57044-306">They will still receive security updates and critical fixes according to the Windows 10 support lifecycle.</span></span>

<span data-ttu-id="57044-307">ユニバーサル Windows プラットフォームに含まれるものは、XAML フレームワークだけでなく (アプリケーションおよびセキュリティ モデル、メディア パイプライン、Xbox と Windows 10 のシェル統合、広範なデバイス サポートなど)、進化し続けています。</span><span class="sxs-lookup"><span data-stu-id="57044-307">The Universal Windows Platform contains more than just the XAML framework (for example, application and security model, media pipeline, Xbox and Windows 10 shell integrations, broad device support) and will continue to evolve.</span></span> <span data-ttu-id="57044-308">すべての新しい XAML 機能は、代わりに WinUI の一部として開発され、出荷されます。</span><span class="sxs-lookup"><span data-stu-id="57044-308">All new XAML features will just be developed and ship as part of WinUI instead.</span></span>

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a><span data-ttu-id="57044-309">デスクトップ アプリの WinUI 3 と WinUI XAML Islands</span><span class="sxs-lookup"><span data-stu-id="57044-309">WinUI 3 in desktop app and WinUI XAML Islands</span></span>

<span data-ttu-id="57044-310">ご覧のように、WinUI 3 は UWP XAML の進化形であり、UWP アプリ モデルとそのすべての要件 (MSIX パッケージ ID、サンドボックス、CoreWindow など) 内で自然に機能します。</span><span class="sxs-lookup"><span data-stu-id="57044-310">As you can see, WinUI 3 is the evolution of UWP XAML and it works naturally within the UWP app model and all its requirements (MSIX packaged ID, sandbox, CoreWindow, and so on.</span></span> <span data-ttu-id="57044-311">Win32 アプリ モデルで WinUI 3 だけを使用するには、WinUI コンテンツを、**WinUI XAML Islands** を使用する別の UI フレームワーク (Windows Forms、WPF など) でホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57044-311">To use just WinUI 3 in a Win32 app model, the WinUI content should be hosted by another UI Framework (Windows Forms, WPF, and so on) using **WinUI XAML Islands**.</span></span> <span data-ttu-id="57044-312">これは、アプリを進化させ、テクノロジを混在させる場合の適切なパスです。</span><span class="sxs-lookup"><span data-stu-id="57044-312">This is the right path if you want to evolve your app and mix technologies.</span></span> <span data-ttu-id="57044-313">ただし、古い UI 全体を WinUI に置き換える場合は、アプリで、WinUI をホストするためだけに UI フレームワークを読み込まないでください。</span><span class="sxs-lookup"><span data-stu-id="57044-313">However, if you want to replace your entire old UI for WinUI, your app shouldn't load UI Frameworks for just hosting WinUI.</span></span>

<span data-ttu-id="57044-314">WinUI 3 によって、**デスクトップアプリへの WinUI** の追加に関するこの重要なフィードバックに対処します。</span><span class="sxs-lookup"><span data-stu-id="57044-314">WinUI 3 will address this critical feedback adding **WinUI in desktop apps**.</span></span> <span data-ttu-id="57044-315">これにより、Win32 アプリで、スタンドアロン UI フレームワークとして、WinUI 3 を使用できるようになります。Windows Forms や WPF を読み込む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="57044-315">This will allow that Win32 apps can use WinUI 3 as standalone UI Framework; no need to load Windows Forms or WPF.</span></span>

<span data-ttu-id="57044-316">この集合体の中で、WinUI 3 によって、開発者は次の正しい組み合わせを簡単に組み合わせることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="57044-316">Within this aggregation, WinUI 3 will let developers easily mix and match the right combination of:</span></span>

* <span data-ttu-id="57044-317">アプリ モデル: UWP、Win32</span><span class="sxs-lookup"><span data-stu-id="57044-317">App model: UWP, Win32</span></span>
* <span data-ttu-id="57044-318">プラットフォーム: .NET またはネイティブ</span><span class="sxs-lookup"><span data-stu-id="57044-318">Platform: .NET or Native</span></span>
* <span data-ttu-id="57044-319">言語: .NET (C \#、Visual Basic)、標準 C++</span><span class="sxs-lookup"><span data-stu-id="57044-319">Language: .NET (C\#, Visual Basic), standard C++</span></span>
* <span data-ttu-id="57044-320">パッケージ化: MSIX、Microsoft Store 用 AppX、パッケージ化されない</span><span class="sxs-lookup"><span data-stu-id="57044-320">Packaging: MSIX, AppX for the Microsoft Store, unpackaged</span></span>
* <span data-ttu-id="57044-321">相互運用: WinUI 3 を使用し、WinUI XAML Islands を使用する既存の WPF、WinForms、および MFC アプリを拡張する。</span><span class="sxs-lookup"><span data-stu-id="57044-321">Interop: use WinUI 3 to extend existing WPF, WinForms, and MFC apps using WinUI XAML Islands.</span></span>

<span data-ttu-id="57044-322">詳細については、Microsoft が <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> でこのロードマップを公表しています。</span><span class="sxs-lookup"><span data-stu-id="57044-322">If you want to know more details, Microsoft is sharing this roadmap in <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="57044-323">[前へ](migrate-modern-applications.md)
>[次へ](example-migration.md)</span><span class="sxs-lookup"><span data-stu-id="57044-323">[Previous](migrate-modern-applications.md)
[Next](example-migration.md)</span></span>
