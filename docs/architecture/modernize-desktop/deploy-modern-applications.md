---
title: 最新デスクトップ アプリケーションのデプロイ
description: 最新のデスクトップアプリケーションの展開について理解しておく必要があるすべての情報。
ms.date: 05/12/2020
ms.openlocfilehash: ba47f09b27adf270734bbfff285fe44dd4175d29
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615855"
---
# <a name="deploying-modern-desktop-applications"></a><span data-ttu-id="691a8-103">最新デスクトップ アプリケーションのデプロイ</span><span class="sxs-lookup"><span data-stu-id="691a8-103">Deploying Modern Desktop Applications</span></span>

<span data-ttu-id="691a8-104">デスクトップアプリケーションを開発する際に考慮すべき1つの点は、アプリケーションをパッケージ化してユーザーのコンピューターに配置する方法です。</span><span class="sxs-lookup"><span data-stu-id="691a8-104">When you develop desktop applications, one thing to consider is how your application is going to be packaged and deployed to the users' machines.</span></span> <span data-ttu-id="691a8-105">パッケージ化、デプロイ、およびインストールに関する問題は、通常、開発者とは異なることに注意して、IT プロフェッショナルの包括的なものになります。</span><span class="sxs-lookup"><span data-stu-id="691a8-105">The problem with packaging, deployment, and installation is that it usually falls under the umbrella of the IT professionals, who care about different things than developers.</span></span>

<span data-ttu-id="691a8-106">ここでは、開発者や IT 担当者がアプリケーションを運用環境に移行する際に緊密に連携する、DevOps の概念を熟知しています。</span><span class="sxs-lookup"><span data-stu-id="691a8-106">These days, we're all familiar with the DevOps concept, where developers and IT Pros work closely to move applications to their production environments.</span></span> <span data-ttu-id="691a8-107">しかし、10年以上にわたってデスクトップの戦いを行っている場合は、次のような話をしているかもしれません。</span><span class="sxs-lookup"><span data-stu-id="691a8-107">But if you've been in the desktop battle for more than 10 years, you might have seen the following story.</span></span> <span data-ttu-id="691a8-108">開発者チームは、プロジェクトの期限に合わせて作業を行うことが困難です。</span><span class="sxs-lookup"><span data-stu-id="691a8-108">A team of developers works together hard to meet the project deadlines.</span></span> <span data-ttu-id="691a8-109">企業では、多くのユーザーのコンピューターで作業する必要があるため、ビジネス担当者は不安ています。</span><span class="sxs-lookup"><span data-stu-id="691a8-109">Business people are nervous since they need the system working on many user's machines to run the company.</span></span> <span data-ttu-id="691a8-110">"D 日" では、プロジェクトマネージャーは、コードが正常に動作していることと、すべての問題があることをすべての開発者に確認します。</span><span class="sxs-lookup"><span data-stu-id="691a8-110">On "D-Day", the project manager checks with every developer that their code is working well and that everything is fine, so they can ship.</span></span> <span data-ttu-id="691a8-111">次に、パッケージチームは、アプリのセットアップを生成し、すべてのユーザーコンピューターに配布し、一連のテストユーザーがアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="691a8-111">Then, the package team comes in generating the setup for the app, distribute it to every user machine and a set of test users run the application.</span></span> <span data-ttu-id="691a8-112">UI を表示する前に、アプリケーションが "メソッド ~ オブジェクト ~ 失敗" という例外をスローしています。</span><span class="sxs-lookup"><span data-stu-id="691a8-112">Well, they try, because before showing any UI, the application throws an exception that says "Method ~ of object ~ failed".</span></span> <span data-ttu-id="691a8-113">パニックからの旅が開始され、簡単な調査では、サードパーティ製のコントロールを導入した若いおよび疲れている開発者を指しています。これは、"開発用コンピューターでの作業" です。</span><span class="sxs-lookup"><span data-stu-id="691a8-113">Panic starts flowing through the air and a brief investigation points to a young and tired developer that has introduced a third-party control, that certainly "worked on the dev machine".</span></span>

<span data-ttu-id="691a8-114">従来、デスクトップアプリケーションのインストールは、主に次の2つの理由で悪夢でした。</span><span class="sxs-lookup"><span data-stu-id="691a8-114">Installing desktop applications have traditionally been a nightmare for two main reasons:</span></span>

- <span data-ttu-id="691a8-115">開発チームと IT チームの間に密接なコラボレーションの文化がない。</span><span class="sxs-lookup"><span data-stu-id="691a8-115">Lack of close collaboration culture between dev and IT teams.</span></span>
- <span data-ttu-id="691a8-116">安定したパッケージ化と展開を可能にするテクノロジの欠如。</span><span class="sxs-lookup"><span data-stu-id="691a8-116">Lack of a solid packaging and deploying technology we can build upon.</span></span>

<span data-ttu-id="691a8-117">実際、次の理由により、アプリをインストールしたことがあります。</span><span class="sxs-lookup"><span data-stu-id="691a8-117">In fact, we've been living with the fact that sometimes you regret that you installed an app because:</span></span>

