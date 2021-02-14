---
description: '詳細情報: セキュリティの概要'
title: セキュリティの概要
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: 3aa6e5cbe444e9cfc417d79defce7e89a2034f71
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718825"
---
# <a name="security-overview"></a><span data-ttu-id="6b0b8-103">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="6b0b8-103">Security overview</span></span>

<span data-ttu-id="6b0b8-104">アプリケーションのセキュリティ保護は継続的なプロセスとして行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-104">Securing an application is an ongoing process.</span></span> <span data-ttu-id="6b0b8-105">開発者は、アプリケーションがあらゆる攻撃に対して安全であることを常に保証できるわけではありません。これは、新しい技術がもたらす未知の攻撃を予測することが不可能なためです。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-105">There will never be a point where a developer can guarantee that an application is safe from all attacks, because it is impossible to predict what kinds of future attacks new technologies will bring about.</span></span> <span data-ttu-id="6b0b8-106">反対に、システムに欠陥が発見 (または公開) されていない場合も、そのシステムに欠陥がないとは限りません。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-106">Conversely, just because nobody has yet discovered (or published) security flaws in a system does not mean that none exist or could exist.</span></span> <span data-ttu-id="6b0b8-107">プロジェクトの設計フェーズでセキュリティを考慮することはもちろんのこと、アプリケーションの使用期間を通じてセキュリティをいかに確保してゆくかを計画しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-107">You need to plan for security during the design phase of the project, as well as plan how security will be maintained over the lifetime of the application.</span></span>

## <a name="design-for-security"></a><span data-ttu-id="6b0b8-108">セキュリティのデザイン</span><span class="sxs-lookup"><span data-stu-id="6b0b8-108">Design for Security</span></span>

 <span data-ttu-id="6b0b8-109">セキュリティで保護されたアプリケーションを開発するうえで最大の問題は、プロジェクトのコードが完成した後にセキュリティが導入されるということです。つまり、セキュリティが補足的になりがちです。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-109">One of the biggest problems in developing secure applications is that security is often an afterthought, something to implement after a project is code-complete.</span></span> <span data-ttu-id="6b0b8-110">最初の段階でアプリケーションにセキュリティを導入しておかないと、十分な対策が講じられず、アプリケーションの安全性を損ねる結果となります。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-110">Not building security into an application at the outset leads to insecure applications because little thought has been given to what makes an application secure.</span></span>

 <span data-ttu-id="6b0b8-111">最終段階でセキュリティが実装された場合、新しい制限によりソフトウェアが誤動作を起こしたり、予期していなかった機能を組み込むためにソフトウェアの書き換えが必要となって、バグの発生が増えます。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-111">Last-minute security implementation leads to more bugs, as software breaks under the new restrictions or has to be rewritten to accommodate unanticipated functionality.</span></span> <span data-ttu-id="6b0b8-112">また、書き換えたすべてのコードが新たなバグの原因となる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-112">Every line of revised code contains the possibility of introducing a new bug.</span></span> <span data-ttu-id="6b0b8-113">このような理由から、新しい機能の開発と平行して進めるよう、開発プロセスの早い段階でセキュリティを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-113">For this reason, you should consider security early in the development process so that it can proceed in tandem with the development of new features.</span></span>

