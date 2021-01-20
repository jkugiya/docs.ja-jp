---
title: 最新のデスクトップアプリケーションの移行
description: 最新のデスクトップアプリケーションの移行プロセスについて理解しておく必要があること。
ms.date: 01/19/2021
ms.openlocfilehash: b5bea6e601dc040adfd8ed410320a3416cb3372e
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615764"
---
# <a name="migrating-modern-desktop-applications"></a><span data-ttu-id="a8726-103">最新のデスクトップアプリケーションの移行</span><span class="sxs-lookup"><span data-stu-id="a8726-103">Migrating Modern Desktop applications</span></span>

<span data-ttu-id="a8726-104">この章では、既存のアプリケーションを .NET Framework から .NET に移行する際に直面する可能性がある、最も一般的な問題と課題について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8726-104">In this chapter, we're exploring the most common issues and challenges you can face when migrating an existing application from .NET Framework to .NET.</span></span>

<span data-ttu-id="a8726-105">複雑なデスクトップアプリケーションは、独立して動作せず、ローカルコンピューターまたはリモートサーバー上に存在する可能性があるサブシステムとの対話を必要とします。</span><span class="sxs-lookup"><span data-stu-id="a8726-105">A complex desktop application doesn't work in isolation and needs some kind of interaction with subsystems that may reside on the local machine or on a remote server.</span></span> <span data-ttu-id="a8726-106">多くの場合、永続化ストレージとしてローカルまたはリモートで接続するには、何らかの種類のデータベースが必要になります。</span><span class="sxs-lookup"><span data-stu-id="a8726-106">It will probably need some kind of database to connect as a persistence storage either locally or remotely.</span></span> <span data-ttu-id="a8726-107">インターネットとサービス指向アーキテクチャの向上により、アプリケーションは、リモートサーバーまたはクラウドに存在する何らかのサービスに接続することが一般的です。</span><span class="sxs-lookup"><span data-stu-id="a8726-107">With the raise of Internet and service-oriented architectures, it's common to have your application connected to some sort of service residing on a remote server or in the cloud.</span></span> <span data-ttu-id="a8726-108">一部の機能を実装するには、コンピューターのファイルシステムにアクセスする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-108">You may need to access the machine file system to implement some functionality.</span></span> <span data-ttu-id="a8726-109">または、アプリケーションの外部にある COM オブジェクト内に存在する機能を使用している場合もあります。たとえば、アプリに Office アセンブリを統合している場合は、一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="a8726-109">Alternatively, maybe you're using a piece of functionality that resides inside a COM object outside your application, which is a common scenario if, for example, you're integrating Office assemblies in your app.</span></span>

<span data-ttu-id="a8726-110">また、.NET Framework と .NET によって公開される API サーフェイスには違いがあり、.NET Framework で利用できる一部の機能は .NET では使用できません。</span><span class="sxs-lookup"><span data-stu-id="a8726-110">Besides, there are differences in the API surface that is exposed by .NET Framework and .NET, and some features that are available on .NET Framework aren't available on .NET.</span></span> <span data-ttu-id="a8726-111">そのため、移行を計画する際には、それらを把握して考慮することが重要です。</span><span class="sxs-lookup"><span data-stu-id="a8726-111">So, it's important for you to know and take them into account when planning a migration.</span></span>

## <a name="configuration-files"></a><span data-ttu-id="a8726-112">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="a8726-112">Configuration files</span></span>

<span data-ttu-id="a8726-113">構成ファイルを利用すると、実行時に読み取られるプロパティのセットを格納して、アプリケーションの動作に影響を与えることができます。たとえば、データベースを配置する場所や、ループを実行する回数などです。</span><span class="sxs-lookup"><span data-stu-id="a8726-113">Configuration files offer the possibility to store sets of properties that are read at run time and affect the behavior of our apps, such as where to locate a database or how many times to execute a loop.</span></span> <span data-ttu-id="a8726-114">この手法の利点は、アプリケーションの一部の側面を再書き込みと再コンパイルせずに変更できることです。</span><span class="sxs-lookup"><span data-stu-id="a8726-114">The beauty of this technique is that you can modify some aspects of the application without the need to recode and recompile.</span></span> <span data-ttu-id="a8726-115">これは、たとえば、同じアプリコードが、特定の構成値のセットを持つ開発環境で実行され、別の構成値を持つ運用環境で実行される場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a8726-115">This comes in handy when, for example, the same app code runs on a development environment with a certain set of configuration values and in production with a different one.</span></span>

### <a name="configuration-on-net-framework"></a><span data-ttu-id="a8726-116">.NET Framework での構成</span><span class="sxs-lookup"><span data-stu-id="a8726-116">Configuration on .NET Framework</span></span>