- <span data-ttu-id="691a8-118">最終的に、コンピューターに望ましくない副作用が発生します。</span><span class="sxs-lookup"><span data-stu-id="691a8-118">It ends up having some undesired side effects on your machine.</span></span>
- <span data-ttu-id="691a8-119">以前にインストールされた一部のアプリケーションは動作しなくなります。</span><span class="sxs-lookup"><span data-stu-id="691a8-119">Some applications that were previously installed stop working.</span></span>

<span data-ttu-id="691a8-120">また、アプリをアンインストールすることで、システムを元の状態に復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="691a8-120">Additionally, you can't just restore the system to its original state by uninstalling the app.</span></span> <span data-ttu-id="691a8-121">私たちは、"DLL の造語" や "Winrot" のような用語を使用して、このような状況に対処しました。</span><span class="sxs-lookup"><span data-stu-id="691a8-121">We're so used to live this situation that we've coined terms like "DLL Hell" or "Winrot".</span></span>

<span data-ttu-id="691a8-122">この章では、MSIX について説明します。</span><span class="sxs-lookup"><span data-stu-id="691a8-122">In this chapter, we'll talk about MSIX.</span></span> <span data-ttu-id="691a8-123">MSIX は、Microsoft が提供する最新のテクノロジであり、以前のテクノロジを最大限に活用して、将来のパッケージ化テクノロジの堅牢な基盤を提供しようとしています。</span><span class="sxs-lookup"><span data-stu-id="691a8-123">MSIX is the brand-new technology from Microsoft that tries to capture the best of previous technologies to provide a solid foundation for the packaging technology of the future.</span></span>

<span data-ttu-id="691a8-124">パッケージ化テクノロジは、最新化に関してどのようなことを行う必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="691a8-124">What does a packaging technology have to do with modernization?</span></span> <span data-ttu-id="691a8-125">このパッケージは、企業の IT 部門にとって多くの資金が投資されています。</span><span class="sxs-lookup"><span data-stu-id="691a8-125">Well, it turns out that packaging is fundamental for the enterprise IT with lots of money invested there.</span></span> <span data-ttu-id="691a8-126">最新のテクノロジを使用する場合にのみ、最新化が関連しています。</span><span class="sxs-lookup"><span data-stu-id="691a8-126">Modernization isn't only related to using the latest technologies.</span></span> <span data-ttu-id="691a8-127">また、企業がクライアントに機能を提供するまで、ビジネス要件が定義されている時点から市場投入までの時間を短縮することにも関連しています。</span><span class="sxs-lookup"><span data-stu-id="691a8-127">It's also related to reducing time to market from the moment a business requirement is defined until your company delivers the feature to your client.</span></span>

## <a name="the-modern-application-lifecycle"></a><span data-ttu-id="691a8-128">最新のアプリケーションライフサイクル</span><span class="sxs-lookup"><span data-stu-id="691a8-128">The modern application lifecycle</span></span>

<span data-ttu-id="691a8-129">現在、開発者はアプリのコードを記述してビルドし、生成された資産を IT 担当者に渡します。</span><span class="sxs-lookup"><span data-stu-id="691a8-129">Today, developers write and build the code for an app and then pass the generated assets to the IT Pros.</span></span> <span data-ttu-id="691a8-130">その後、IT 担当者はアプリを再構成し、通常は MSI または最近の App-v パッケージ形式でパッケージを再パッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="691a8-130">Then, the IT Pros reconfigure the app and repackage it, typically in an MSI or more recently in an App-V packaging format.</span></span> <span data-ttu-id="691a8-131">このアプリは、さまざまなチャネルやツールを使用してデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="691a8-131">The app is then deployed through different channels and tools.</span></span> <span data-ttu-id="691a8-132">このアプローチの主な問題の1つは、一般的に "パッケージング paralysis" と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="691a8-132">One of the main problems with this approach is commonly known as "packaging paralysis".</span></span> <span data-ttu-id="691a8-133">問題は、アプリの更新または OS の更新が発生するたびに、このサイクルが繰り返されることです。</span><span class="sxs-lookup"><span data-stu-id="691a8-133">The problem is that this cycle repeats every time there's an app update or an OS update.</span></span>

<span data-ttu-id="691a8-134">このプロセスは、次の図のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="691a8-134">You can see the process reflected on the following picture:</span></span>

