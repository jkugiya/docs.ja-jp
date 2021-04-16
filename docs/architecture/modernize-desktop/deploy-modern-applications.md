---
title: 最新デスクトップ アプリケーションのデプロイ
description: モダン デスクトップ アプリケーションのデプロイについて理解しておく必要があるすべての情報。
ms.date: 05/12/2020
ms.openlocfilehash: ba47f09b27adf270734bbfff285fe44dd4175d29
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "98615855"
---
# <a name="deploying-modern-desktop-applications"></a><span data-ttu-id="2f748-103">最新デスクトップ アプリケーションのデプロイ</span><span class="sxs-lookup"><span data-stu-id="2f748-103">Deploying Modern Desktop Applications</span></span>

<span data-ttu-id="2f748-104">デスクトップ アプリケーションを開発する際に考慮すべき 1 つの点は、アプリケーションをパッケージ化してユーザーのコンピューターにデプロイする方法です。</span><span class="sxs-lookup"><span data-stu-id="2f748-104">When you develop desktop applications, one thing to consider is how your application is going to be packaged and deployed to the users' machines.</span></span> <span data-ttu-id="2f748-105">パッケージ化、デプロイ、およびインストールに関する問題は、それらは通常、開発者とは関心の対象が異なる IT プロフェッショナルが担当するということです。</span><span class="sxs-lookup"><span data-stu-id="2f748-105">The problem with packaging, deployment, and installation is that it usually falls under the umbrella of the IT professionals, who care about different things than developers.</span></span>

<span data-ttu-id="2f748-106">今日では、開発者と IT プロフェッショナルが緊密に連携してアプリケーションを運用環境に移行するという DevOps の概念を私たち全員が理解しています。</span><span class="sxs-lookup"><span data-stu-id="2f748-106">These days, we're all familiar with the DevOps concept, where developers and IT Pros work closely to move applications to their production environments.</span></span> <span data-ttu-id="2f748-107">しかし、10 年以上にわたってデスクトップに取り組んできた場合は、次のようなストーリーを目にしたことがあるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="2f748-107">But if you've been in the desktop battle for more than 10 years, you might have seen the following story.</span></span> <span data-ttu-id="2f748-108">開発者チームは、プロジェクトの期限に合わせて懸命に共同作業を行っています。</span><span class="sxs-lookup"><span data-stu-id="2f748-108">A team of developers works together hard to meet the project deadlines.</span></span> <span data-ttu-id="2f748-109">企業の運営には、多くのユーザーのコンピューターでシステムが動作する必要があるため、経営者たちは心配しています。</span><span class="sxs-lookup"><span data-stu-id="2f748-109">Business people are nervous since they need the system working on many user's machines to run the company.</span></span> <span data-ttu-id="2f748-110">"引き渡し" の日、プロジェクト マネージャーはすべての開発者に、コードが正常に動作していて、すべてうまく行っており、出荷できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2f748-110">On "D-Day", the project manager checks with every developer that their code is working well and that everything is fine, so they can ship.</span></span> <span data-ttu-id="2f748-111">そこで、パッケージ チームがアプリのセットアップを生成してすべてのユーザーのコンピューターに配布し、一連のテスト ユーザーがアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="2f748-111">Then, the package team comes in generating the setup for the app, distribute it to every user machine and a set of test users run the application.</span></span> <span data-ttu-id="2f748-112">しかし、実行しようとしても、UI が表示される前に、アプリケーションから "~ メソッドの ~ オブジェクトが失敗しました" という例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2f748-112">Well, they try, because before showing any UI, the application throws an exception that says "Method ~ of object ~ failed".</span></span> <span data-ttu-id="2f748-113">パニックが広がり始め、簡単な調査によって、サード パーティ製のコントロールを導入した疲れた若い開発者が指し示されます。それは、たしかに "開発用コンピューターでは動作していました"。</span><span class="sxs-lookup"><span data-stu-id="2f748-113">Panic starts flowing through the air and a brief investigation points to a young and tired developer that has introduced a third-party control, that certainly "worked on the dev machine".</span></span>

<span data-ttu-id="2f748-114">従来、デスクトップ アプリケーションのインストールは、主に次の 2 つの理由で非常に厄介でした。</span><span class="sxs-lookup"><span data-stu-id="2f748-114">Installing desktop applications have traditionally been a nightmare for two main reasons:</span></span>

- <span data-ttu-id="2f748-115">開発チームと IT チームの間に緊密な共同作業の文化がない。</span><span class="sxs-lookup"><span data-stu-id="2f748-115">Lack of close collaboration culture between dev and IT teams.</span></span>
- <span data-ttu-id="2f748-116">パッケージ化とデプロイの基盤にできる堅牢なテクノロジがない。</span><span class="sxs-lookup"><span data-stu-id="2f748-116">Lack of a solid packaging and deploying technology we can build upon.</span></span>

<span data-ttu-id="2f748-117">実際、次の理由により、アプリをインストールしたことに後悔することがあります。</span><span class="sxs-lookup"><span data-stu-id="2f748-117">In fact, we've been living with the fact that sometimes you regret that you installed an app because:</span></span>