<span data-ttu-id="a8726-117">動作中の .NET Framework デスクトップアプリケーションがある場合、名前空間からクラスを介してアクセスされる *app.config* ファイルがある可能性があり <xref:System.Configuration.AppSettingsSection> `System.Configuration` ます。</span><span class="sxs-lookup"><span data-stu-id="a8726-117">If you have a working .NET Framework desktop application, chances are you have an *app.config* file accessed through the <xref:System.Configuration.AppSettingsSection> class from the `System.Configuration` namespace.</span></span>

<span data-ttu-id="a8726-118">.NET Framework インフラストラクチャ内には、親からプロパティを継承する構成ファイルの階層があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-118">Within the .NET Framework infrastructure, there's a hierarchy of configuration files that inherit properties from its parents.</span></span> <span data-ttu-id="a8726-119">子孫構成ファイルで使用またはオーバーライドできる多くのプロパティと構成セクションを定義する *machine.config* ファイルを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="a8726-119">You can find a *machine.config* file that defines many properties and configuration sections that can be used or overridden in any descendant configuration file.</span></span>

### <a name="configuration-on-net"></a><span data-ttu-id="a8726-120">.NET での構成</span><span class="sxs-lookup"><span data-stu-id="a8726-120">Configuration on .NET</span></span>

<span data-ttu-id="a8726-121">.NET の世界では、 *machine.config* ファイルはありません。</span><span class="sxs-lookup"><span data-stu-id="a8726-121">In the .NET world, there's no *machine.config* file.</span></span> <span data-ttu-id="a8726-122">また、以前の方法の名前空間を使用し続けることもできますが、 <xref:System.Configuration> <xref:Microsoft.Extensions.Configuration> 多くの拡張機能を備えた最新のに切り替えることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a8726-122">And even though you can continue to use the old fashioned <xref:System.Configuration> namespace, you may consider switching to the modern <xref:Microsoft.Extensions.Configuration>, which offers a good number of enhancements.</span></span>

<span data-ttu-id="a8726-123">構成 API は、構成プロバイダーの概念をサポートします。構成プロバイダーは、構成の読み込みに使用されるデータソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="a8726-123">The configuration API supports the concept of configuration provider, which defines the data source to be used to load the configuration.</span></span> <span data-ttu-id="a8726-124">組み込みプロバイダーには、次のような種類があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-124">There are different kinds of built-in providers, such as:</span></span>

- <span data-ttu-id="a8726-125">メモリ内 .NET オブジェクト</span><span class="sxs-lookup"><span data-stu-id="a8726-125">In-memory .NET objects</span></span>
- <span data-ttu-id="a8726-126">INI ファイル</span><span class="sxs-lookup"><span data-stu-id="a8726-126">INI files</span></span>
- <span data-ttu-id="a8726-127">JSON ファイル</span><span class="sxs-lookup"><span data-stu-id="a8726-127">JSON files</span></span>
- <span data-ttu-id="a8726-128">XML ファイル</span><span class="sxs-lookup"><span data-stu-id="a8726-128">XML files</span></span>
- <span data-ttu-id="a8726-129">コマンド ライン引数</span><span class="sxs-lookup"><span data-stu-id="a8726-129">Command-line arguments</span></span>
- <span data-ttu-id="a8726-130">環境変数</span><span class="sxs-lookup"><span data-stu-id="a8726-130">Environment variables</span></span>
- <span data-ttu-id="a8726-131">暗号化されたユーザーストア</span><span class="sxs-lookup"><span data-stu-id="a8726-131">Encrypted user store</span></span>

 <span data-ttu-id="a8726-132">または、独自のものを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8726-132">Or you can build your own.</span></span>

<span data-ttu-id="a8726-133">新しい構成では、複数レベルの階層にグループ化できる名前と値のペアの一覧を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8726-133">The new configuration allows a list of name-value pairs that can be grouped into a multi-level hierarchy.</span></span> <span data-ttu-id="a8726-134">格納されている値は文字列にマップされます。また、設定をカスタムの plain old CLR object (POCO) オブジェクトに逆シリアル化できる組み込みのバインディングがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a8726-134">Any stored value maps to a string, and there's built-in binding support that allows you to deserialize settings into a custom plain old CLR object (POCO) object.</span></span>

<span data-ttu-id="a8726-135"><xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>オブジェクトを使用すると、優先順位ルールを使用して優先順位を解決することで、アプリケーションに必要な構成プロバイダーをいくつでも追加できます。</span><span class="sxs-lookup"><span data-stu-id="a8726-135">The <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder> object lets you add as many configuration providers you may need for your application, using a precedence rule to resolve preference.</span></span> <span data-ttu-id="a8726-136">そのため、コードに最後に追加したプロバイダーが他のプロバイダーよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="a8726-136">So, the last provider you add in your code will override the others.</span></span> <span data-ttu-id="a8726-137">これは、開発、テスト、および運用環境用にさまざまな構成を定義し、コード内の1つの関数でそれらを管理できるため、さまざまな実行環境を管理するための優れた機能です。</span><span class="sxs-lookup"><span data-stu-id="a8726-137">This is a great feature for managing different environments for execution since you can define different configurations for development, testing and production environments, and manage them on a single function inside your code.</span></span>

