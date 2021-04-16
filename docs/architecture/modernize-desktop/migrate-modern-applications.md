---
title: モダン デスクトップ アプリケーションの移行
description: モダン デスクトップ アプリケーションの移行プロセスについて理解しておく必要があるすべての情報。
ms.date: 01/19/2021
ms.openlocfilehash: b5bea6e601dc040adfd8ed410320a3416cb3372e
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "98615764"
---
# <a name="migrating-modern-desktop-applications"></a>モダン デスクトップ アプリケーションの移行

この章では、既存のアプリケーションを .NET Framework から .NET に移行する際に直面する可能性がある、最も一般的な問題と課題について説明します。

複雑なデスクトップ アプリケーションは、独立しては動作せず、ローカル コンピューターまたはリモート サーバー上に存在する可能性があるサブシステムとの対話を必要とします。 多くの場合、永続化ストレージとして何らかの種類のデータベースにローカルまたはリモートで接続することが必要になります。 インターネットとサービス指向アーキテクチャの台頭により、リモート サーバーまたはクラウドに存在する何らかのサービスにアプリケーションを接続することは一般的になりました。 一部の機能を実装するために、コンピューターのファイル システムへのアクセスが必要になる場合があります。 または、アプリケーションの外部にある COM オブジェクト内に存在する機能を使用している場合もあります。これはたとえば、アプリに Office アセンブリを統合している場合によくあるシナリオです。

また、.NET Framework と .NET によって公開される API サーフェイスには違いがあり、.NET Framework で利用できる一部の機能は .NET では使用できません。 そのため、移行を計画する際には、それらを把握して考慮することが重要です。

## <a name="configuration-files"></a>構成ファイル

構成ファイルを利用すると、実行時に読み取られアプリケーションの動作に影響を与える、一連のプロパティを格納できます。たとえば、データベースを配置する場所や、ループを実行する回数などです。 この手法の利点は、コードの書き直しや再コンパイルを行わずに、アプリケーションの一部の側面を変更できることです。 これは、たとえば、特定の構成値のセットを持つ開発環境と、別の構成値を持つ運用環境で、同じアプリコードが実行される場合に便利です。

### <a name="configuration-on-net-framework"></a>.NET Framework での構成

動作している .NET Framework デスクトップ アプリケーションがある場合、`System.Configuration` 名前空間から <xref:System.Configuration.AppSettingsSection> クラスを介して *app.config* ファイルがアクセスされる可能性があります。

.NET Framework インフラストラクチャ内には、親からプロパティを継承する構成ファイルの階層があります。 *machine.config* というファイルには、子孫構成ファイルで使用またはオーバーライドできる、多くのプロパティと構成セクションが定義されています。

### <a name="configuration-on-net"></a>.NET での構成

.NET の世界に *machine.config* ファイルはありません。 また、旧式の <xref:System.Configuration> 名前空間を使用し続けることもできますが、多くの拡張機能を備えたモダンな <xref:Microsoft.Extensions.Configuration> に切り替えることを検討してください。

構成 API では、構成プロバイダーの概念がサポートされます。構成プロバイダーでは、構成の読み込みに使用されるデータ ソースを定義します。 組み込みプロバイダーには、次のような種類があります。

- メモリ内 .NET オブジェクト
- INI ファイル
- JSON ファイル
- XML ファイル
- コマンド ライン引数
- 環境変数
- 暗号化されたユーザー ストア

 ユーザー独自のものも作成できます。

新しい構成では、複数レベルの階層にグループ化できる名前と値のペアの一覧を使用できます。 格納されている値は文字列にマップされます。また、設定をカスタムの単純な従来の CLR オブジェクト (POCO) に逆シリアル化できる、組み込みのバインディング サポートがあります。