![最新の IT ライフサイクルを示す図](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

<span data-ttu-id="691a8-136">企業は、このパッケージ化サイクルを3つの独立したサイクルに分割する方法を必要としています。</span><span class="sxs-lookup"><span data-stu-id="691a8-136">Companies need a way to break this packaging cycle into three independent cycles:</span></span>

- <span data-ttu-id="691a8-137">OS の更新</span><span class="sxs-lookup"><span data-stu-id="691a8-137">OS updates</span></span>
- <span data-ttu-id="691a8-138">アプリケーションの更新</span><span class="sxs-lookup"><span data-stu-id="691a8-138">Application updates</span></span>
- <span data-ttu-id="691a8-139">カスタマイズ</span><span class="sxs-lookup"><span data-stu-id="691a8-139">Customization</span></span>

![最新の IT 好循環サイクルを示す図](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

<span data-ttu-id="691a8-141">前の図は、次のことができることを示しています。</span><span class="sxs-lookup"><span data-stu-id="691a8-141">The previous diagram shows that you can:</span></span>

- <span data-ttu-id="691a8-142">アプリを再パッケージ化しなくても、基になる OS を更新できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-142">Update the underlying OS without having to repackage your apps.</span></span>
- <span data-ttu-id="691a8-143">元の開発者パッケージを再パッケージ化しなくても、カスタマイズを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="691a8-143">Enable customizations from IT without the need to repackage the original developer package.</span></span>

<span data-ttu-id="691a8-144">この根の変化により、次の図に示すように、新しい IT ライフサイクルと最新の IT ライフサイクルが得られます。</span><span class="sxs-lookup"><span data-stu-id="691a8-144">This radical change leads us to the new and modern IT lifecycle as shown in the following picture:</span></span>

![Microsoft ツールを使用したアプリケーションライフサイクルを示す図](./media/deploy-modern-applications/microsoft-it-tools.png)

<span data-ttu-id="691a8-146">開発者がアプリを作成し、MSIX パッケージを生成します。これは、IT 担当者が再パッケージ化の必要なしに使用および構成できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-146">Developers create the app and generate an MSIX package that IT Pros can consume and configure without the need of repackaging.</span></span> <span data-ttu-id="691a8-147">Microsoft では、MSIX テクノロジと共に、パッケージを再パッケージ化せずにカスタマイズおよび構成できるツールを作成しています。</span><span class="sxs-lookup"><span data-stu-id="691a8-147">Along with the MSIX technology, Microsoft has created tools to allow IT to customize and configure packages without repackaging.</span></span>

## <a name="msix-the-next-generation-of-deployment"></a><span data-ttu-id="691a8-148">MSIX: 次世代の配置</span><span class="sxs-lookup"><span data-stu-id="691a8-148">MSIX: The next generation of deployment</span></span>

<span data-ttu-id="691a8-149">MSIX より前のバージョンでは、セットアップウィザード、MSI、ClickOnce、App-v、スクリプトなど、いくつかのパッケージテクノロジが用意されていました。</span><span class="sxs-lookup"><span data-stu-id="691a8-149">Before MSIX, there were several packaging technologies available like setup wizards, MSI, ClickOnce, App-V, and scripting.</span></span> <span data-ttu-id="691a8-150">これらの各テクノロジには独自の強みがあり、Microsoft では、MSIX を構築するための最適なものを選択することにしました。</span><span class="sxs-lookup"><span data-stu-id="691a8-150">Each of these technologies has their own strengths and Microsoft has decided to pick the best of all to build MSIX.</span></span> <span data-ttu-id="691a8-151">MSIX は、これらのテクノロジを最大限に活用することを基礎として構築されています。</span><span class="sxs-lookup"><span data-stu-id="691a8-151">MSIX is built on the foundations of these existing technologies picking the best of each:</span></span>

- <span data-ttu-id="691a8-152">App-v = \> コンテナー化</span><span class="sxs-lookup"><span data-stu-id="691a8-152">App-V =\> Containerization</span></span>
- <span data-ttu-id="691a8-153">ClickOnce = \> 自動更新</span><span class="sxs-lookup"><span data-stu-id="691a8-153">ClickOnce =\> Auto updating</span></span>
- <span data-ttu-id="691a8-154">MSI = \> 簡単に配布</span><span class="sxs-lookup"><span data-stu-id="691a8-154">MSI =\> Easy to distribute</span></span>

<span data-ttu-id="691a8-155">MSIX では、これらすべての機能を備えた1つのインストーラーテクノロジを入手できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-155">With MSIX, you get one installer technology with all these features.</span></span>

![MSIX のビルドに影響を与えるさまざまなテクノロジを示す図](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a><span data-ttu-id="691a8-157">MSIX の利点</span><span class="sxs-lookup"><span data-stu-id="691a8-157">Benefits of MSIX</span></span>

#### <a name="never-regret-installing-an-app"></a><span data-ttu-id="691a8-158">アプリをインストールしないでください</span><span class="sxs-lookup"><span data-stu-id="691a8-158">Never regret installing an app</span></span>

<span data-ttu-id="691a8-159">MSIX は、予測可能で信頼性の高い、安全なデプロイを提供します。</span><span class="sxs-lookup"><span data-stu-id="691a8-159">MSIX provides a predictable, reliable, and safe deployment.</span></span> <span data-ttu-id="691a8-160">パッケージマニフェストに含まれる宣言型のメソッドを使用すると、アプリケーションに必要なすべての資産を OS で追跡できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-160">The declarative method contained in the package manifest lets the OS keep track of every asset your application needs.</span></span> <span data-ttu-id="691a8-161">また、副作用のない真のクリーンアンインストールも提供します。</span><span class="sxs-lookup"><span data-stu-id="691a8-161">It also provides a true clean uninstall with no side effects.</span></span>

#### <a name="disk-space-optimization"></a><span data-ttu-id="691a8-162">ディスク領域の最適化</span><span class="sxs-lookup"><span data-stu-id="691a8-162">Disk space optimization</span></span>

<span data-ttu-id="691a8-163">MSIX は、アプリケーションがユーザーのコンピューターディスク領域に与えるフットプリントを削減するように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="691a8-163">MSIX is optimized to reduce the footprint that an application has on the user's machine disk space.</span></span> <span data-ttu-id="691a8-164">ファイルの単一インスタンスストレージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="691a8-164">It creates a single instance storage of your files.</span></span> <span data-ttu-id="691a8-165">つまり、同じ DLL を持つ2つの異なるパッケージがある場合、DLL は2回インストールされません。</span><span class="sxs-lookup"><span data-stu-id="691a8-165">That is, if you have two different packages with the same DLL, the DLL isn't installed twice.</span></span> <span data-ttu-id="691a8-166">プラットフォームは、特定のアプリによってインストールされたすべてのファイルが宣言的な性質を持つことを認識しているため、この問題に対処します。</span><span class="sxs-lookup"><span data-stu-id="691a8-166">The platform takes care of that problem because it knows all the files that a particular app installed thanks to its declarative nature.</span></span> <span data-ttu-id="691a8-167">また、異なるバージョンの DLL を並行して動作させることもできます。</span><span class="sxs-lookup"><span data-stu-id="691a8-167">It also allows you to have different versions of a DLL working side by side.</span></span>

<span data-ttu-id="691a8-168">リソースパッケージを使用すると、多言語アプリを簡単に作成できます。 OS は、使用されているアプリのインストールを処理します。</span><span class="sxs-lookup"><span data-stu-id="691a8-168">With the use of resource packages, you can easily create multilingual apps and the OS takes care of installing the ones that are used.</span></span>

#### <a name="network-optimization"></a><span data-ttu-id="691a8-169">ネットワーク最適化</span><span class="sxs-lookup"><span data-stu-id="691a8-169">Network optimization</span></span>

<span data-ttu-id="691a8-170">MSIX は、バイトブロックレベルでファイルの相違点を検出し、差分更新と呼ばれる機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="691a8-170">MSIX detects the differences on the files at the byte block level enabling a feature called differential updates.</span></span> <span data-ttu-id="691a8-171">これは、更新されたバイトブロックだけがアプリケーションの更新プログラムにダウンロードされることを意味します。</span><span class="sxs-lookup"><span data-stu-id="691a8-171">What this means is that only the updated byte blocks are downloaded on application updates.</span></span>

![MSIX が差分更新を管理する方法を示す図](./media/deploy-modern-applications/msix-managing-updates.png)

<span data-ttu-id="691a8-173">ストリーミングインストールでは、アプリケーションの他の部分がバックグラウンドでダウンロードされている間に、ユーザーがアプリケーションの作業をすぐに開始できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-173">With streaming installation, the user can quickly start working on your application while other parts of the app are downloaded on the background.</span></span> <span data-ttu-id="691a8-174">この機能は、ユーザーにとって魅力的なエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="691a8-174">This feature contributes to an engaging experience for your users.</span></span>

<span data-ttu-id="691a8-175">オプションのパッケージ機能を使用すると、アプリのデプロイでコンポーネント化を獲得できるため、必要に応じてダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="691a8-175">With the optional packages feature, you achieve componentization on your app deployment, so you can download them when needed.</span></span>

#### <a name="simple-packaging-and-deployment"></a><span data-ttu-id="691a8-176">単純なパッケージ化と配置</span><span class="sxs-lookup"><span data-stu-id="691a8-176">Simple packaging and deployment</span></span>

<span data-ttu-id="691a8-177">Appmanifest.xaml は、バージョン管理、デバイスのターゲット設定、およびすべてのアプリケーションの標準的な方法での識別を宣言します。</span><span class="sxs-lookup"><span data-stu-id="691a8-177">The AppManifest declares the versioning, device targeting and identify in a standard way for every application.</span></span> <span data-ttu-id="691a8-178">また、堅牢なセキュリティ基盤を提供する資産に署名する方法も用意されています。</span><span class="sxs-lookup"><span data-stu-id="691a8-178">It also provides a way to sign your assets providing a solid security foundation.</span></span>

#### <a name="os-managed"></a><span data-ttu-id="691a8-179">OS で管理</span><span class="sxs-lookup"><span data-stu-id="691a8-179">OS managed</span></span>

<span data-ttu-id="691a8-180">OS は、アプリケーションをインストール、更新、および削除するためのすべてのプロセスを処理します。</span><span class="sxs-lookup"><span data-stu-id="691a8-180">The OS handles all the processes for installing, updating, and removing an application.</span></span> <span data-ttu-id="691a8-181">アプリケーションはユーザーごとにインストールされますが、ダウンロードされるのは一度だけです。ディスクフットプリントは最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="691a8-181">Applications are installed per user but downloaded only once, minimizing the disk footprint.</span></span> <span data-ttu-id="691a8-182">Microsoft は、Windows 7 でも MSIX エクスペリエンスの提供に取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="691a8-182">Microsoft is working on providing the MSIX experience also on Windows 7.</span></span>

#### <a name="windows-provides-integrity-for-the-app"></a><span data-ttu-id="691a8-183">Windows はアプリの整合性を提供します</span><span class="sxs-lookup"><span data-stu-id="691a8-183">Windows provides integrity for the app</span></span>

<span data-ttu-id="691a8-184">デジタル署名を使用すると、信頼されていないソースからアプリケーションをインストールしないことを保証できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-184">With the use of digital signatures, you can guarantee that you don't install an application from untrusted sources.</span></span> <span data-ttu-id="691a8-185">MSIX は、次の理由で改ざんを防止します。</span><span class="sxs-lookup"><span data-stu-id="691a8-185">MSIX also prevents tampering because:</span></span>

- <span data-ttu-id="691a8-186">ファイルハッシュの記録を保持します。</span><span class="sxs-lookup"><span data-stu-id="691a8-186">It keeps a record of file hashes.</span></span>
- <span data-ttu-id="691a8-187">インストール後にファイルが変更されたかどうかを検出します。</span><span class="sxs-lookup"><span data-stu-id="691a8-187">It detects if a file has been modified after installation.</span></span>

#### <a name="works-for-the-entire-app-catalog"></a><span data-ttu-id="691a8-188">アプリカタログ全体に対して機能する</span><span class="sxs-lookup"><span data-stu-id="691a8-188">Works for the entire App Catalog</span></span>

<span data-ttu-id="691a8-189">MSIX に関する講演の1つは、アプリケーションカタログ全体、Windows フォーム、WPF、MFC/ATL、Delphi に対して機能することです。これは、xCopy 配置、ClickOnce、またはストアに移動する場合でも、同じ MSIX パッケージを使用できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-189">One of the coolest things about MSIX is that it works for the entire application catalog, Windows Forms, WPF, MFC/ATL, Delphi, even if you want to do xCopy deployment, ClickOnce, or going to the Store, you can use the same MSIX package.</span></span>

### <a name="tools"></a><span data-ttu-id="691a8-190">ツール</span><span class="sxs-lookup"><span data-stu-id="691a8-190">Tools</span></span>

#### <a name="windows-application-packaging-project"></a><span data-ttu-id="691a8-191">Windows アプリケーション パッケージ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="691a8-191">Windows Application Packaging Project</span></span>

<span data-ttu-id="691a8-192">Visual Studio の **Windows アプリケーション パッケージ プロジェクト** というプロジェクトを使用して、デスクトップ アプリのパッケージを生成できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-192">You can use the **Windows Application Packaging Project** project in Visual Studio to generate a package for your desktop app.</span></span> <span data-ttu-id="691a8-193">その後、そのパッケージを Microsoft Store に発行したり、1つまたは複数の Pc にサイドロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="691a8-193">Then, you can publish that package to the Microsoft Store or sideload it onto one or more PCs.</span></span>

#### <a name="msix-packaging-tool"></a><span data-ttu-id="691a8-194">MSIX パッケージ作成ツール</span><span class="sxs-lookup"><span data-stu-id="691a8-194">MSIX Packaging Tool</span></span>

<span data-ttu-id="691a8-195">MSIX Packaging Tool を使用すると、既存の Win32 アプリケーションを MSIX 形式に再パッケージ化できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-195">The MSIX Packaging Tool enables you to repackage your existing Win32 applications to the MSIX format.</span></span> <span data-ttu-id="691a8-196">対話型の UI と変換用のコマンドラインの両方が用意されており、ソースコードを使用せずにアプリケーションを変換することができます。</span><span class="sxs-lookup"><span data-stu-id="691a8-196">It offers both an interactive UI and a command line for conversions and gives you the ability to convert an application without having the source code.</span></span>

![MSIX パッケージ作成ツール](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a><span data-ttu-id="691a8-198">パッケージ サポート フレームワーク</span><span class="sxs-lookup"><span data-stu-id="691a8-198">Package Support Framework</span></span>

<span data-ttu-id="691a8-199">パッケージサポートフレームワークは、ソースコードにアクセスできない場合に、既存の Win32 アプリケーションに修正プログラムを適用するのに役立つオープンソースキットです。これにより、MSIX コンテナーで実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="691a8-199">The Package Support Framework is an open-source kit that helps you apply fixes to your existing Win32 application when you don't have access to the source code, so that it can run in an MSIX container.</span></span> <span data-ttu-id="691a8-200">パッケージ サポート フレームワークは、アプリケーションで最新のランタイム環境のベスト プラクティスに従うのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="691a8-200">The Package Support Framework helps your application follow the best practices of the modern runtime environment.</span></span>

#### <a name="app-installer"></a><span data-ttu-id="691a8-201">アプリ インストーラー</span><span class="sxs-lookup"><span data-stu-id="691a8-201">App Installer</span></span>

<span data-ttu-id="691a8-202">アプリのインストーラーを使用すると、アプリパッケージをダブルクリックすることで、Windows 10 アプリをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="691a8-202">App Installer allows Windows 10 apps to be installed by double-clicking the app package.</span></span> <span data-ttu-id="691a8-203">つまり、ユーザーは、Windows 10 アプリを展開するために PowerShell やその他の開発者ツールを使用する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="691a8-203">This means that users don't need to use PowerShell or other developer tools to deploy Windows 10 apps.</span></span> <span data-ttu-id="691a8-204">また、アプリ インストーラーでは、Web、オプション パッケージ、関連セットからアプリをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="691a8-204">The App Installer can also install an app from the web, optional packages, and related sets.</span></span>

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a><span data-ttu-id="691a8-205">既存の Win32 デスクトップアプリケーションから MSIX パッケージを作成する方法</span><span class="sxs-lookup"><span data-stu-id="691a8-205">How to create an MSIX package from an existing Win32 desktop application</span></span>

<span data-ttu-id="691a8-206">ここでは、既存の Win32 アプリケーションから MSIX パッケージを作成するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="691a8-206">Let's go through the process to create an MSIX package from an existing Win32 application.</span></span> <span data-ttu-id="691a8-207">この例では、Windows フォームアプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="691a8-207">In this example, we'll use a Windows Forms app.</span></span>

<span data-ttu-id="691a8-208">まず、ソリューションに新しいプロジェクトを追加し、[Windows アプリケーションパッケージ] プロジェクトを選択して、名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="691a8-208">To start, add a new project to your solution, select the Windows Application Packaging Project, and give it a name.</span></span>

![新しい Windows アプリケーションパッケージプロジェクトを追加しています](./media/deploy-modern-applications/add-packaging-project.png)

<span data-ttu-id="691a8-210">パッケージプロジェクトの構造が表示され、 *アプリケーション* と呼ばれる特別なフォルダーが記録されます。</span><span class="sxs-lookup"><span data-stu-id="691a8-210">You'll see the structure of the packaging project and note a special folder called *Applications*.</span></span> <span data-ttu-id="691a8-211">このフォルダー内に、パッケージに含めるアプリケーションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-211">Inside this folder, you can specify which applications you want to include in the package.</span></span> <span data-ttu-id="691a8-212">複数の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-212">It can be more than one.</span></span>

![パッケージプロジェクトの構造](./media/deploy-modern-applications/packaging-project.png)

<span data-ttu-id="691a8-214">[ *アプリケーション* ] フォルダーを右クリックし、Visual Studio ソリューションからパッケージ化する Windows フォームプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="691a8-214">Right-click on the *Applications* folder and select the Windows Forms project you want to package from the Visual Studio solution.</span></span>

![パッケージプロジェクトへの Windows フォームプロジェクトの追加](./media/deploy-modern-applications/add-winforms-project.png)

<span data-ttu-id="691a8-216">この時点で、パッケージをコンパイルして生成することはできますが、いくつかのことを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="691a8-216">At this point, you can compile and generate the package but let's examine a couple of things.</span></span> <span data-ttu-id="691a8-217">ユーザーエクスペリエンスを向上させるために、Visual Studio では、最新のアプリケーションがタイルバーと [スタート] メニューのアイコンとタイルアセットを処理するために必要なすべてのビジュアルアセットを自動生成できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-217">To have a better user experience, Visual Studio can autogenerate all the visual assets a modern application needs to handle icons and tile assets for the tile bar and start menu.</span></span> <span data-ttu-id="691a8-218">*Package.appxmanifest* ファイルを開き、マニフェストデザイナーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="691a8-218">Open the *Package.appxmanifest* file to access the Manifest Designer.</span></span> <span data-ttu-id="691a8-219">その後、[ **作成**] をクリックするだけで、プロジェクトに存在する特定のイメージからすべてのビジュアルアセットを生成できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-219">You can then generate all the visual assets from a given image present on your project just by clicking **Create**.</span></span>

![Visual Studio のマニフェストデザイナーのスクリーンショット](./media/deploy-modern-applications/manifest-designer.png)

<span data-ttu-id="691a8-221">*Package.appxmanifest* ファイルのコードを開くと、いくつかの興味深い項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="691a8-221">If you open the code for the *Package.appxmanifest* file, you can see a couple of interesting things.</span></span>

<span data-ttu-id="691a8-222">すぐ下 `<Package>` にノードがあり `<Identity>` ます。</span><span class="sxs-lookup"><span data-stu-id="691a8-222">Right under `<Package>`, there's an `<Identity>` node.</span></span> <span data-ttu-id="691a8-223">これは、パッケージアプリケーションが id を取得する場所であり、OS によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="691a8-223">This is where your packaged application is going to get its identity, which will be managed by the OS.</span></span>

![Id ノード](./media/deploy-modern-applications/identity-node.png)

<span data-ttu-id="691a8-225">ノードでは、 `<Capabilities>` アプリケーションが必要とするすべての要件を見つけることができます。に特に注意してください。これは、 `<rescap:Capability Name="runFullTrust" \>` Win32 アプリケーションであるため、アプリを完全信頼モードで実行するように OS に指示します。</span><span class="sxs-lookup"><span data-stu-id="691a8-225">In the `<Capabilities>` node, you can find all the requirements the application needs, paying special attention to the `<rescap:Capability Name="runFullTrust" \>`, which tells the OS to run the app in full trust mode since it's a Win32 application.</span></span>

![機能ノード](./media/deploy-modern-applications/capabilities-node.png)

<span data-ttu-id="691a8-227">パッケージプロジェクトをソリューションのスタートアッププロジェクトとして設定し、[ *実行*] を選択します。</span><span class="sxs-lookup"><span data-stu-id="691a8-227">Set the packaging project as the startup project for the solution and select *Run*.</span></span> <span data-ttu-id="691a8-228">次のようになります。</span><span class="sxs-lookup"><span data-stu-id="691a8-228">This is going to:</span></span>

- <span data-ttu-id="691a8-229">Windows フォームアプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="691a8-229">Compile the Windows Forms application.</span></span>
- <span data-ttu-id="691a8-230">ビルド結果から MSIX パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="691a8-230">Create an MSIX package out of the build results.</span></span>
- <span data-ttu-id="691a8-231">パッケージを展開します。</span><span class="sxs-lookup"><span data-stu-id="691a8-231">Deploy the packages.</span></span>
- <span data-ttu-id="691a8-232">開発用コンピューターにローカルにインストールします。</span><span class="sxs-lookup"><span data-stu-id="691a8-232">Install it locally on the development machine.</span></span>
- <span data-ttu-id="691a8-233">アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="691a8-233">Launch the app.</span></span>

![インストールされているアプリケーション](./media/deploy-modern-applications/our-installed-application.png)

<span data-ttu-id="691a8-235">これにより、MSIX が Windows 10 に完全に統合された、クリーンインストールおよびアンインストールエクスペリエンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="691a8-235">With this, you have the clean install and uninstall experience that MSIX provides fully integrated into Windows 10.</span></span>

<span data-ttu-id="691a8-236">最後の段階では、MSIX パッケージを別のコンピューターに展開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="691a8-236">The final stage is about how you deploy the MSIX package to another machine.</span></span>

<span data-ttu-id="691a8-237">パッケージプロジェクトを右クリックし、[ **ストア** ] メニューを選択し、[ **アプリパッケージの作成** ] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="691a8-237">Right-click on the packaging project, select the **Store** menu, and then select the **Create App Packages** option.</span></span>

<span data-ttu-id="691a8-238">次に、ストアにアップロードするパッケージを作成するか、サイドローディング用にパッケージを作成するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-238">Then, you can choose between creating a package to upload to the store or creating packages for sideloading.</span></span> <span data-ttu-id="691a8-239">ほとんどの近代化シナリオでは、 **サイドローディング用のパッケージを作成** することを選択します。</span><span class="sxs-lookup"><span data-stu-id="691a8-239">In most modernization scenarios, you'll choose **I want to create packages for sideloading**.</span></span>

![パッケージの構成](./media/deploy-modern-applications/configuring-packages.png)

<span data-ttu-id="691a8-241">ここでは、同じ MSIX パッケージに必要な数だけ含めることができるため、ターゲットにするさまざまなアーキテクチャを選択できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-241">There you can select the different architectures you want to target as you can include as many as you want into the same MSIX package.</span></span>

<span data-ttu-id="691a8-242">最後の手順では、最終的なインストールアセットをデプロイする場所を宣言します。</span><span class="sxs-lookup"><span data-stu-id="691a8-242">The final step is to declare where you want to deploy the final installation assets.</span></span>

![更新設定の構成](./media/deploy-modern-applications/configure-update-settings.png)

<span data-ttu-id="691a8-244">エンタープライズファイルサーバーで共有 UNC パスの web サーバーを使用することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-244">You can choose to use a web server of a shared UNC path on your enterprise file servers.</span></span> <span data-ttu-id="691a8-245">設定に注意を払って、アプリケーションの更新方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="691a8-245">Pay attention to the settings to specify how you want to update your application.</span></span> <span data-ttu-id="691a8-246">アプリケーションの更新については、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="691a8-246">We'll cover application updates in the next section.</span></span>

<span data-ttu-id="691a8-247">詳細な手順ガイドについては、「 [Visual Studio を使用してソースコードからデスクトップアプリをパッケージ化する](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="691a8-247">For a detailed step-by-step guide, see [Package a desktop app from source code using Visual Studio](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).</span></span>

## <a name="auto-updates-in-msix"></a><span data-ttu-id="691a8-248">MSIX での自動更新</span><span class="sxs-lookup"><span data-stu-id="691a8-248">Auto Updates in MSIX</span></span>

<span data-ttu-id="691a8-249">Windows ストアには Windows Update を使用した優れた更新メカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="691a8-249">The Windows Store has a great updating mechanism using Windows Update.</span></span> <span data-ttu-id="691a8-250">ほとんどのエンタープライズシナリオでは、デスクトップアプリの配布にストアを使用しません。</span><span class="sxs-lookup"><span data-stu-id="691a8-250">In most enterprise scenarios, you don't use the Store to distribute your desktop apps.</span></span> <span data-ttu-id="691a8-251">そのため、アプリケーションの更新プログラムを構成してユーザーにプルするのと同様の方法が必要です。</span><span class="sxs-lookup"><span data-stu-id="691a8-251">So, you need a similar way to configure updates for your application and pull them to your users.</span></span>

<span data-ttu-id="691a8-252">Windows 10 の機能と MSIX パッケージの組み合わせを使用すると、ユーザーにとって優れた更新エクスペリエンスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-252">Using a combination of Windows 10 features and MSIX packages, you can provide a great updating experience for your users.</span></span> <span data-ttu-id="691a8-253">実際、ユーザーは技術的には必要ありませんが、シームレスなアプリケーションの更新エクスペリエンスの恩恵を受けることができます。</span><span class="sxs-lookup"><span data-stu-id="691a8-253">In fact, the user doesn't need to be technical at all but still benefit from a seamless application update experience.</span></span>

<span data-ttu-id="691a8-254">次の2つの方法で、ユーザーと対話するように更新プログラムを構成できます。</span><span class="sxs-lookup"><span data-stu-id="691a8-254">You can configure your updates to interact with the user in two different ways:</span></span>

- <span data-ttu-id="691a8-255">ユーザーによる更新のプロンプト: OS には、アプリケーションのインストールが実行されようとしていることをユーザーに通知する、自動生成された優れた UI が表示されます。</span><span class="sxs-lookup"><span data-stu-id="691a8-255">User prompted updates: The OS shows some autogenerated nice UI to notify the user about the application is about to install.</span></span> <span data-ttu-id="691a8-256">この UI は、インストールファイルで指定したプロパティに基づいて構築されます。</span><span class="sxs-lookup"><span data-stu-id="691a8-256">It builds this UI based on the properties you specify on your installation files.</span></span>

- <span data-ttu-id="691a8-257">バックグラウンドでサイレント更新を行います。</span><span class="sxs-lookup"><span data-stu-id="691a8-257">Silent updates in the background.</span></span> <span data-ttu-id="691a8-258">このオプションを使用すると、ユーザーは更新プログラムを意識する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="691a8-258">With this option, your users don't need to be aware of the updates.</span></span>

<span data-ttu-id="691a8-259">また、アプリケーションの起動時または定期的に更新を実行するタイミングを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="691a8-259">You can also configure when you want to perform updates, when the application launches or on a regular basis.</span></span> <span data-ttu-id="691a8-260">サイドローディング機能のおかげで、アプリケーションの実行中にこれらの更新プログラムを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="691a8-260">Thanks to the side-loading features, you can even get these updates while the application is running.</span></span>

<span data-ttu-id="691a8-261">この種類の配置を使用すると、appinstaller という特殊なファイルが作成され *ます。*</span><span class="sxs-lookup"><span data-stu-id="691a8-261">When you use this type of deployment, a special file is created called *.appinstaller*.</span></span> <span data-ttu-id="691a8-262">この単純なファイルには、次のセクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="691a8-262">This simple file contains the following sections:</span></span>

- <span data-ttu-id="691a8-263">*Appinstaller* ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="691a8-263">The location of the *.appinstaller* file</span></span>
- <span data-ttu-id="691a8-264">アプリケーションのメインの MSIX パッケージのプロパティ</span><span class="sxs-lookup"><span data-stu-id="691a8-264">The application's main MSIX package properties</span></span>
- <span data-ttu-id="691a8-265">更新プログラムの動作</span><span class="sxs-lookup"><span data-stu-id="691a8-265">The update behavior</span></span>

![appinstaller ファイル](./media/deploy-modern-applications/appinstaller-file.png)

<span data-ttu-id="691a8-267">Microsoft では、このファイルと組み合わせて、リンクからインストールプロセスを起動するための特別な URL プロトコルを設計しました。</span><span class="sxs-lookup"><span data-stu-id="691a8-267">In combination with this file, Microsoft has designed a special URL protocol to launch the installation process from a link:</span></span>

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

<span data-ttu-id="691a8-268">このプロトコルは、すべてのブラウザーで機能し、Windows 10 の優れたユーザーエクスペリエンスでインストールプロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="691a8-268">This protocol works on all browsers and launches the installation process with a great user experience on Windows 10.</span></span> <span data-ttu-id="691a8-269">OS はインストールプロセスを管理するため、このアプリケーションがインストールされた場所を認識し、プロセスによって影響を受けるすべてのファイルを追跡します。</span><span class="sxs-lookup"><span data-stu-id="691a8-269">Since the OS manages the installation process, it's aware of the location this application was installed from and tracks all the files affected by the process.</span></span>

<span data-ttu-id="691a8-270">MSIX は、パッケージの一部のプロパティを自動的に表示するインストール用のユーザーインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="691a8-270">MSIX creates a user interface for installation automatically showing some properties of the package.</span></span> <span data-ttu-id="691a8-271">これにより、すべてのアプリに共通のインストールエクスペリエンスが実現します。</span><span class="sxs-lookup"><span data-stu-id="691a8-271">This allows for a common installation experience for every app.</span></span>

<span data-ttu-id="691a8-272">新しい MSIX パッケージを生成してデプロイサーバーに移動したら、 *appinstaller* ファイルを編集して、これらの変更を反映する必要があります。これは、主に新しい msix ファイルのバージョンとパスです。</span><span class="sxs-lookup"><span data-stu-id="691a8-272">Once you've generated the new MSIX package and moved it to the deployment server, you just have to edit the *.appinstaller* file to reflect these changes, mainly the version and the path to the new MSIX file.</span></span> <span data-ttu-id="691a8-273">次回ユーザーがアプリケーションを起動したときに、システムは変更を検出し、新しいバージョンのファイルをバックグラウンドでダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="691a8-273">The next time the user launches the application, the system is going to detect the change and download the files for the new version in the background.</span></span> <span data-ttu-id="691a8-274">この処理が完了すると、ユーザーに対して透過的に新しいアプリケーションの起動時にインストールが実行されます。</span><span class="sxs-lookup"><span data-stu-id="691a8-274">When this is done, installation will execute on new application launch transparently for your user.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="691a8-275">[[戻る]](example-migration.md)</span><span class="sxs-lookup"><span data-stu-id="691a8-275">[Previous](example-migration.md)</span></span>