### <a name="migrating-configuration-files"></a><span data-ttu-id="a8726-138">構成ファイルの移行</span><span class="sxs-lookup"><span data-stu-id="a8726-138">Migrating Configuration files</span></span>

<span data-ttu-id="a8726-139">既存の app.config XML ファイルを引き続き使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a8726-139">You can continue to use your existing app.config XML file.</span></span> <span data-ttu-id="a8726-140">ただし、この機会を利用して構成を移行することで、.NET に加えられたいくつかの拡張機能を活用できます。</span><span class="sxs-lookup"><span data-stu-id="a8726-140">However, you could take this opportunity to migrate your configuration to benefit from the several enhancements made on .NET.</span></span>

<span data-ttu-id="a8726-141">旧形式の *app.config* から新しい構成ファイルに移行するには、XML 形式と JSON 形式のどちらかを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-141">To migrate from an old-style *app.config* to a new configuration file, you should choose between an XML format and a JSON format.</span></span>

<span data-ttu-id="a8726-142">XML を選択した場合、変換は簡単です。</span><span class="sxs-lookup"><span data-stu-id="a8726-142">If you choose XML, the conversion is straightforward.</span></span> <span data-ttu-id="a8726-143">コンテンツは同じであるため、 *app.config* ファイルを XML で型として保存するだけです。</span><span class="sxs-lookup"><span data-stu-id="a8726-143">Since the content is the same, just save the *app.config* file with XML as type.</span></span> <span data-ttu-id="a8726-144">次に、AppSettings を参照するコードを変更して、クラスを使用し `ConfigurationBuilder` ます。</span><span class="sxs-lookup"><span data-stu-id="a8726-144">Then, change the code that references AppSettings to use the `ConfigurationBuilder` class.</span></span> <span data-ttu-id="a8726-145">この変更は簡単です。</span><span class="sxs-lookup"><span data-stu-id="a8726-145">This change should be easy.</span></span>