<xref:Microsoft.Extensions.Configuration.ConfigurationBuilder> オブジェクトを使用すると、アプリケーションに必要な構成プロバイダーをいくつでも追加できます。優先順位の解決には優先順位ルールが使用されます。 そのため、コードに最後に追加したプロバイダーが他のプロバイダーよりも優先されます。 これは、開発、テスト、および運用環境用に異なる構成を定義し、コード内の 1 つの関数でそれらを管理できるため、さまざまな実行環境を管理するための優れた機能です。

### <a name="migrating-configuration-files"></a>構成ファイルの移行

既存の app.config XML ファイルを引き続き使用することができます。 ただし、この機会を利用して構成を移行することで、.NET に加えられたいくつかの機能強化を活用できます。

旧形式の *app.config* から新しい構成ファイルに移行するには、XML 形式と JSON 形式のどちらかを選択する必要があります。

XML を選択した場合、変換は簡単です。 内容は同じであるため、*app.config* ファイルを XML 形式として保存するだけです。 次に、AppSettings を参照するコードを変更して、`ConfigurationBuilder` クラスを使用するようにします。 この変更は簡単なはずです。

JSON 形式を使用する場合で、手作業での移行を望まないときは、.NET で使用できる [dotnet-config2json](https://www.nuget.org/packages/dotnet-config2json/) というツールで、*app.config* ファイルを JSON 構成ファイルに変換できます。

また、*machine.config* ファイルに定義されていた構成セクションを使用する際に、いくつかの問題が発生する場合があります。 たとえば、次のような構成があるとします。

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

この構成を .NET に移行すると、次の例外が発生します。

> 構成セクション System.Diagnostics を認識できません

この例外が発生するのは、そのセクションと、そのセクションを処理するアセンブリが、現在は存在しない *machine.config* ファイルで定義されていたためです。

この問題を簡単に解決するには、古い *machine.config* から新しい構成ファイルにセクションの定義をコピーします。

```xml
<configSections>
    <section name="system.diagnostics"
             type="System.Diagnostics.SystemDiagnosticsSection,
                   System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
</configSections>
```

## <a name="accessing-databases"></a>データベースへのアクセス

ほとんどすべてのデスクトップ アプリケーションには、何らかの種類のデータベースが必要です。 デスクトップの場合は、クライアント/サーバー アーキテクチャでデスクトップ アプリとデータベース エンジンの間の直接接続を使用することがよくあります。 これらのデータベースは、異なるユーザー間で情報を共有する必要があるかどうかに応じて、ローカルまたはリモートになります。

コードの観点からは、開発者がデータベースに接続し、クエリを実行し、データベースを更新できるようにするためのテクノロジとフレームワークが数多くあります。

Windows デスクトップ アプリケーション関連では、最も一般的なデータベースの例として、Microsoft Access と Microsoft SQL Server があります。 デスクトップのプログラミングで 20 年を超える経験を持っているなら、ODBC、OLEDB、RDO、ADO、ADO.NET、LINQ、Entity Framework などの名前に馴染みがあるでしょう。

### <a name="odbc"></a>ODBC

Microsoft から .NET Standard 2.0 と互換性のある `System.Data.Odbc` ライブラリが提供されているため、ODBC を .NET で使用し続けることができます。

### <a name="ole-db"></a>OLE DB (OLE DB)

[OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85)) は、一貫した方法でさまざまなデータ ソースにアクセスするための優れた方法です。 しかし、Windows 専用のテクノロジである COM に基づいているため、.NET などのクロスプラットフォーム テクノロジには最適ではありませんでした。 また、SQL Server バージョン 2014 以降ではサポートされていません。 このような理由から、OLE DB は .NET ではサポートされません。

### <a name="adonet"></a>ADO.NET

既存のデスクトップ コードから ADO.NET を .NET で引き続き使用できます。 必要なのは、一部の NuGet パッケージを更新することだけです。

### <a name="ef-core-vs-ef6"></a>EF Core と EF6 の比較

Entity Framework (EF)、Entity Framework 6 (EF6)、および EF Core には、現在サポートされているバージョンが 2 つあります。