- <span data-ttu-id="2f748-118">最終的に、コンピューターに望ましくない副作用が発生します。</span><span class="sxs-lookup"><span data-stu-id="2f748-118">It ends up having some undesired side effects on your machine.</span></span>
- <span data-ttu-id="2f748-119">以前にインストールされた一部のアプリケーションが動作しなくなります。</span><span class="sxs-lookup"><span data-stu-id="2f748-119">Some applications that were previously installed stop working.</span></span>

<span data-ttu-id="2f748-120">また、アプリをアンインストールするだけでは、システムを元の状態に復元できません。</span><span class="sxs-lookup"><span data-stu-id="2f748-120">Additionally, you can't just restore the system to its original state by uninstalling the app.</span></span> <span data-ttu-id="2f748-121">そのため、"DLL 地獄" や "Winrot" などの造語で呼ぶ、このような状況を経験することが常でした。</span><span class="sxs-lookup"><span data-stu-id="2f748-121">We're so used to live this situation that we've coined terms like "DLL Hell" or "Winrot".</span></span>

<span data-ttu-id="2f748-122">この章では、MSIX について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f748-122">In this chapter, we'll talk about MSIX.</span></span> <span data-ttu-id="2f748-123">MSIX は、Microsoft が提供する最新のテクノロジであり、以前のテクノロジを最大限に活用して、将来のパッケージ化テクノロジの堅牢な基盤を提供しようとしています。</span><span class="sxs-lookup"><span data-stu-id="2f748-123">MSIX is the brand-new technology from Microsoft that tries to capture the best of previous technologies to provide a solid foundation for the packaging technology of the future.</span></span>

<span data-ttu-id="2f748-124">パッケージ化テクノロジは、モダン化に関してどのようなことを行う必要があるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2f748-124">What does a packaging technology have to do with modernization?</span></span> <span data-ttu-id="2f748-125">パッケージ化は、企業の IT にとって基盤となるものであり、多くの資金が投資されています。</span><span class="sxs-lookup"><span data-stu-id="2f748-125">Well, it turns out that packaging is fundamental for the enterprise IT with lots of money invested there.</span></span> <span data-ttu-id="2f748-126">モダン化は、最新のテクノロジを使用することだけに関連しているのではありません。</span><span class="sxs-lookup"><span data-stu-id="2f748-126">Modernization isn't only related to using the latest technologies.</span></span> <span data-ttu-id="2f748-127">ビジネス要件を定義する時点から、企業がクライアントに機能を提供するまでの、市場投入までの時間を短縮することにも関連しています。</span><span class="sxs-lookup"><span data-stu-id="2f748-127">It's also related to reducing time to market from the moment a business requirement is defined until your company delivers the feature to your client.</span></span>

## <a name="the-modern-application-lifecycle"></a><span data-ttu-id="2f748-128">モダン アプリケーションのライフサイクル</span><span class="sxs-lookup"><span data-stu-id="2f748-128">The modern application lifecycle</span></span>

<span data-ttu-id="2f748-129">現在は、開発者がアプリのコードを記述してビルドし、生成された資産を IT プロフェッショナルに渡します。</span><span class="sxs-lookup"><span data-stu-id="2f748-129">Today, developers write and build the code for an app and then pass the generated assets to the IT Pros.</span></span> <span data-ttu-id="2f748-130">次に、IT プロフェッショナルがアプリを再構成し、再パッケージ化します。通常は MSI、さらに最近では App-V パッケージ形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-130">Then, the IT Pros reconfigure the app and repackage it, typically in an MSI or more recently in an App-V packaging format.</span></span> <span data-ttu-id="2f748-131">その後、アプリは、さまざまなチャネルやツールを使用してデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="2f748-131">The app is then deployed through different channels and tools.</span></span> <span data-ttu-id="2f748-132">このアプローチの主な問題の 1 つは、一般に "パッケージ化のまひ状態" として知られています。</span><span class="sxs-lookup"><span data-stu-id="2f748-132">One of the main problems with this approach is commonly known as "packaging paralysis".</span></span> <span data-ttu-id="2f748-133">問題は、アプリの更新または OS の更新が発生するたびに、このサイクルが繰り返されることです。</span><span class="sxs-lookup"><span data-stu-id="2f748-133">The problem is that this cycle repeats every time there's an app update or an OS update.</span></span>

<span data-ttu-id="2f748-134">このプロセスは、次の図で示されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-134">You can see the process reflected on the following picture:</span></span>