### <a name="threat-modeling"></a><span data-ttu-id="6b0b8-114">脅威モデリング</span><span class="sxs-lookup"><span data-stu-id="6b0b8-114">Threat Modeling</span></span>

 <span data-ttu-id="6b0b8-115">システムがどのような攻撃に曝されているかを理解せずに、攻撃からシステムを保護することはできません。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-115">You cannot protect a system against attack unless you understand all the potential attacks that it is exposed to.</span></span> <span data-ttu-id="6b0b8-116">ADO.NET アプリケーション上でセキュリティ違反の可能性およびその影響を調べるには、"*脅威モデリング*" と呼ばれるセキュリティ上の脅威を評価するプロセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-116">The process of evaluating security threats, called *threat modeling*, is necessary to determine the likelihood and ramifications of security breaches in your ADO.NET application.</span></span>

 <span data-ttu-id="6b0b8-117">脅威のモデリングは、1) 攻撃者の視点を理解し、2) システムのセキュリティの特徴を把握し、3) 脅威を特定するという、大きく 3 つの手順で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-117">Threat modeling is composed of three high-level steps: understanding the adversary’s view, characterizing the security of the system, and determining threats.</span></span>

 <span data-ttu-id="6b0b8-118">脅威のモデリングでは、反復的なアプローチによってアプリケーションの脆弱性を評価しながら、最重要データの漏洩につながる最も危険な部分を特定します。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-118">Threat modeling is an iterative approach to assessing vulnerabilities in your application to find those that are the most dangerous because they expose the most sensitive data.</span></span> <span data-ttu-id="6b0b8-119">脆弱性を特定したら、それらを深刻度の順にランクを付けて脅威への一連の対策に優先順位を付けます。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-119">Once you identify the vulnerabilities, you rank them in order of severity and create a prioritized set of countermeasures to counter the threats.</span></span>

<span data-ttu-id="6b0b8-120">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-120">For more information, see the following resources:</span></span>