<span data-ttu-id="a8726-146">JSON 形式を使用し、手動で移行しない場合は、 [dotnet](https://www.nuget.org/packages/dotnet-config2json/) というツールを .net で使用できます。このツールを使用すると、 *app.config* ファイルを JSON 構成ファイルに変換できます。</span><span class="sxs-lookup"><span data-stu-id="a8726-146">If you want to use a JSON format and you don't want to migrate by hand, there's a tool called [dotnet-config2json](https://www.nuget.org/packages/dotnet-config2json/) available on .NET that can convert an *app.config* file to a JSON configuration file.</span></span>

<span data-ttu-id="a8726-147">また、 *machine.config* ファイルで定義された構成セクションを使用すると、いくつかの問題が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-147">You may also come across some issues when using configuration sections that were defined in the *machine.config* file.</span></span> <span data-ttu-id="a8726-148">たとえば、次のような構成を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="a8726-148">For example, consider the following configuration:</span></span>

```xml
<configuration>
    <system.diagnostics>
        <switches>
            <add name="General" value="4" />
        </switches>
        <trace autoflush="true" indentsize="2">
            <listeners>
                <add name="myListener"
                     type="System.Diagnostics.TextWriterTraceListener,
                           System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
                     initializeData="MyListener.log"
                     traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />
            </listeners>
        </trace>
    </system.diagnostics>
</configuration>
```

<span data-ttu-id="a8726-149">この構成を .NET に対して行うと、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="a8726-149">If you take this configuration to a .NET, you'll get an exception:</span></span>

> <span data-ttu-id="a8726-150">認識されない構成セクションシステムです。診断</span><span class="sxs-lookup"><span data-stu-id="a8726-150">Unrecognized configuration section System.Diagnostics</span></span>

<span data-ttu-id="a8726-151">この例外が発生するのは、そのセクションと、そのセクションを処理するアセンブリが、現在は存在しない *machine.config* ファイルで定義されているためです。</span><span class="sxs-lookup"><span data-stu-id="a8726-151">This exception occurs because that section and the assembly responsible for handling that section was defined in the *machine.config* file, which now doesn't exist.</span></span>

<span data-ttu-id="a8726-152">この問題を簡単に解決するには、古い *machine.config* から新しい構成ファイルにセクションの定義をコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8726-152">To easily fix the issue, you can copy the section definition from your old *machine.config* to your new configuration file:</span></span>

```xml
<configSections>
    <section name="system.diagnostics"
             type="System.Diagnostics.SystemDiagnosticsSection,
                   System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
</configSections>
```

## <a name="accessing-databases"></a><span data-ttu-id="a8726-153">データベースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="a8726-153">Accessing databases</span></span>

<span data-ttu-id="a8726-154">ほとんどすべてのデスクトップアプリケーションには、何らかの種類のデータベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="a8726-154">Almost every desktop application needs some kind of database.</span></span> <span data-ttu-id="a8726-155">デスクトップの場合は、デスクトップアプリとデータベースエンジンの間の直接接続を使用して、クライアントサーバーアーキテクチャを検索するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="a8726-155">For desktop, it's common to find client-server architectures with a direct connection between the desktop app and the database engine.</span></span> <span data-ttu-id="a8726-156">これらのデータベースは、異なるユーザー間で情報を共有する必要があるかどうかに応じて、ローカルでもリモートでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="a8726-156">These databases can be local or remote depending on the need to share information between different users.</span></span>

<span data-ttu-id="a8726-157">コードの観点からは、開発者がデータベースに接続し、クエリを実行し、データベースを更新できるようにするためのテクノロジとフレームワークが数多くあります。</span><span class="sxs-lookup"><span data-stu-id="a8726-157">From the code perspective, there have been many technologies and frameworks to give the developer the possibility to connect, query, and update a database.</span></span>

<span data-ttu-id="a8726-158">Windows デスクトップアプリケーションについて説明している最も一般的なデータベースの例として、Microsoft Access と Microsoft SQL Server があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-158">The most common examples of database you can find when talking about Windows Desktop application are Microsoft Access and Microsoft SQL Server.</span></span> <span data-ttu-id="a8726-159">デスクトップに対して20年を超える経験を持っている場合、ODBC、OLEDB、RDO、ADO、ADO.NET、LINQ、Entity Framework などの名前がよく知られています。</span><span class="sxs-lookup"><span data-stu-id="a8726-159">If you have more than 20 years of experience programming for the desktop, names like ODBC, OLEDB, RDO, ADO, ADO.NET, LINQ, and Entity Framework will sound familiar.</span></span>

### <a name="odbc"></a><span data-ttu-id="a8726-160">ODBC</span><span class="sxs-lookup"><span data-stu-id="a8726-160">ODBC</span></span>

<span data-ttu-id="a8726-161">Microsoft が .NET Standard 2.0 と互換性のあるライブラリを提供しているため、.NET で ODBC を使用し続けることができ `System.Data.Odbc` ます。</span><span class="sxs-lookup"><span data-stu-id="a8726-161">You can continue to use ODBC on .NET since Microsoft is providing the `System.Data.Odbc` library compatible with .NET Standard 2.0.</span></span>

### <a name="ole-db"></a><span data-ttu-id="a8726-162">OLE DB</span><span class="sxs-lookup"><span data-stu-id="a8726-162">OLE DB</span></span>

<span data-ttu-id="a8726-163">[OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85)) は、一貫した方法でさまざまなデータソースにアクセスするための優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="a8726-163">[OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85)) has been a great way to access various data sources in a uniform manner.</span></span> <span data-ttu-id="a8726-164">しかし、これは Windows 専用のテクノロジであり、.NET などのクロスプラットフォームテクノロジに最適ではないため、COM に基づいていました。</span><span class="sxs-lookup"><span data-stu-id="a8726-164">But it was based on COM, which is a Windows-only technology, and as such wasn't the best fit for a cross-platform technology such as .NET.</span></span> <span data-ttu-id="a8726-165">SQL Server バージョン2014以降でもサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a8726-165">It's also unsupported in SQL Server versions 2014 and later.</span></span> <span data-ttu-id="a8726-166">このような理由から、OLE DB は .NET ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="a8726-166">For those reasons, OLE DB won't be supported by .NET.</span></span>

### <a name="adonet"></a><span data-ttu-id="a8726-167">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8726-167">ADO.NET</span></span>

<span data-ttu-id="a8726-168">.NET の既存のデスクトップコードから ADO.NET を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8726-168">You can still use ADO.NET from your existing desktop code on .NET.</span></span> <span data-ttu-id="a8726-169">一部の NuGet パッケージのみを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-169">You just need to update some NuGet packages.</span></span>

### <a name="ef-core-vs-ef6"></a><span data-ttu-id="a8726-170">EF Core と EF6</span><span class="sxs-lookup"><span data-stu-id="a8726-170">EF Core vs. EF6</span></span>

<span data-ttu-id="a8726-171">現在サポートされているバージョンの Entity Framework (EF)、Entity Framework 6 (EF6)、および EF Core が2つあります。</span><span class="sxs-lookup"><span data-stu-id="a8726-171">There are two currently supported versions of Entity Framework (EF), Entity Framework 6 (EF6) and EF Core.</span></span>