.NET Framework 世界の一部としてリリースされた最新のテクノロジは Entity Framework であり、最新バージョンは 6.4 です。 .NET Core の投入と共に、Microsoft では Entity Framework に基づく新しいデータ アクセス スタックもリリースしました。これは Entity Framework Core と呼ばれます。

.NET Framework と .NET の両方の EF 6.4 と EF Core を使用できます。 それでは、2 つのうちどちらを選ぶかの決め手は何でしょうか。

EF 6.3 は、.NET で実行できる EF6 の最初のバージョンであり、クロスプラットフォームで動作します。 実際、このリリースの主な目的は、EF6 を使用する既存のアプリケーションを .NET に簡単に移行できるようにすることでした。

EF Core は EF6 のような開発者エクスペリエンスを提供するように設計されました。 最上位レベルの API のほとんどは同じままなので、EF6 を使用していた開発者にとって EF Core は使い慣れたものと感じるでしょう。

互換性はありますが、実装には違いがあり、決定を行う前に確認する必要があります。
詳細については、「[EF Core と EF6 を比較する](/ef/efcore-and-ef6/)」を参照してください。

次の場合には EF Core を使用することをお勧めします。

* アプリでは .NET の機能が必要とされています。
* EF Core では、そのアプリに必要な機能がすべてサポートされています。

次の条件の両方に該当する場合、EF 6 の使用を検討してください。

* アプリは Windows と .NET Framework 4.0 以降で実行されます。
* EF6 では、そのアプリに必要な機能がすべてサポートされています。

### <a name="relational-databases"></a>リレーショナル データベース

#### <a name="sql-server"></a>SQL Server

何年か前のデスクトップ向けの開発では、SQL Server は選ばれるデータベースの 1 つでした。 .NET Framework では <xref:System.Data.SqlClient> を使用して SQL Server のバージョンにアクセスできました。これには、データベース固有のプロトコルがカプセル化されています。

.NET には新しい `SqlClient` クラスがあります。これは、.NET Framework に既存のものと完全に互換性がありますが、<xref:Microsoft.Data.SqlClient> ライブラリ内にあります。 [Microsoft.Data.SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) NuGet パッケージへの参照を追加し、名前空間の名前をいくらか変更するだけで、すべてが想定どおりに動作するはずです。

#### <a name="microsoft-access"></a>Microsoft Access

Microsoft Access は、より高度でスケーラブルな SQL Server が必要でなかった間、何年も使用されてきました。 Microsoft Access には <xref:System.Data.Odbc> ライブラリを使用して引き続き接続できます。

## <a name="consuming-services"></a>サービスの利用

サービス指向アーキテクチャの台頭により、デスクトップ アプリケーションは、クライアント/サーバー モデルから 3 層アプローチへ進化し始めました。 クライアント/サーバー型のアプローチでは、通常は 1 つの EXE ファイル内にビジネス ロジックを保持しているクライアントから直接データベース接続が確立されます。 一方、3 層アプローチでは、ビジネス ロジックとデータベース アクセスを実装している中間のサービス層が確立され、セキュリティ、スケーラビリティ、および再利用性が向上します。 3 層アプローチは、データのデータセットを直接操作するのではなく、データ転送を実装する手段として、コントラクトと型オブジェクトを実装する一連のサービスに依存します。

WCF サービスを使用しているデスクトップ アプリケーションがあり、それを .NET に移行する場合は、いくつかの点を考慮する必要があります。

まず、サービスにアクセスするために構成を解決する方法です。 構成は .NET では異なるため、構成ファイルにいくつかの変更を加える必要があります。

次に、Visual Studio 2019 に存在する新しいツールを使用してサービス クライアントを再生成する必要があります。 この手順では、同期操作の生成をアクティブ化して、クライアントが既存のコードと互換性を持つようにする必要があります。

移行後に、必要なライブラリが .NET 上にないことがわかった場合は、[Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) NuGet パッケージへの参照を追加し、不足している関数があるかどうかを確認します。