|<span data-ttu-id="6b0b8-121">リソース</span><span class="sxs-lookup"><span data-stu-id="6b0b8-121">Resource</span></span>|<span data-ttu-id="6b0b8-122">説明</span><span class="sxs-lookup"><span data-stu-id="6b0b8-122">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="6b0b8-123">セキュリティ エンジニアリング ポータルの[脅威モデル化](https://www.microsoft.com/securityengineering/sdl/threatmodeling) サイト</span><span class="sxs-lookup"><span data-stu-id="6b0b8-123">The [Threat Modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) site on the Security Engineering Portal</span></span>|<span data-ttu-id="6b0b8-124">脅威のモデリング プロセスを理解し、開発したアプリケーションの脅威モデルを構築するうえで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-124">The resources on this page will help you understand the threat modeling process and build threat models that you can use to secure your own applications</span></span>|

## <a name="the-principle-of-least-privilege"></a><span data-ttu-id="6b0b8-125">最小特権の原則</span><span class="sxs-lookup"><span data-stu-id="6b0b8-125">The Principle of Least Privilege</span></span>

 <span data-ttu-id="6b0b8-126">アプリケーションの設計、ビルド、および配置は、アプリケーションが攻撃されるという前提で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-126">When you design, build, and deploy your application, you must assume that your application will be attacked.</span></span> <span data-ttu-id="6b0b8-127">多くの場合、こうした攻撃は、コードを実行しているユーザーの権限で悪意のあるコードを実行することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-127">Often these attacks come from malicious code that executes with the permissions of the user running the code.</span></span> <span data-ttu-id="6b0b8-128">高い技術を持った攻撃者が脆弱性を悪用することによって作成したコードも存在します。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-128">Others can originate with well-intentioned code that has been exploited by an attacker.</span></span> <span data-ttu-id="6b0b8-129">セキュリティの計画を立てるときは、常に最悪のシナリオを想定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-129">When planning security, always assume the worst-case scenario will occur.</span></span>

 <span data-ttu-id="6b0b8-130">コードを最小限の特権で実行することによって、できるだけ多層的にコードを防御することが対策の 1 つとして考えられます。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-130">One counter-measure you can employ is to try to erect as many walls around your code as possible by running with least privilege.</span></span> <span data-ttu-id="6b0b8-131">最小限の特権では、常に必要最小限のコードに対し、その処理に必要な最小限の時間だけ権限を与えることが原則となります。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-131">The principle of least privilege says that any given privilege should be granted to the least amount of code necessary for the shortest duration of time that is required to get the job done.</span></span>

 <span data-ttu-id="6b0b8-132">安全なアプリケーションを作成するためのベスト プラクティスは、まず、権限をまったく付与しない状態から始め、その後で、実行しようとする特定のタスクに必要な最小限の権限を追加してゆくことです。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-132">The best practice for creating secure applications is to start with no permissions at all and then add the narrowest permissions for the particular task being performed.</span></span> <span data-ttu-id="6b0b8-133">逆に、すべての権限を与えてから、不要なものを 1 つずつ拒否していく方法では、アプリケーションを危険にさらす結果となります。この場合、意図せずに必要以上の権限を付与することによってセキュリティ ホールを招く可能性があるため、安全性をテストすることも、管理していくことも困難です。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-133">By contrast, starting with all permissions and then denying individual ones leads to insecure applications that are difficult to test and maintain because security holes may exist from unintentionally granting more permissions than required.</span></span>

<span data-ttu-id="6b0b8-134">アプリケーションのセキュリティ保護の詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-134">For more information on securing your applications, see the following resources:</span></span>

|<span data-ttu-id="6b0b8-135">リソース</span><span class="sxs-lookup"><span data-stu-id="6b0b8-135">Resource</span></span>|<span data-ttu-id="6b0b8-136">説明</span><span class="sxs-lookup"><span data-stu-id="6b0b8-136">Description</span></span>|
|--------------|-----------------|
|[<span data-ttu-id="6b0b8-137">アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="6b0b8-137">Securing Applications</span></span>](/visualstudio/ide/securing-applications)|<span data-ttu-id="6b0b8-138">一般的なセキュリティ トピックへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-138">Contains links to general security topics.</span></span> <span data-ttu-id="6b0b8-139">分散アプリケーション、Web アプリケーション、モバイル アプリケーション、およびデスクトップ アプリケーションを保護するためのトピックへのリンクも含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-139">Also contains links to topics for securing distributed applications, Web applications, mobile applications, and desktop applications.</span></span>|

## <a name="code-access-security-cas"></a><span data-ttu-id="6b0b8-140">コード アクセス セキュリティ (CAS)</span><span class="sxs-lookup"><span data-stu-id="6b0b8-140">Code Access Security (CAS)</span></span>

<span data-ttu-id="6b0b8-141">コード アクセス セキュリティ (CAS) は、保護されたリソースや操作に対するコードのアクセスを制限するメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-141">Code access security (CAS) is a mechanism that helps limit the access that code has to protected resources and operations.</span></span> <span data-ttu-id="6b0b8-142">.NET Framework では CAS によって次の機能が実行されます。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-142">In the .NET Framework, CAS performs the following functions:</span></span>

- <span data-ttu-id="6b0b8-143">各種システム リソースにアクセスするための権限や権限セットを定義する。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-143">Defines permissions and permission sets that represent the right to access various system resources.</span></span>

- <span data-ttu-id="6b0b8-144">管理者が一連の権限をコードのグループ (コード グループ) で関連付けることにより、セキュリティ ポリシーを構成できるようにする。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-144">Enables administrators to configure security policy by associating sets of permissions with groups of code (code groups).</span></span>

- <span data-ttu-id="6b0b8-145">実行に不可欠な権限のほか、あった方がよいと思われる権限、決して与えてはならない権限をコードから要求できるようにする。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-145">Enables code to request the permissions it requires in order to run, as well as the permissions that would be useful to have, and specifies which permissions the code must never have.</span></span>

- <span data-ttu-id="6b0b8-146">コードによって要求された権限およびセキュリティ ポリシーによって許可された操作に基づいて、読み込まれた各アセンブリに権限を付与する。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-146">Grants permissions to each assembly that is loaded, based on the permissions requested by the code and on the operations permitted by security policy.</span></span>

- <span data-ttu-id="6b0b8-147">呼び出し元が特定の権限を所有していることをコードから要求できるようにする。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-147">Enables code to demand that its callers have specific permissions.</span></span>

- <span data-ttu-id="6b0b8-148">呼び出し元にデジタル署名があることをコード自身が要求できるようにします。これにより、特定の組織またはサイトからの呼び出し元だけが、保護されたコードを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-148">Enables code to demand that its callers possess a digital signature, thus allowing only callers from a particular organization or site to call the protected code.</span></span>

- <span data-ttu-id="6b0b8-149">呼び出し履歴上で、各呼び出し元に付与された権限を、その呼び出し元に求められる権限と比較することにより、コードに対する制限を実行時に強制する。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-149">Enforces restrictions on code at run time by comparing the granted permissions of every caller on the call stack to the permissions that callers must have.</span></span>

<span data-ttu-id="6b0b8-150">攻撃を許した場合でも損害の規模を最小限に抑えるため、コードのセキュリティ コンテキストを選択し、コードの処理に必要なリソースへの権限だけを付与し、それ以外は実行できないようにする。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-150">To minimize the amount of damage that can occur if an attack succeeds, choose a security context for your code that grants access only to the resources it needs to get its work done and no more.</span></span>

<span data-ttu-id="6b0b8-151">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-151">For more information, see the following resources:</span></span>

|<span data-ttu-id="6b0b8-152">リソース</span><span class="sxs-lookup"><span data-stu-id="6b0b8-152">Resource</span></span>|<span data-ttu-id="6b0b8-153">説明</span><span class="sxs-lookup"><span data-stu-id="6b0b8-153">Description</span></span>|
|--------------|-----------------|
|[<span data-ttu-id="6b0b8-154">コード アクセス セキュリティと ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6b0b8-154">Code Access Security and ADO.NET</span></span>](code-access-security.md)|<span data-ttu-id="6b0b8-155">ADO.NET アプリケーションの観点から、コード アクセス セキュリティ、ロール ベース セキュリティ、および部分信頼環境間の相互作用について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-155">Describes the interactions between code access security, role-based security, and partially trusted environments from the perspective of an ADO.NET application.</span></span>|
|[<span data-ttu-id="6b0b8-156">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6b0b8-156">Code Access Security</span></span>](../../misc/code-access-security.md)|<span data-ttu-id="6b0b8-157">.NET Framework の CAS について説明する追加のトピックへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-157">Contains links to additional topics describing CAS in the .NET Framework.</span></span>|

## <a name="database-security"></a><span data-ttu-id="6b0b8-158">データベース セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6b0b8-158">Database Security</span></span>

<span data-ttu-id="6b0b8-159">最小特権の原則はデータ ソースにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-159">The principle of least privilege also applies to your data source.</span></span> <span data-ttu-id="6b0b8-160">データベース セキュリティの一般的なガイドラインは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-160">Some general guidelines for database security include:</span></span>

- <span data-ttu-id="6b0b8-161">アカウントをできるだけ低い権限で作成する。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-161">Create accounts with the lowest possible privileges.</span></span>

- <span data-ttu-id="6b0b8-162">単にコードの正常動作を目的としてユーザーに管理者アカウントにアクセスさせることは避ける。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-162">Do not allow users access to administrative accounts just to get code working.</span></span>

- <span data-ttu-id="6b0b8-163">サーバー側のエラー メッセージをクライアント アプリケーションに返さない。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-163">Do not return server-side error messages to client applications.</span></span>

- <span data-ttu-id="6b0b8-164">クライアントとサーバーの両方ですべての入力を検証する。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-164">Validate all input at both the client and the server.</span></span>

- <span data-ttu-id="6b0b8-165">動的 SQL ステートメントは避け、パラメーター化コマンドを使用するようにする。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-165">Use parameterized commands and avoid dynamic SQL statements.</span></span>

- <span data-ttu-id="6b0b8-166">データベースのセキュリティ監査とログ記録を有効にし、セキュリティ侵害が発生した場合に警告を受けることができるようにする。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-166">Enable security auditing and logging for the database you are using so that you are alerted to any security breaches.</span></span>

<span data-ttu-id="6b0b8-167">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-167">For more information, see the following resources:</span></span>

|<span data-ttu-id="6b0b8-168">リソース</span><span class="sxs-lookup"><span data-stu-id="6b0b8-168">Resource</span></span>|<span data-ttu-id="6b0b8-169">説明</span><span class="sxs-lookup"><span data-stu-id="6b0b8-169">Description</span></span>|
|--------------|-----------------|
|[<span data-ttu-id="6b0b8-170">SQL Server のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="6b0b8-170">SQL Server Security</span></span>](./sql/sql-server-security.md)|<span data-ttu-id="6b0b8-171">SQL Server のセキュリティの概要を説明します。アプリケーションのシナリオを交えながら、SQL Server を対象とした安全な ADO.NET アプリケーションを作成するための指針を提供します。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-171">Provides an overview of SQL Server security with application scenarios that provide guidance for creating secure ADO.NET applications that target SQL Server.</span></span>|
|<span data-ttu-id="6b0b8-172">[データ アクセス戦略に関する推奨事項](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6b0b8-172">[Recommendations for Data Access Strategies](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))</span></span>|<span data-ttu-id="6b0b8-173">データへのアクセスおよびデータベース操作の実行に関連した推奨事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-173">Provides recommendations for accessing data and performing database operations.</span></span>|

## <a name="security-policy-and-administration"></a><span data-ttu-id="6b0b8-174">セキュリティ ポリシーと管理</span><span class="sxs-lookup"><span data-stu-id="6b0b8-174">Security Policy and Administration</span></span>

<span data-ttu-id="6b0b8-175">コード アクセス セキュリティ (CAS) ポリシーの管理が不適切だと、セキュリティの脆弱性を招く可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-175">Improperly administering code access security (CAS) policy can potentially create security weaknesses.</span></span> <span data-ttu-id="6b0b8-176">アプリケーションを展開した後は、セキュリティ監視技法を適用し、新しい脅威が現れた際はそのリスクを評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-176">Once an application is deployed, techniques for monitoring security should be used and risks evaluated as new threats emerge.</span></span>

<span data-ttu-id="6b0b8-177">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-177">For more information, see the following resources:</span></span>

|<span data-ttu-id="6b0b8-178">リソース</span><span class="sxs-lookup"><span data-stu-id="6b0b8-178">Resource</span></span>|<span data-ttu-id="6b0b8-179">説明</span><span class="sxs-lookup"><span data-stu-id="6b0b8-179">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="6b0b8-180">[セキュリティ ポリシーの管理](/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6b0b8-180">[Security Policy Management](/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))</span></span>|<span data-ttu-id="6b0b8-181">セキュリティ ポリシーの作成と管理について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-181">Provides information on creating and administering security policy.</span></span>|
|<span data-ttu-id="6b0b8-182">[セキュリティ ポリシーのベスト プラクティス](/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6b0b8-182">[Security Policy Best Practices](/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))</span></span>|<span data-ttu-id="6b0b8-183">セキュリティ ポリシーの管理方法について説明したトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="6b0b8-183">Provides links describing how to administer security policy.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6b0b8-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b0b8-184">See also</span></span>

- [<span data-ttu-id="6b0b8-185">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="6b0b8-185">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="6b0b8-186">.NET でのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="6b0b8-186">Security in .NET</span></span>](../../../standard/security/index.md)
- [<span data-ttu-id="6b0b8-187">SQL Server のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="6b0b8-187">SQL Server Security</span></span>](./sql/sql-server-security.md)
- [<span data-ttu-id="6b0b8-188">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="6b0b8-188">ADO.NET Overview</span></span>](ado-net-overview.md)