![モダン IT ライフサイクルを示す図](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

<span data-ttu-id="2f748-136">企業では、このパッケージ化サイクルを 3 つの独立したサイクルに分割する方法を必要としています。</span><span class="sxs-lookup"><span data-stu-id="2f748-136">Companies need a way to break this packaging cycle into three independent cycles:</span></span>

- <span data-ttu-id="2f748-137">OS の更新</span><span class="sxs-lookup"><span data-stu-id="2f748-137">OS updates</span></span>
- <span data-ttu-id="2f748-138">アプリケーションの更新</span><span class="sxs-lookup"><span data-stu-id="2f748-138">Application updates</span></span>
- <span data-ttu-id="2f748-139">カスタマイズ</span><span class="sxs-lookup"><span data-stu-id="2f748-139">Customization</span></span>

![モダン IT の好循環を示す図](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

<span data-ttu-id="2f748-141">上の図は、次のことができることを示しています。</span><span class="sxs-lookup"><span data-stu-id="2f748-141">The previous diagram shows that you can:</span></span>

- <span data-ttu-id="2f748-142">アプリを再パッケージ化しなくても、基になる OS を更新できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-142">Update the underlying OS without having to repackage your apps.</span></span>
- <span data-ttu-id="2f748-143">元の開発者パッケージを再パッケージ化しなくても、IT 部門でのカスタマイズが可能になります。</span><span class="sxs-lookup"><span data-stu-id="2f748-143">Enable customizations from IT without the need to repackage the original developer package.</span></span>

<span data-ttu-id="2f748-144">この根本的な変更により、新しいモダン IT ライフサイクルは次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="2f748-144">This radical change leads us to the new and modern IT lifecycle as shown in the following picture:</span></span>

![Microsoft ツールを使用したアプリケーション ライフサイクルを示す図](./media/deploy-modern-applications/microsoft-it-tools.png)

<span data-ttu-id="2f748-146">開発者がアプリを作成し、MSIX パッケージを生成します。IT プロフェッショナルは、再パッケージ化の必要なしに、これを使用および構成できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-146">Developers create the app and generate an MSIX package that IT Pros can consume and configure without the need of repackaging.</span></span> <span data-ttu-id="2f748-147">Microsoft では、MSIX テクノロジと共に、パッケージを再パッケージ化せずに IT 部門でカスタマイズおよび構成できるツールを作成しました。</span><span class="sxs-lookup"><span data-stu-id="2f748-147">Along with the MSIX technology, Microsoft has created tools to allow IT to customize and configure packages without repackaging.</span></span>

## <a name="msix-the-next-generation-of-deployment"></a><span data-ttu-id="2f748-148">MSIX: 次世代のデプロイ</span><span class="sxs-lookup"><span data-stu-id="2f748-148">MSIX: The next generation of deployment</span></span>

<span data-ttu-id="2f748-149">MSIX より前は、セットアップ ウィザード、MSI、ClickOnce、App-V、スクリプトなど、いくつかのパッケージ化テクノロジがありました。</span><span class="sxs-lookup"><span data-stu-id="2f748-149">Before MSIX, there were several packaging technologies available like setup wizards, MSI, ClickOnce, App-V, and scripting.</span></span> <span data-ttu-id="2f748-150">これらのテクノロジにはそれぞれ独自の強みがあり、Microsoft では、最適なものを選択して MSIX を構築することにしました。</span><span class="sxs-lookup"><span data-stu-id="2f748-150">Each of these technologies has their own strengths and Microsoft has decided to pick the best of all to build MSIX.</span></span> <span data-ttu-id="2f748-151">MSIX は、これらのテクノロジを基盤とし、それぞれを最大限に活用して構築されています。</span><span class="sxs-lookup"><span data-stu-id="2f748-151">MSIX is built on the foundations of these existing technologies picking the best of each:</span></span>

- <span data-ttu-id="2f748-152">App-V =\> コンテナー化</span><span class="sxs-lookup"><span data-stu-id="2f748-152">App-V =\> Containerization</span></span>
- <span data-ttu-id="2f748-153">ClickOnce =\> 自動更新</span><span class="sxs-lookup"><span data-stu-id="2f748-153">ClickOnce =\> Auto updating</span></span>
- <span data-ttu-id="2f748-154">MSI =\> 簡単に配布</span><span class="sxs-lookup"><span data-stu-id="2f748-154">MSI =\> Easy to distribute</span></span>

<span data-ttu-id="2f748-155">MSIX は、1 つでこれらすべての機能を備えたインストーラー テクノロジとなります。</span><span class="sxs-lookup"><span data-stu-id="2f748-155">With MSIX, you get one installer technology with all these features.</span></span>

![MSIX の構築に影響を与えたさまざまなテクノロジを示す図](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a><span data-ttu-id="2f748-157">MSIX の利点</span><span class="sxs-lookup"><span data-stu-id="2f748-157">Benefits of MSIX</span></span>

#### <a name="never-regret-installing-an-app"></a><span data-ttu-id="2f748-158">アプリをインストールして後悔しない</span><span class="sxs-lookup"><span data-stu-id="2f748-158">Never regret installing an app</span></span>

<span data-ttu-id="2f748-159">MSIX は、予測可能で信頼性の高い、安全なデプロイを提供します。</span><span class="sxs-lookup"><span data-stu-id="2f748-159">MSIX provides a predictable, reliable, and safe deployment.</span></span> <span data-ttu-id="2f748-160">パッケージ マニフェストに含まれている宣言型のメソッドにより、アプリケーションに必要なすべての資産を OS で追跡できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-160">The declarative method contained in the package manifest lets the OS keep track of every asset your application needs.</span></span> <span data-ttu-id="2f748-161">また、副作用のない真にクリーンなアンインストールも提供します。</span><span class="sxs-lookup"><span data-stu-id="2f748-161">It also provides a true clean uninstall with no side effects.</span></span>

#### <a name="disk-space-optimization"></a><span data-ttu-id="2f748-162">ディスク領域の最適化</span><span class="sxs-lookup"><span data-stu-id="2f748-162">Disk space optimization</span></span>

<span data-ttu-id="2f748-163">MSIX は、ユーザーのコンピューターのディスク領域におけるアプリケーションのフットプリントを削減するように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="2f748-163">MSIX is optimized to reduce the footprint that an application has on the user's machine disk space.</span></span> <span data-ttu-id="2f748-164">ユーザーのファイル用に単一インスタンス記憶域が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-164">It creates a single instance storage of your files.</span></span> <span data-ttu-id="2f748-165">つまり、同じ DLL を持つ 2 つの異なるパッケージがある場合、DLL は 2 回インストールされません。</span><span class="sxs-lookup"><span data-stu-id="2f748-165">That is, if you have two different packages with the same DLL, the DLL isn't installed twice.</span></span> <span data-ttu-id="2f748-166">プラットフォームでは、特定のアプリによってインストールされたすべてのファイルがその宣言型の性質によって把握されているため、この問題はプラットフォームで処理されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-166">The platform takes care of that problem because it knows all the files that a particular app installed thanks to its declarative nature.</span></span> <span data-ttu-id="2f748-167">また、異なるバージョンの DLL を並行して動作させることもできます。</span><span class="sxs-lookup"><span data-stu-id="2f748-167">It also allows you to have different versions of a DLL working side by side.</span></span>

<span data-ttu-id="2f748-168">リソース パッケージを使用すると、多言語アプリを簡単に作成でき、使用されるアプリのインストールは OS で処理されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-168">With the use of resource packages, you can easily create multilingual apps and the OS takes care of installing the ones that are used.</span></span>

#### <a name="network-optimization"></a><span data-ttu-id="2f748-169">ネットワーク最適化</span><span class="sxs-lookup"><span data-stu-id="2f748-169">Network optimization</span></span>

<span data-ttu-id="2f748-170">MSIX では、バイト ブロック レベルでファイルの相違点が検出され、差分更新と呼ばれる機能が使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="2f748-170">MSIX detects the differences on the files at the byte block level enabling a feature called differential updates.</span></span> <span data-ttu-id="2f748-171">これは、更新されたバイト ブロックだけがアプリケーションの更新でダウンロードされることを意味します。</span><span class="sxs-lookup"><span data-stu-id="2f748-171">What this means is that only the updated byte blocks are downloaded on application updates.</span></span>

![MSIX で差分更新がどのように管理されるかを示す図](./media/deploy-modern-applications/msix-managing-updates.png)

<span data-ttu-id="2f748-173">ストリーミング インストールを使用すると、ユーザーはアプリケーションの他の部分をバックグラウンドでダウンロードしながら、アプリケーションでの作業をすぐに開始できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-173">With streaming installation, the user can quickly start working on your application while other parts of the app are downloaded on the background.</span></span> <span data-ttu-id="2f748-174">この機能は、ユーザーにとって魅力的なエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2f748-174">This feature contributes to an engaging experience for your users.</span></span>

<span data-ttu-id="2f748-175">オプションのパッケージ機能を使用すると、アプリのデプロイでコンポーネント化を実現できるため、必要に応じてダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="2f748-175">With the optional packages feature, you achieve componentization on your app deployment, so you can download them when needed.</span></span>

#### <a name="simple-packaging-and-deployment"></a><span data-ttu-id="2f748-176">簡単なパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="2f748-176">Simple packaging and deployment</span></span>

<span data-ttu-id="2f748-177">AppManifest は、バージョン管理、デバイスのターゲット設定、および識別を、すべてのアプリケーションに対して標準的な方法で宣言します。</span><span class="sxs-lookup"><span data-stu-id="2f748-177">The AppManifest declares the versioning, device targeting and identify in a standard way for every application.</span></span> <span data-ttu-id="2f748-178">また、資産に署名する方法も用意されており、堅牢なセキュリティ基盤となります。</span><span class="sxs-lookup"><span data-stu-id="2f748-178">It also provides a way to sign your assets providing a solid security foundation.</span></span>

#### <a name="os-managed"></a><span data-ttu-id="2f748-179">OS による管理</span><span class="sxs-lookup"><span data-stu-id="2f748-179">OS managed</span></span>

<span data-ttu-id="2f748-180">アプリケーションのインストール、更新、および削除のプロセスはすべて OS で処理されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-180">The OS handles all the processes for installing, updating, and removing an application.</span></span> <span data-ttu-id="2f748-181">アプリケーションはユーザーごとにインストールされますが、ダウンロードされるのは一度だけで、ディスクのフットプリントは最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="2f748-181">Applications are installed per user but downloaded only once, minimizing the disk footprint.</span></span> <span data-ttu-id="2f748-182">Microsoft では、Windows 7 でも MSIX エクスペリエンスを提供することに取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="2f748-182">Microsoft is working on providing the MSIX experience also on Windows 7.</span></span>

#### <a name="windows-provides-integrity-for-the-app"></a><span data-ttu-id="2f748-183">Windows によってアプリの整合性が提供される</span><span class="sxs-lookup"><span data-stu-id="2f748-183">Windows provides integrity for the app</span></span>

<span data-ttu-id="2f748-184">デジタル署名を使用すると、信頼されていないソースからのアプリケーションをインストールしないことを保証できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-184">With the use of digital signatures, you can guarantee that you don't install an application from untrusted sources.</span></span> <span data-ttu-id="2f748-185">次の理由から、MSIX では改ざんも防止されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-185">MSIX also prevents tampering because:</span></span>

- <span data-ttu-id="2f748-186">ファイル ハッシュの記録を保持します。</span><span class="sxs-lookup"><span data-stu-id="2f748-186">It keeps a record of file hashes.</span></span>
- <span data-ttu-id="2f748-187">インストール後にファイルが変更されたかどうかを検出します。</span><span class="sxs-lookup"><span data-stu-id="2f748-187">It detects if a file has been modified after installation.</span></span>

#### <a name="works-for-the-entire-app-catalog"></a><span data-ttu-id="2f748-188">アプリ カタログ全体に対して機能する</span><span class="sxs-lookup"><span data-stu-id="2f748-188">Works for the entire App Catalog</span></span>

<span data-ttu-id="2f748-189">MSIX の最も優れた点の 1 つは、アプリケーション カタログ全体に対して機能することです。Windows フォーム、WPF、MFC/ATL、Delphi、xCopy によるデプロイ、ClickOnce、またはストアへの移動でも、同じ MSIX パッケージを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-189">One of the coolest things about MSIX is that it works for the entire application catalog, Windows Forms, WPF, MFC/ATL, Delphi, even if you want to do xCopy deployment, ClickOnce, or going to the Store, you can use the same MSIX package.</span></span>

### <a name="tools"></a><span data-ttu-id="2f748-190">ツール</span><span class="sxs-lookup"><span data-stu-id="2f748-190">Tools</span></span>

#### <a name="windows-application-packaging-project"></a><span data-ttu-id="2f748-191">Windows アプリケーション パッケージ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="2f748-191">Windows Application Packaging Project</span></span>

<span data-ttu-id="2f748-192">Visual Studio の **Windows アプリケーション パッケージ プロジェクト** というプロジェクトを使用して、デスクトップ アプリのパッケージを生成できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-192">You can use the **Windows Application Packaging Project** project in Visual Studio to generate a package for your desktop app.</span></span> <span data-ttu-id="2f748-193">その後、そのパッケージを Microsoft Store に発行したり、1 つまたは複数の PC にサイドロードしたりできます。</span><span class="sxs-lookup"><span data-stu-id="2f748-193">Then, you can publish that package to the Microsoft Store or sideload it onto one or more PCs.</span></span>

#### <a name="msix-packaging-tool"></a><span data-ttu-id="2f748-194">MSIX パッケージ作成ツール</span><span class="sxs-lookup"><span data-stu-id="2f748-194">MSIX Packaging Tool</span></span>

<span data-ttu-id="2f748-195">MSIX Packaging Tool を使用すると、既存の Win32 アプリケーションを MSIX 形式に再パッケージ化できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-195">The MSIX Packaging Tool enables you to repackage your existing Win32 applications to the MSIX format.</span></span> <span data-ttu-id="2f748-196">変換用の対話型 UI とコマンド ラインの両方が用意されており、ソース コードなしでアプリケーションを変換することができます。</span><span class="sxs-lookup"><span data-stu-id="2f748-196">It offers both an interactive UI and a command line for conversions and gives you the ability to convert an application without having the source code.</span></span>

![MSIX パッケージ作成ツール](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a><span data-ttu-id="2f748-198">パッケージ サポート フレームワーク</span><span class="sxs-lookup"><span data-stu-id="2f748-198">Package Support Framework</span></span>

<span data-ttu-id="2f748-199">パッケージ サポート フレームワークは、ソース コードにアクセスできない場合に既存の Win32 アプリケーションに修正を適用して MSIX コンテナー内で実行できるようにするのに役立つオープン ソース キットです。</span><span class="sxs-lookup"><span data-stu-id="2f748-199">The Package Support Framework is an open-source kit that helps you apply fixes to your existing Win32 application when you don't have access to the source code, so that it can run in an MSIX container.</span></span> <span data-ttu-id="2f748-200">パッケージ サポート フレームワークは、アプリケーションで最新のランタイム環境のベスト プラクティスに従うのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2f748-200">The Package Support Framework helps your application follow the best practices of the modern runtime environment.</span></span>

#### <a name="app-installer"></a><span data-ttu-id="2f748-201">アプリ インストーラー</span><span class="sxs-lookup"><span data-stu-id="2f748-201">App Installer</span></span>

<span data-ttu-id="2f748-202">アプリ インストーラーを使用すると、アプリ パッケージをダブルクリックして Windows 10 アプリをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="2f748-202">App Installer allows Windows 10 apps to be installed by double-clicking the app package.</span></span> <span data-ttu-id="2f748-203">つまり、ユーザーは、Windows 10 アプリをデプロイするために PowerShell やその他の開発者ツールを使用する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="2f748-203">This means that users don't need to use PowerShell or other developer tools to deploy Windows 10 apps.</span></span> <span data-ttu-id="2f748-204">また、アプリ インストーラーでは、Web、オプション パッケージ、関連セットからアプリをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2f748-204">The App Installer can also install an app from the web, optional packages, and related sets.</span></span>

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a><span data-ttu-id="2f748-205">既存の Win32 デスクトップ アプリケーションから MSIX パッケージを作成する方法</span><span class="sxs-lookup"><span data-stu-id="2f748-205">How to create an MSIX package from an existing Win32 desktop application</span></span>

<span data-ttu-id="2f748-206">ここでは、既存の Win32 アプリケーションから MSIX パッケージを作成するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2f748-206">Let's go through the process to create an MSIX package from an existing Win32 application.</span></span> <span data-ttu-id="2f748-207">この例では、Windows フォーム アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="2f748-207">In this example, we'll use a Windows Forms app.</span></span>

<span data-ttu-id="2f748-208">まず、ソリューションに新しいプロジェクトを追加し、[Windows アプリケーション パッケージ プロジェクト] を選択して、名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="2f748-208">To start, add a new project to your solution, select the Windows Application Packaging Project, and give it a name.</span></span>

![新しい Windows アプリケーション パッケージ プロジェクトの追加](./media/deploy-modern-applications/add-packaging-project.png)

<span data-ttu-id="2f748-210">パッケージ プロジェクトの構造が表示され、"*アプリケーション*" という名前の特別なフォルダーがあります。</span><span class="sxs-lookup"><span data-stu-id="2f748-210">You'll see the structure of the packaging project and note a special folder called *Applications*.</span></span> <span data-ttu-id="2f748-211">このフォルダー内に、パッケージに含めるアプリケーションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-211">Inside this folder, you can specify which applications you want to include in the package.</span></span> <span data-ttu-id="2f748-212">複数指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f748-212">It can be more than one.</span></span>

![パッケージ プロジェクトの構造](./media/deploy-modern-applications/packaging-project.png)

<span data-ttu-id="2f748-214">"*アプリケーション*" フォルダーを右クリックし、Visual Studio ソリューションからパッケージ化する Windows フォーム プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="2f748-214">Right-click on the *Applications* folder and select the Windows Forms project you want to package from the Visual Studio solution.</span></span>

![パッケージ プロジェクトへの Windows フォーム プロジェクトの追加](./media/deploy-modern-applications/add-winforms-project.png)

<span data-ttu-id="2f748-216">この時点で、パッケージをコンパイルして生成することはできますが、いくつかのことを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="2f748-216">At this point, you can compile and generate the package but let's examine a couple of things.</span></span> <span data-ttu-id="2f748-217">ユーザー エクスペリエンスを向上させるために、Visual Studio では、モダン アプリケーションでタイルバーとスタート メニューのアイコンとタイル資産を処理するために必要な、すべてのビジュアル資産を自動生成できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-217">To have a better user experience, Visual Studio can autogenerate all the visual assets a modern application needs to handle icons and tile assets for the tile bar and start menu.</span></span> <span data-ttu-id="2f748-218">*Package.appxmanifest* ファイルを開き、マニフェスト デザイナーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2f748-218">Open the *Package.appxmanifest* file to access the Manifest Designer.</span></span> <span data-ttu-id="2f748-219">その後、 **[作成]** をクリックするだけで、プロジェクトに存在する特定のイメージからすべてのビジュアル資産を生成できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-219">You can then generate all the visual assets from a given image present on your project just by clicking **Create**.</span></span>

![Visual Studio のマニフェスト デザイナーのスクリーンショット](./media/deploy-modern-applications/manifest-designer.png)

<span data-ttu-id="2f748-221">*Package.appxmanifest* ファイルのコードを開くと、いくつかの興味深い項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-221">If you open the code for the *Package.appxmanifest* file, you can see a couple of interesting things.</span></span>

<span data-ttu-id="2f748-222">`<Package>` のすぐ下に `<Identity>` ノードがあります。</span><span class="sxs-lookup"><span data-stu-id="2f748-222">Right under `<Package>`, there's an `<Identity>` node.</span></span> <span data-ttu-id="2f748-223">パッケージ化されたアプリケーションにここで ID が与えられ、OS によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-223">This is where your packaged application is going to get its identity, which will be managed by the OS.</span></span>

![Identity ノード](./media/deploy-modern-applications/identity-node.png)

<span data-ttu-id="2f748-225">`<Capabilities>` ノードには、アプリケーションに必要なすべての要件が含まれています。特に `<rescap:Capability Name="runFullTrust" \>` に注目してください。これは、Win32 アプリケーションであるため、アプリを完全信頼モードで実行するように OS に指示しています。</span><span class="sxs-lookup"><span data-stu-id="2f748-225">In the `<Capabilities>` node, you can find all the requirements the application needs, paying special attention to the `<rescap:Capability Name="runFullTrust" \>`, which tells the OS to run the app in full trust mode since it's a Win32 application.</span></span>

![Capabilities ノード](./media/deploy-modern-applications/capabilities-node.png)

<span data-ttu-id="2f748-227">パッケージ プロジェクトをソリューションのスタートアッププロジェクトとして設定し、 *[実行]* を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f748-227">Set the packaging project as the startup project for the solution and select *Run*.</span></span> <span data-ttu-id="2f748-228">これによって次のことが行われます。</span><span class="sxs-lookup"><span data-stu-id="2f748-228">This is going to:</span></span>

- <span data-ttu-id="2f748-229">Windows フォーム アプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="2f748-229">Compile the Windows Forms application.</span></span>
- <span data-ttu-id="2f748-230">ビルド結果から MSIX パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="2f748-230">Create an MSIX package out of the build results.</span></span>
- <span data-ttu-id="2f748-231">パッケージをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="2f748-231">Deploy the packages.</span></span>
- <span data-ttu-id="2f748-232">開発用コンピューターにローカルにインストールします。</span><span class="sxs-lookup"><span data-stu-id="2f748-232">Install it locally on the development machine.</span></span>
- <span data-ttu-id="2f748-233">アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="2f748-233">Launch the app.</span></span>

![インストールされているアプリケーション](./media/deploy-modern-applications/our-installed-application.png)

<span data-ttu-id="2f748-235">これにより、MSIX で提供されるクリーンなインストールとアンインストールのエクスペリエンスが、Windows 10 に完全に統合されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-235">With this, you have the clean install and uninstall experience that MSIX provides fully integrated into Windows 10.</span></span>

<span data-ttu-id="2f748-236">最後の段階では、MSIX パッケージを別のコンピューターにデプロイする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f748-236">The final stage is about how you deploy the MSIX package to another machine.</span></span>

<span data-ttu-id="2f748-237">パッケージ プロジェクトを右クリックし、 **[ストア]** メニューを選択し、 **[アプリ パッケージの作成]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="2f748-237">Right-click on the packaging project, select the **Store** menu, and then select the **Create App Packages** option.</span></span>

<span data-ttu-id="2f748-238">次に、ストアにアップロードするパッケージを作成するか、サイドローディング用にパッケージを作成するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-238">Then, you can choose between creating a package to upload to the store or creating packages for sideloading.</span></span> <span data-ttu-id="2f748-239">ほとんどのモダン化シナリオでは、 **[サイドローディング用のパッケージを作成します]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f748-239">In most modernization scenarios, you'll choose **I want to create packages for sideloading**.</span></span>

![パッケージの構成](./media/deploy-modern-applications/configuring-packages.png)

<span data-ttu-id="2f748-241">ここでは、同じ MSIX パッケージに必要な数だけ含めることができるため、ターゲットにするさまざまなアーキテクチャを選択できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-241">There you can select the different architectures you want to target as you can include as many as you want into the same MSIX package.</span></span>

<span data-ttu-id="2f748-242">最後の手順では、最終的なインストール資産をデプロイする場所を宣言します。</span><span class="sxs-lookup"><span data-stu-id="2f748-242">The final step is to declare where you want to deploy the final installation assets.</span></span>

![更新設定の構成](./media/deploy-modern-applications/configure-update-settings.png)

<span data-ttu-id="2f748-244">エンタープライズ ファイル サーバーで共有 UNC パスの Web サーバーを使用することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-244">You can choose to use a web server of a shared UNC path on your enterprise file servers.</span></span> <span data-ttu-id="2f748-245">アプリケーションの更新方法を指定する設定に注意を払ってください。</span><span class="sxs-lookup"><span data-stu-id="2f748-245">Pay attention to the settings to specify how you want to update your application.</span></span> <span data-ttu-id="2f748-246">アプリケーションの更新については、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="2f748-246">We'll cover application updates in the next section.</span></span>

<span data-ttu-id="2f748-247">詳細な手順ガイドについては、[Visual Studio を使用してソース コードからデスクトップ アプリをパッケージ化する](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net)方法に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f748-247">For a detailed step-by-step guide, see [Package a desktop app from source code using Visual Studio](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).</span></span>

## <a name="auto-updates-in-msix"></a><span data-ttu-id="2f748-248">MSIX での自動更新</span><span class="sxs-lookup"><span data-stu-id="2f748-248">Auto Updates in MSIX</span></span>

<span data-ttu-id="2f748-249">Windows ストアには Windows Update を使用した優れた更新メカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="2f748-249">The Windows Store has a great updating mechanism using Windows Update.</span></span> <span data-ttu-id="2f748-250">ほとんどのエンタープライズ シナリオでは、デスクトップ アプリの配布にストアを使用しません。</span><span class="sxs-lookup"><span data-stu-id="2f748-250">In most enterprise scenarios, you don't use the Store to distribute your desktop apps.</span></span> <span data-ttu-id="2f748-251">したがって、アプリケーションの更新を構成してユーザーにプルするために、類似の方法が必要です。</span><span class="sxs-lookup"><span data-stu-id="2f748-251">So, you need a similar way to configure updates for your application and pull them to your users.</span></span>

<span data-ttu-id="2f748-252">Windows 10 の機能と MSIX パッケージの組み合わせを使用すると、優れた更新エクスペリエンスをユーザーに提供できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-252">Using a combination of Windows 10 features and MSIX packages, you can provide a great updating experience for your users.</span></span> <span data-ttu-id="2f748-253">実際、ユーザーは技術に熟達している必要はなく、シームレスなアプリケーションの更新エクスペリエンスの恩恵を受けることができます。</span><span class="sxs-lookup"><span data-stu-id="2f748-253">In fact, the user doesn't need to be technical at all but still benefit from a seamless application update experience.</span></span>

<span data-ttu-id="2f748-254">次の 2 つの方法でユーザーと対話するように更新を構成できます。</span><span class="sxs-lookup"><span data-stu-id="2f748-254">You can configure your updates to interact with the user in two different ways:</span></span>

- <span data-ttu-id="2f748-255">ユーザーに通知される更新: OS によって自動生成された適切な UI が 表示され、アプリケーションのインストールが実行されようとしていることをユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2f748-255">User prompted updates: The OS shows some autogenerated nice UI to notify the user about the application is about to install.</span></span> <span data-ttu-id="2f748-256">この UI は、インストール ファイルで指定したプロパティに基づいて構築されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-256">It builds this UI based on the properties you specify on your installation files.</span></span>

- <span data-ttu-id="2f748-257">バックグラウンドでのサイレント更新。</span><span class="sxs-lookup"><span data-stu-id="2f748-257">Silent updates in the background.</span></span> <span data-ttu-id="2f748-258">このオプションを使用すると、ユーザーは更新を意識する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="2f748-258">With this option, your users don't need to be aware of the updates.</span></span>

<span data-ttu-id="2f748-259">また、アプリケーションの起動時または定期的に実行するように、更新のタイミングを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f748-259">You can also configure when you want to perform updates, when the application launches or on a regular basis.</span></span> <span data-ttu-id="2f748-260">サイドローディング機能のおかげで、アプリケーションの実行中にこれらの更新プログラムを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f748-260">Thanks to the side-loading features, you can even get these updates while the application is running.</span></span>

<span data-ttu-id="2f748-261">この種類のデプロイを使用すると、 *.appinstaller* という特殊なファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-261">When you use this type of deployment, a special file is created called *.appinstaller*.</span></span> <span data-ttu-id="2f748-262">この単純なファイルには、次のセクションがあります。</span><span class="sxs-lookup"><span data-stu-id="2f748-262">This simple file contains the following sections:</span></span>

- <span data-ttu-id="2f748-263">*.appinstaller* ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="2f748-263">The location of the *.appinstaller* file</span></span>
- <span data-ttu-id="2f748-264">アプリケーションのメイン MSIX パッケージのプロパティ</span><span class="sxs-lookup"><span data-stu-id="2f748-264">The application's main MSIX package properties</span></span>
- <span data-ttu-id="2f748-265">更新の動作</span><span class="sxs-lookup"><span data-stu-id="2f748-265">The update behavior</span></span>

![.appinstaller ファイル](./media/deploy-modern-applications/appinstaller-file.png)

<span data-ttu-id="2f748-267">Microsoft では、このファイルと組み合わせて、リンクからインストール プロセスを起動するための特別な URL プロトコルを設計しました。</span><span class="sxs-lookup"><span data-stu-id="2f748-267">In combination with this file, Microsoft has designed a special URL protocol to launch the installation process from a link:</span></span>

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

<span data-ttu-id="2f748-268">このプロトコルは、すべてのブラウザーで機能し、Windows 10 の優れたユーザー エクスペリエンスでインストール プロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="2f748-268">This protocol works on all browsers and launches the installation process with a great user experience on Windows 10.</span></span> <span data-ttu-id="2f748-269">OS は、インストール プロセスを管理しているため、このアプリケーションがどの場所からインストールされたかを認識し、プロセスによる影響を受けるすべてのファイルを追跡します。</span><span class="sxs-lookup"><span data-stu-id="2f748-269">Since the OS manages the installation process, it's aware of the location this application was installed from and tracks all the files affected by the process.</span></span>

<span data-ttu-id="2f748-270">MSIX は、インストール用のユーザー インターフェイスを自動的に作成して、パッケージの一部のプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="2f748-270">MSIX creates a user interface for installation automatically showing some properties of the package.</span></span> <span data-ttu-id="2f748-271">これにより、すべてのアプリに共通のインストール エクスペリエンスが実現します。</span><span class="sxs-lookup"><span data-stu-id="2f748-271">This allows for a common installation experience for every app.</span></span>

<span data-ttu-id="2f748-272">新しい MSIX パッケージを生成してデプロイ サーバーに移動したら、 *.appinstaller* ファイルを編集して、これらの変更を反映する必要があります。主に、新しい MSIX ファイルのバージョンとパスです。</span><span class="sxs-lookup"><span data-stu-id="2f748-272">Once you've generated the new MSIX package and moved it to the deployment server, you just have to edit the *.appinstaller* file to reflect these changes, mainly the version and the path to the new MSIX file.</span></span> <span data-ttu-id="2f748-273">ユーザーがアプリケーションを次回起動したときに、システムによって変更が検出され、新しいバージョンのファイルがバックグラウンドでダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="2f748-273">The next time the user launches the application, the system is going to detect the change and download the files for the new version in the background.</span></span> <span data-ttu-id="2f748-274">この処理が完了すると、新しいアプリケーションの起動時にユーザーには透過的にインストールが実行されます。</span><span class="sxs-lookup"><span data-stu-id="2f748-274">When this is done, installation will execute on new application launch transparently for your user.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2f748-275">[[戻る]](example-migration.md)</span><span class="sxs-lookup"><span data-stu-id="2f748-275">[Previous](example-migration.md)</span></span>
