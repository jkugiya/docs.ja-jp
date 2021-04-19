---
title: '方法 : サンドボックスで部分信頼コードを実行する'
description: .NET のサンドボックス内で部分的に信頼されたコードを実行する方法を確認します。 AppDomain クラスは、マネージド アプリケーションをサンドボックス化するための効果的な方法です。
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: baa04a3c55728590b8aa502648a8ab42bf62f903
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288282"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="a7c2d-104">方法 : サンドボックスで部分信頼コードを実行する</span><span class="sxs-lookup"><span data-stu-id="a7c2d-104">How to: Run Partially Trusted Code in a Sandbox</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="a7c2d-105">サンドボックス化は、制限されたセキュリティ環境でコードを実行する方法です。この方法を採用すると、コードに付与されるアクセス許可が制限されます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-105">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="a7c2d-106">たとえば、完全に信頼していない発行元のマネージド ライブラリは、完全信頼として実行しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-106">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="a7c2d-107">代わりに、必要なアクセス許可 (<xref:System.Security.Permissions.SecurityPermissionFlag.Execution> アクセス許可など) のみを与えるサンドボックスにコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-107">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="a7c2d-108">また、部分的に信頼された環境で実行する予定のコードについて、サンドボックスを使用してテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-108">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="a7c2d-109"><xref:System.AppDomain> を使用すると、マネージド アプリケーションのサンドボックスを効果的に提供できます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-109">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="a7c2d-110">部分信頼コードの実行時に使用するアプリケーション ドメインには、<xref:System.AppDomain> 内で実行する際に利用できる保護対象リソースを定義するアクセス許可が与えられます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-110">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="a7c2d-111"><xref:System.AppDomain> 内で実行されるコードは、<xref:System.AppDomain> に関連付けられているアクセス許可によって制約され、指定したリソースにのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-111">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="a7c2d-112">また、<xref:System.AppDomain> には、完全信頼として読み込むアセンブリを特定する <xref:System.Security.Policy.StrongName> 配列も含まれます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-112">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="a7c2d-113">これによって <xref:System.AppDomain> の作成者は、新しいサンドボックス化されたドメインを開始して、特定のヘルパー アセンブリを完全信頼とすることができます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-113">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="a7c2d-114">アセンブリを完全信頼として読み込むには、グローバル アセンブリ キャッシュに配置する方法もあります。ただし、そのコンピューター上に作成されたすべてのアプリケーション ドメインに、アセンブリが完全信頼として読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-114">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="a7c2d-115">厳密な名前の一覧は <xref:System.AppDomain> ごとに決定できるので、対象アセンブリのより限定的な指定が可能になります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-115">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="a7c2d-116">サンドボックスで実行するアプリケーションのアクセス許可セットを指定するには、<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> メソッド オーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-116">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="a7c2d-117">このオーバーロードを使用することで、コード アクセス セキュリティのレベルを希望どおりに設定できます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-117">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="a7c2d-118">このオーバーロードを使用して <xref:System.AppDomain> に読み込まれるアセンブリには、指定の許可セットのみを付与することもできますし、完全信頼を付与することもできます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-118">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="a7c2d-119">グローバル アセンブリ キャッシュ内のアセンブリ、または `fullTrustAssemblies` (<xref:System.Security.Policy.StrongName>) 配列パラメーターに列挙されているアセンブリには、完全信頼が付与されます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-119">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="a7c2d-120">完全に信頼できるアセンブリだけを `fullTrustAssemblies` リストに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-120">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="a7c2d-121">オーバーロードは次のシグネチャを持ちます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-121">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="a7c2d-122"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> メソッド オーバーロードのパラメーターでは、<xref:System.AppDomain> の名前、<xref:System.AppDomain> の証拠、サンドボックスのアプリケーション ベースを指定する <xref:System.AppDomainSetup> オブジェクト、使用するアクセス許可セット、および完全に信頼されたアセンブリの厳密な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-122">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="a7c2d-123">セキュリティ上の理由から、`info` パラメーターに指定するアプリケーション ベースに、ホスト アプリケーションのアプリケーション ベースを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-123">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="a7c2d-124">`grantSet` パラメーターには、明示的に作成したアクセス許可セットを指定するか、<xref:System.Security.SecurityManager.GetStandardSandbox%2A> メソッドによって作成された標準アクセス許可セットを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-124">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="a7c2d-125">他の多くの <xref:System.AppDomain> 読み込みとは異なり、部分的に信頼されたアセンブリの許可セットの決定に (`securityInfo` パラメーターで指定される) <xref:System.AppDomain> の証拠は使用されません。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-125">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="a7c2d-126">代わりに、`grantSet` パラメーターによって単独で指定されます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-126">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="a7c2d-127">ただし、分離ストレージのスコープの決定など、他の用途に証拠を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-127">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="a7c2d-128">サンドボックスでアプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="a7c2d-128">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="a7c2d-129">信頼関係のないアプリケーションに付与するアクセス許可セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-129">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="a7c2d-130">付与できる最小限のアクセス許可は <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> です。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-130">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="a7c2d-131">また、信頼関係のないコードでも安全と考えられる追加のアクセス許可を付与することもできます。たとえば、<xref:System.Security.Permissions.IsolatedStorageFilePermission> などです。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-131">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="a7c2d-132">次のコードでは、<xref:System.Security.Permissions.SecurityPermissionFlag.Execution> アクセス許可のみを含む新しいアクセス許可セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-132">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="a7c2d-133">また、"Internet" など、既存の名前付きアクセス許可セットを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-133">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="a7c2d-134">証拠のゾーンに応じて、<xref:System.Security.SecurityManager.GetStandardSandbox%2A> メソッドは `Internet` アクセス許可セットまたは `LocalIntranet` アクセス許可セットを返します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-134">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="a7c2d-135">また、<xref:System.Security.SecurityManager.GetStandardSandbox%2A> は、参照として渡される一部の証拠オブジェクトの ID アクセス許可を構築します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="a7c2d-136">信頼関係のないコードを呼び出すホスト クラス (この例では `Sandboxer`) を含むアセンブリに署名します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-136">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="a7c2d-137">アセンブリの署名で使用した <xref:System.Security.Policy.StrongName> を、<xref:System.Security.Policy.StrongName> を呼び出す際の `fullTrustAssemblies` パラメーターに <xref:System.AppDomain.CreateDomain%2A> 配列として追加します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-137">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="a7c2d-138">部分信頼コードを実行できるようにする場合、または部分信頼アプリケーションにサービスを提供する場合は、ホスト クラスを完全信頼として実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-138">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="a7c2d-139">アセンブリの <xref:System.Security.Policy.StrongName> を読み取る方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-139">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="a7c2d-140">mscorlib や System.dll などの .NET Framework アセンブリを完全信頼一覧に追加することはできません。グローバル アセンブリ キャッシュから完全信頼として読み込まれているためです。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-140">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="a7c2d-141"><xref:System.AppDomain.CreateDomain%2A> メソッドの <xref:System.AppDomainSetup> パラメーターを初期化します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-141">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="a7c2d-142">このパラメーターを使用すると、新しい <xref:System.AppDomain> の多くの設定を制御できます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-142">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="a7c2d-143"><xref:System.AppDomainSetup.ApplicationBase%2A> プロパティは重要な設定なので、ホスト アプリケーションの <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> プロパティとは違う設定にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-143">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="a7c2d-144"><xref:System.AppDomainSetup.ApplicationBase%2A> 設定が同じ場合、部分的に信頼されたアプリケーションは、ホスト アプリケーションが定義する例外を完全信頼として読み込み、それを悪用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-144">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="a7c2d-145">これは、キャッシュ (例外) が推奨されないもう 1 つの理由です。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-145">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="a7c2d-146">ホストのアプリケーション ベースと、サンドボックス アプリケーションのアプリケーション ベースを異なる設定にすると、悪用のリスクが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-146">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="a7c2d-147"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> メソッド オーバーロードを呼び出し、指定したパラメーターを使用してアプリケーション ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-147">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="a7c2d-148">このメソッドのシグネチャは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-148">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="a7c2d-149">追加情報:</span><span class="sxs-lookup"><span data-stu-id="a7c2d-149">Additional information:</span></span>  
  
    - <span data-ttu-id="a7c2d-150">これは、パラメーターとして <xref:System.Security.PermissionSet> を使用する <xref:System.AppDomain.CreateDomain%2A> メソッドの唯一のオーバーロードです。つまり、部分信頼設定でアプリケーションを読み込むことができる唯一のオーバーロードになります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-150">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="a7c2d-151">`evidence` パラメーターは、アクセス許可セットの計算では使用されません。このパラメーターは、.NET Framework の他の機能が識別目的で使用します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-151">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="a7c2d-152">このオーバーロードでは、`info` パラメーターの <xref:System.AppDomainSetup.ApplicationBase%2A> プロパティを必ず設定します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-152">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="a7c2d-153">`fullTrustAssemblies` パラメーターには `params` キーワードがあります。これは <xref:System.Security.Policy.StrongName> 配列を作成する必要がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-153">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="a7c2d-154">パラメーターとして、0 個、1 個、または複数の厳密な名前を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-154">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="a7c2d-155">アプリケーション ドメインを作成するコードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-155">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="a7c2d-156">作成したサンドボックスの <xref:System.AppDomain> にコードを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-156">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="a7c2d-157">これは、2 つの方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-157">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="a7c2d-158">アセンブリに対して <xref:System.AppDomain.ExecuteAssembly%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-158">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="a7c2d-159"><xref:System.Activator.CreateInstanceFrom%2A> メソッドを使用して、<xref:System.MarshalByRefObject> から派生したクラスのインスタンスを新しい <xref:System.AppDomain> に作成します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-159">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="a7c2d-160">2 番目の方が望ましい方法です。新しい <xref:System.AppDomain> インスタンスにパラメーターを渡しやすいためです。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-160">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="a7c2d-161"><xref:System.Activator.CreateInstanceFrom%2A> メソッドには 2 つの重要な機能があります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-161">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="a7c2d-162">アセンブリが保存されていない場所を示すコード ベースを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-162">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="a7c2d-163"><xref:System.Security.CodeAccessPermission.Assert%2A> の下で、完全信頼 (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>) で作成操作を実行できます。こうすることで、重要なクラスのインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-163">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="a7c2d-164">(この状況は、アセンブリに透過マーキングがなく、完全な信頼として読み込まれるときに毎回発生します。)そのため、この関数で信頼するコードのみを作成する場合は注意が必要です。新しいアプリケーション ドメインに、完全信頼クラスのインスタンスのみを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-164">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="a7c2d-165">新しいドメインにクラスのインスタンスを作成するには、そのクラスで <xref:System.MarshalByRefObject> クラスを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-165">To create an instance of a class in a new domain, the class must extend the <xref:System.MarshalByRefObject> class.</span></span>
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="a7c2d-166">新しいドメイン インスタンスをこのドメイン内の参照にラップ解除します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-166">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="a7c2d-167">この参照は、信頼関係のないコードを実行するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-167">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="a7c2d-168">作成した `Sandboxer` クラスのインスタンスで、`ExecuteUntrustedCode` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-168">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="a7c2d-169">この呼び出しは、アクセス許可が制限されているサンドボックス アプリケーション ドメインで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-169">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <span data-ttu-id="a7c2d-170"><xref:System.Reflection> を使用して、部分的に信頼されたアセンブリでメソッドのハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-170"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="a7c2d-171">このハンドルは、最小限のアクセス許可を持つ安全な方法でコードを実行するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-171">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="a7c2d-172">上記のコードでは、<xref:System.Security.SecurityException> を出力する前に完全信頼のアクセス許可の <xref:System.Security.PermissionSet.Assert%2A> があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-172">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="a7c2d-173">完全信頼アサートは、<xref:System.Security.SecurityException> から拡張情報を取得するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-173">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="a7c2d-174"><xref:System.Security.PermissionSet.Assert%2A> を使用しない場合、<xref:System.Security.SecurityException> の <xref:System.Security.SecurityException.ToString%2A> メソッドは、スタック上に部分的に信頼されたコードがあることを検出します。また、返される情報を制限します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-174">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="a7c2d-175">部分信頼コードがその情報を読み取ることができる場合、これによってセキュリティ上の問題が発生する可能性もありますが、<xref:System.Security.Permissions.UIPermission> を付与しないことでそのリスクは軽減されます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-175">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="a7c2d-176">完全信頼アサートは慎重に使用する必要があります。部分信頼コードが完全信頼に昇格できないことが確実である場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-176">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="a7c2d-177">通則として、信頼できないコードは、完全信頼のアサートを呼び出した後に同じ関数で呼び出すのは避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-177">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="a7c2d-178">アサートの使用を完了したときは、常にアサートを元に戻すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-178">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7c2d-179">例</span><span class="sxs-lookup"><span data-stu-id="a7c2d-179">Example</span></span>  

 <span data-ttu-id="a7c2d-180">次の例では、前のセクションの手順を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-180">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="a7c2d-181">この例では、Visual Studio ソリューションの `Sandboxer` というプロジェクトにも `UntrustedCode` というプロジェクトが含まれます。これはクラス `UntrustedClass` を実装します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-181">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="a7c2d-182">このシナリオでは、指定した数字がフィボナッチ数かどうかを示すために、`true` または `false` を返すことが期待されているメソッドを含むライブラリ アセンブリをダウンロードしたことを想定しています。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-182">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="a7c2d-183">代わりに、このメソッドはコンピューターからのファイルの読み込みを試みます。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-183">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="a7c2d-184">次の例は信頼関係のないコードを示します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-184">The following example shows the untrusted code.</span></span>  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a7c2d-185">次の例は、信頼関係のないコードを実行する `Sandboxer` アプリケーション コードを示します。</span><span class="sxs-lookup"><span data-stu-id="a7c2d-185">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7c2d-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7c2d-186">See also</span></span>

- [<span data-ttu-id="a7c2d-187">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="a7c2d-187">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