<span data-ttu-id="a8726-172">.NET Framework 世界の一部としてリリースされた最新のテクノロジは Entity Framework であり、6.4 は最新バージョンです。</span><span class="sxs-lookup"><span data-stu-id="a8726-172">The latest technology released as part of the .NET Framework world is Entity Framework, with 6.4 being the latest version.</span></span> <span data-ttu-id="a8726-173">.NET Core を起動すると、Microsoft は Entity Framework に基づいて新しいデータアクセススタックをリリースし、Entity Framework Core と呼ばれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a8726-173">With the launch of .NET Core, Microsoft also released a new data access stack based on Entity Framework and called Entity Framework Core.</span></span>

<span data-ttu-id="a8726-174">EF 6.4 と EF Core .NET Framework と .NET の両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8726-174">You can use EF 6.4 and EF Core from both .NET Framework and .NET.</span></span> <span data-ttu-id="a8726-175">そのため、2つの判断に役立つデシジョンドライバーは何ですか。</span><span class="sxs-lookup"><span data-stu-id="a8726-175">So, what are the decision drivers to help to decide between the two?</span></span>

<span data-ttu-id="a8726-176">EF 6.3 は、.NET で実行できる EF6 の最初のバージョンであり、クロスプラットフォームで動作します。</span><span class="sxs-lookup"><span data-stu-id="a8726-176">EF 6.3 is the first version of EF6 that can run on .NET and work cross-platform.</span></span> <span data-ttu-id="a8726-177">実際、このリリースの主な目的は、EF6 を使用する既存のアプリケーションを .NET に簡単に移行できるようにすることでした。</span><span class="sxs-lookup"><span data-stu-id="a8726-177">In fact, the main goal of this release was to make it easier to migrate existing applications that use EF6 to .NET.</span></span>

<span data-ttu-id="a8726-178">EF Core は EF6 のような開発者エクスペリエンスを提供するように設計されました。</span><span class="sxs-lookup"><span data-stu-id="a8726-178">EF Core was designed to provide a developer experience similar to EF6.</span></span> <span data-ttu-id="a8726-179">最上位レベルの API のほとんどは同じままなので、EF6 を使用していた開発者にとって EF Core は使い慣れたものと感じるでしょう。</span><span class="sxs-lookup"><span data-stu-id="a8726-179">Most of the top-level APIs remain the same, so EF Core will feel familiar to developers who have used EF6.</span></span>