<xref:System.Net.WebRequest> クラスを使用して Web サービス呼び出しを実行している場合は、.NET ではいくつかの違いに気付くことがあります。 代わりに、System.Net.Http.HttpClient を使用することをお勧めします。

## <a name="consuming-a-com-object"></a>COM オブジェクトの使用

現時点では、.NET で使用するために、Visual Studio 2019 から COM オブジェクトへの参照を追加する方法はありません。 そのため、プロジェクト ファイルを手動で変更する必要があります。

次の例のように、プロジェクト ファイル内に `COMReference` 構造体を挿入します。

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

## <a name="more-things-to-consider"></a>その他の考慮事項

.NET Framework ライブラリで利用できるいくつかのテクノロジは、.NET Core または .NET 5 では使用できません。 コードがこれらのテクノロジの一部に依存している場合は、このセクションで説明する別の方法を検討してください。

[Windows 互換機能パック](../../core/porting/windows-compat-pack.md)を使用すると、以前は .NET Framework でのみ使用可能であった API にアクセスできます。 .NET Core と .NET Standard のプロジェクトで使用できます。

API の互換性の詳細については、<https://docs.microsoft.com/dotnet/core/compatibility/fx-core> にある、破壊的変更と非推奨/レガシ API に関するドキュメントを参照してください。

### <a name="appdomains"></a>AppDomain

アプリケーション ドメイン (AppDomains) はアプリを互いに分離します。 AppDomain にはランタイム サポートが必要で、コストがかかります。 追加のアプリ ドメインを作成することはサポートされていません。 コードの分離には、代わりの方法として、プロセスの分離やコンテナーの利用をお勧めします。 アセンブリの動的読み込みには、新しい <xref:System.Runtime.Loader.AssemblyLoadContext> クラスをお勧めします。

.NET Framework からのコードの移行をより簡単にするために、.NET では `AppDomain` API サーフェイスの一部を公開しています。 API の中には、正常に機能するもの (<xref:System.AppDomain.UnhandledException?displayProperty=nameWithType> など)、処理を行わないメンバー (<xref:System.AppDomain.SetCachePath%2A> など)、<xref:System.PlatformNotSupportedException> をスローするもの (<xref:System.AppDomain.CreateDomain%2A> など) があります。

### <a name="remoting"></a>リモート処理

.NET リモート処理は、AppDomain 間の通信で使用されていましたが、サポートされなくなりました。 また、リモート処理にはランタイム サポートが必要で、維持するのに高いコストがかかります。 このような理由から、.NET リモート処理は .NET ではサポートされていません。

プロセス間の通信では、リモート処理に代わる方法として、<xref:System.IO.Pipes?displayProperty=nameWithType> または <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> クラスなどのプロセス間通信 (IPC) メカニズムを検討してください。

マシン間では、代替方法としてネットワーク ベースのソリューションを使用してください。 可能であれば、HTTP などのオーバーヘッドの少ないプレーンテキストのプロトコルを使用してください。 この場合、ASP.NET Core で使用される Web サーバーの Kestrel Web Server も選択できます。

### <a name="code-access-security-cas"></a>コード アクセス セキュリティ (CAS)

サンド ボックスは、マネージド アプリケーションやライブラリが使用または実行するリソースの制限を、ランタイムまたはフレームワークに依存しています。これは .NET Framework ではサポートされていません。

仮想化、コンテナー、ユーザー アカウントなど、オペレーティング システムが提供するセキュリティ境界を使用して、最小限の特権セットでプロセスを実行します。

### <a name="security-transparency"></a>セキュリティ透過性

CAS と同様に、セキュリティ透過性はサンドボックス コードをセキュリティ クリティカルなコードから宣言的に分離しますが、現在はセキュリティ境界としてはサポートされていません。

仮想化、コンテナー、ユーザー アカウントなど、オペレーティング システムが提供するセキュリティ境界を使用して、最低限の特権セットでプロセスを実行します。

>[!div class="step-by-step"]
>[前へ](whats-new-dotnet.md )
>[次へ](windows-migration.md)