<span data-ttu-id="a8726-180">互換性がありますが、決定を行う前に、確認する必要がある実装に違いがあります。</span><span class="sxs-lookup"><span data-stu-id="a8726-180">Although compatible, there are differences on the implementation you should check before making a decision.</span></span>
<span data-ttu-id="a8726-181">詳細については、「 [Compare EF Core & EF6](/ef/efcore-and-ef6/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8726-181">For more information, see [Compare EF Core & EF6](/ef/efcore-and-ef6/).</span></span>

<span data-ttu-id="a8726-182">次の場合に EF Core を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a8726-182">The recommendation is to use EF Core if:</span></span>

* <span data-ttu-id="a8726-183">アプリには .NET の機能が必要です。</span><span class="sxs-lookup"><span data-stu-id="a8726-183">The app needs the capabilities of .NET.</span></span>
* <span data-ttu-id="a8726-184">EF Core では、そのアプリに必要な機能がすべてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a8726-184">EF Core supports all of the features that the app requires.</span></span>

<span data-ttu-id="a8726-185">次の条件の両方に該当する場合、EF 6 の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a8726-185">Consider using EF6 if both of the following conditions are true:</span></span>

* <span data-ttu-id="a8726-186">アプリは Windows で実行され、4.0 以降 .NET Framework ます。</span><span class="sxs-lookup"><span data-stu-id="a8726-186">The app will run on Windows and .NET Framework 4.0 or later.</span></span>
* <span data-ttu-id="a8726-187">EF6 では、そのアプリに必要な機能がすべてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a8726-187">EF6 supports all of the features that the app requires.</span></span>

### <a name="relational-databases"></a><span data-ttu-id="a8726-188">リレーショナル データベース</span><span class="sxs-lookup"><span data-stu-id="a8726-188">Relational databases</span></span>

#### <a name="sql-server"></a><span data-ttu-id="a8726-189">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a8726-189">SQL Server</span></span>

<span data-ttu-id="a8726-190">SQL Server は、何年も前にデスクトップ向けに開発していた場合に、選択したデータベースの1つになりました。</span><span class="sxs-lookup"><span data-stu-id="a8726-190">SQL Server has been one of the databases of choice if you were developing for the desktop some years ago.</span></span> <span data-ttu-id="a8726-191">.NET Framework でを使用すると、 <xref:System.Data.SqlClient> データベース固有のプロトコルをカプセル化した SQL Server のバージョンにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a8726-191">With the use of <xref:System.Data.SqlClient> in .NET Framework, you could access versions of SQL Server, which encapsulates database-specific protocols.</span></span>

<span data-ttu-id="a8726-192">.NET では、.NET Framework に存在する `SqlClient` がライブラリ内に存在するものと完全に互換性のある新しいクラスを見つけることができ <xref:Microsoft.Data.SqlClient> ます。</span><span class="sxs-lookup"><span data-stu-id="a8726-192">In .NET, you can find a new `SqlClient` class, fully compatible with the one existing in the .NET Framework but located in the <xref:Microsoft.Data.SqlClient> library.</span></span> <span data-ttu-id="a8726-193">ここでは、 [Microsoft. Data. SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) NuGet パッケージへの参照を追加し、名前空間の名前を変更して、すべてを想定どおりに動作させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-193">You just have to add a reference to the [Microsoft.Data.SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) NuGet package and do some renaming for the namespaces and everything should work as expected.</span></span>

#### <a name="microsoft-access"></a><span data-ttu-id="a8726-194">Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="a8726-194">Microsoft Access</span></span>

<span data-ttu-id="a8726-195">Microsoft Access は、高度でスケーラブルな SQL Server が不要になったときに、何年も使用されています。</span><span class="sxs-lookup"><span data-stu-id="a8726-195">Microsoft Access has been used for years when the sophisticated and more scalable SQL Server wasn't needed.</span></span> <span data-ttu-id="a8726-196">ライブラリを使用して Microsoft Access に接続することもでき <xref:System.Data.Odbc> ます。</span><span class="sxs-lookup"><span data-stu-id="a8726-196">You can still connect to Microsoft Access using the <xref:System.Data.Odbc> library.</span></span>

## <a name="consuming-services"></a><span data-ttu-id="a8726-197">サービスの利用</span><span class="sxs-lookup"><span data-stu-id="a8726-197">Consuming services</span></span>

<span data-ttu-id="a8726-198">サービス指向アーキテクチャの導入により、デスクトップアプリケーションは、クライアント/サーバーモデルから3層アプローチへの進化を開始しました。</span><span class="sxs-lookup"><span data-stu-id="a8726-198">With the raise of service-oriented architectures, desktop applications began to evolve from a client-server model to the three-layer approach.</span></span> <span data-ttu-id="a8726-199">クライアントとサーバーの間のアプローチでは、通常は1つの EXE ファイル内にビジネスロジックを保持するクライアントから直接データベース接続が確立されます。</span><span class="sxs-lookup"><span data-stu-id="a8726-199">In the client-server approach, a direct database connection is established from the client holding the business logic usually inside a single EXE file.</span></span> <span data-ttu-id="a8726-200">一方、3層アプローチは、ビジネスロジックとデータベースアクセスを実装する中間サービスレイヤーを確立して、セキュリティ、スケーラビリティ、および再利用性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="a8726-200">On the other hand, the three-layer approach establishes an intermediate service layer implementing business logic and database access allowing for better security, scalability, and reusability.</span></span> <span data-ttu-id="a8726-201">レイヤーアプローチは、データのデータセットを直接操作するのではなく、データ転送を実装する手段として、コントラクトと型オブジェクトを実装する一連のサービスに依存します。</span><span class="sxs-lookup"><span data-stu-id="a8726-201">Instead of working directly with datasets of data, the layer approach relies in a set of services implementing contracts and types objects as a way to implement data transfer.</span></span>

<span data-ttu-id="a8726-202">WCF サービスを使用しているデスクトップアプリケーションがあり、それを .NET に移行する場合は、いくつかの点を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-202">If you have a desktop application using a WCF service and you want to migrate it to .NET, there are some things to consider.</span></span>

<span data-ttu-id="a8726-203">まず、サービスにアクセスするための構成を解決する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a8726-203">The first thing is how to resolve the configuration to access the service.</span></span> <span data-ttu-id="a8726-204">構成は .NET では異なるため、構成ファイルでいくつかの更新を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-204">Because the configuration is different on .NET, you'll need to make some updates in your configuration file.</span></span>

<span data-ttu-id="a8726-205">次に、Visual Studio 2019 に存在する新しいツールを使用してサービスクライアントを再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-205">Second, you'll need to regenerate the service client with the new tools present on Visual Studio 2019.</span></span> <span data-ttu-id="a8726-206">この手順では、同期操作の生成をアクティブ化して、クライアントが既存のコードと互換性を持つようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-206">In this step, you must consider activating the generation of the synchronous operations to make the client compatible with your existing code.</span></span>

<span data-ttu-id="a8726-207">移行後に、.NET 上に存在しないライブラリがあることがわかった場合は、 [Microsoft の互換性](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) に関する NuGet パッケージへの参照を追加し、不足している関数があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="a8726-207">After the migration, if you find that there are libraries you need that aren't present on .NET, you can add a reference to the [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) NuGet package and see if the missing functions are there.</span></span>

<span data-ttu-id="a8726-208">クラスを使用して web サービス呼び出しを実行している場合は <xref:System.Net.WebRequest> 、.net にいくつかの違いがある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-208">If you're using the <xref:System.Net.WebRequest> class to perform web service calls, you may find some differences on .NET.</span></span> <span data-ttu-id="a8726-209">代わりに、システムの .Net. HttpClient を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a8726-209">The recommendation is to use the System.Net.Http.HttpClient instead.</span></span>

## <a name="consuming-a-com-object"></a><span data-ttu-id="a8726-210">COM オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="a8726-210">Consuming a COM Object</span></span>

<span data-ttu-id="a8726-211">現時点では、.NET で使用するために、Visual Studio 2019 から COM オブジェクトへの参照を追加する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="a8726-211">Currently, there's no way to add a reference to a COM object from Visual Studio 2019 to use with .NET.</span></span> <span data-ttu-id="a8726-212">そのため、プロジェクトファイルを手動で変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-212">So, you have to manually modify the project file.</span></span>

<span data-ttu-id="a8726-213">次の `COMReference` 例のように、プロジェクトファイル内に構造体を挿入します。</span><span class="sxs-lookup"><span data-stu-id="a8726-213">Insert a `COMReference` structure inside the project file like in the following example:</span></span>

```xml
<ItemGroup>
    <COMReference Include="MSHTML">
        <Guid>{3050F1C5-98B5-11CF-BB82-00AA00BDCE0B}\</Guid>
        <VersionMajor>4</VersionMajor>
        <VersionMinor>0</VersionMinor>
        <Lcid>0</Lcid>
        <WrapperTool>primary</WrapperTool>
        <Isolated>false</Isolated>
    </COMReference>
</ItemGroup>
```

## <a name="more-things-to-consider"></a><span data-ttu-id="a8726-214">その他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="a8726-214">More things to consider</span></span>

<span data-ttu-id="a8726-215">.NET Framework ライブラリで利用できるいくつかのテクノロジは、.NET Core または .NET 5 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="a8726-215">Several technologies available to .NET Framework libraries aren't available for .NET Core or .NET 5.</span></span> <span data-ttu-id="a8726-216">コードがこれらのテクノロジの一部に依存している場合は、このセクションで説明する別の方法を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a8726-216">If your code relies on some of these technologies, consider the alternative approaches outlined in this section.</span></span>

<span data-ttu-id="a8726-217">[Windows 互換機能パック](../../core/porting/windows-compat-pack.md)は、以前に .NET Framework でのみ使用できる api へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="a8726-217">The [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md) provides access to APIs that were previously available only for .NET Framework.</span></span> <span data-ttu-id="a8726-218">.NET Core と .NET Standard のプロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8726-218">It can be used on .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="a8726-219">API の互換性の詳細については、「」の互換性に影響する変更点と非推奨の Api に関するドキュメントを参照して <https://docs.microsoft.com/dotnet/core/compatibility/fx-core> ください。</span><span class="sxs-lookup"><span data-stu-id="a8726-219">For more information on API compatibility, you can find documentation about breaking changes and deprecated/legacy APIs at <https://docs.microsoft.com/dotnet/core/compatibility/fx-core>.</span></span>

### <a name="appdomains"></a><span data-ttu-id="a8726-220">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a8726-220">AppDomains</span></span>

<span data-ttu-id="a8726-221">アプリケーション ドメイン (AppDomains) はアプリを互いに分離します。</span><span class="sxs-lookup"><span data-stu-id="a8726-221">Application domains (AppDomains) isolate apps from one another.</span></span> <span data-ttu-id="a8726-222">AppDomains ではランタイムサポートが必要であり、コストが高くなります。</span><span class="sxs-lookup"><span data-stu-id="a8726-222">AppDomains require runtime support and are expensive.</span></span> <span data-ttu-id="a8726-223">追加のアプリドメインの作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a8726-223">Creating additional app domains isn't supported.</span></span> <span data-ttu-id="a8726-224">コードの分離には、代わりの方法として、プロセスの分離やコンテナーの利用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a8726-224">For code isolation, we recommend separate processes or using containers as an alternative.</span></span> <span data-ttu-id="a8726-225">アセンブリの動的読み込みには、新しい <xref:System.Runtime.Loader.AssemblyLoadContext> クラスをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a8726-225">For the dynamic loading of assemblies, we recommend the new <xref:System.Runtime.Loader.AssemblyLoadContext> class.</span></span>

<span data-ttu-id="a8726-226">コードを .NET Framework から簡単に移行できるように、.NET では API サーフェイスの一部を公開して `AppDomain` います。</span><span class="sxs-lookup"><span data-stu-id="a8726-226">To make code migration from .NET Framework easier, .NET exposes some of the `AppDomain` API surface.</span></span> <span data-ttu-id="a8726-227">API の中には、正常に機能するもの (<xref:System.AppDomain.UnhandledException?displayProperty=nameWithType> など)、処理を行わないメンバー (<xref:System.AppDomain.SetCachePath%2A> など)、<xref:System.PlatformNotSupportedException> をスローするもの (<xref:System.AppDomain.CreateDomain%2A> など) があります。</span><span class="sxs-lookup"><span data-stu-id="a8726-227">Some of the APIs function normally (for example, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), some members do nothing (for example, <xref:System.AppDomain.SetCachePath%2A>), and some of them throw <xref:System.PlatformNotSupportedException> (for example, <xref:System.AppDomain.CreateDomain%2A>).</span></span>

### <a name="remoting"></a><span data-ttu-id="a8726-228">リモート処理</span><span class="sxs-lookup"><span data-stu-id="a8726-228">Remoting</span></span>

<span data-ttu-id="a8726-229">.NET リモート処理は、サポートされなくなった AppDomain 間通信に使用されました。</span><span class="sxs-lookup"><span data-stu-id="a8726-229">.NET Remoting was used for cross-AppDomain communication, which is no longer supported.</span></span> <span data-ttu-id="a8726-230">また、リモート処理にはランタイム サポートが必要で、維持するのに高いコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="a8726-230">Also, Remoting requires runtime support, which is expensive to maintain.</span></span> <span data-ttu-id="a8726-231">このような理由から、.net では .NET リモート処理がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a8726-231">For these reasons, .NET Remoting isn't supported on .NET.</span></span>

<span data-ttu-id="a8726-232">プロセス間の通信については、またはクラスなど、リモート処理の代わりにプロセス間通信 (IPC) メカニズムを検討する必要があり <xref:System.IO.Pipes?displayProperty=nameWithType> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> ます。</span><span class="sxs-lookup"><span data-stu-id="a8726-232">For communication across processes, you should consider inter-process communication (IPC) mechanisms as an alternative to Remoting, such as the <xref:System.IO.Pipes?displayProperty=nameWithType> or the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> class.</span></span>

<span data-ttu-id="a8726-233">マシン間では、代替方法としてネットワーク ベースのソリューションを使用してください。</span><span class="sxs-lookup"><span data-stu-id="a8726-233">Across machines, use a network-based solution as an alternative.</span></span> <span data-ttu-id="a8726-234">できれば、HTTP など、オーバーヘッドの少ないプレーンテキストプロトコルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a8726-234">Preferably, use a low-overhead plaintext protocol, such as HTTP.</span></span> <span data-ttu-id="a8726-235">この場合、ASP.NET Core で使用される Web サーバーの Kestrel Web Server も選択できます。</span><span class="sxs-lookup"><span data-stu-id="a8726-235">The Kestrel web server, the web server used by ASP.NET Core, is an option here.</span></span>

### <a name="code-access-security-cas"></a><span data-ttu-id="a8726-236">コード アクセス セキュリティ (CAS)</span><span class="sxs-lookup"><span data-stu-id="a8726-236">Code Access Security (CAS)</span></span>

<span data-ttu-id="a8726-237">サンドボックスは、ランタイムまたはフレームワークに依存して、マネージアプリケーションまたはライブラリが使用または実行するリソースを制限します。 .NET ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a8726-237">Sandboxing, which relies on the runtime or the framework to constrain which resources a managed application or library uses or runs, isn't supported on .NET.</span></span>

<span data-ttu-id="a8726-238">オペレーティングシステムによって提供されるセキュリティ境界 (仮想化、コンテナー、ユーザーアカウントなど) を使用して、最小限の特権セットでプロセスを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8726-238">Use security boundaries that are provided by the operating system, such as virtualization, containers, or user accounts for running processes with the minimum set of privileges.</span></span>

### <a name="security-transparency"></a><span data-ttu-id="a8726-239">セキュリティ透過性</span><span class="sxs-lookup"><span data-stu-id="a8726-239">Security Transparency</span></span>

<span data-ttu-id="a8726-240">CAS と同様に、セキュリティ透過性はサンドボックス コードをセキュリティ クリティカルなコードから宣言的に分離しますが、現在はセキュリティ境界としてはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a8726-240">Similar to CAS, Security Transparency separates sandboxed code from security critical code in a declarative fashion but is no longer supported as a security boundary.</span></span>

<span data-ttu-id="a8726-241">仮想化、コンテナー、ユーザーアカウントなど、オペレーティングシステムによって提供されるセキュリティ境界を使用して、最小限の特権を持つプロセスを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8726-241">Use security boundaries that are provided by the operating system, such as virtualization, containers, or user accounts for running processes with the least set of privileges.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a8726-242">[前へ](whats-new-dotnet.md )
>[次へ](windows-migration.md)</span><span class="sxs-lookup"><span data-stu-id="a8726-242">[Previous](whats-new-dotnet.md )
[Next](windows-migration.md)</span></span>
