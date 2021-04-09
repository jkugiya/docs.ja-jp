---
title: インターネット インフォメーション サービスでホストされる WCF サービスの配置
description: IIS でホストされる WCF サービスを開発および展開するために必要なタスクについて説明します。これは、コンポーネントのインストールの確認から始まります。
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: a51cf09309a5a5c9ac8c8a4cc4fecc0a203b7b3c
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653479"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>インターネット インフォメーション サービスでホストされる WCF サービスの配置

インターネット インフォメーション サービス (IIS) でホストされる Windows Communication Foundation (WCF) サービスの開発および展開には、次のタスクが含まれます。

- IIS、ASP.NET、WCF、WCF アクティブ化コンポーネントが正しくインストールおよび登録されていることを確認します。

- 新しい IIS アプリケーションを作成するか、既存の ASP.NET アプリケーションを再利用します。

- WCF サービス用の .svc ファイルを作成します。

- IIS アプリケーションにサービス実装を展開します。

- WCF サービスを構成します。

IIS でホストされる WCF サービスの作成に関する詳細なチュートリアルについては、「[方法: IIS で WCF サービスをホストする](how-to-host-a-wcf-service-in-iis.md)」を参照してください。

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>IIS、ASP.NET、および WCF が正しくインストールおよび登録されていることの確認

IIS でホストされる WCF サービスを正常に機能させるには、WCF、IIS、ASP.NET をインストールする必要があります。 WCF (.NET Framework の一部として)、ASP.NET、IIS のインストール手順は、ご使用のオペレーティング システムのバージョンによって異なります。 WCF と .NET Framework のインストールの詳細については、「[開発者向けの .NET Framework のインストール](../../install/guide-for-developers.md)」を参照してください。 Windows 10 に IIS をインストールするには、 **[コントロール パネル]** 内の **[プログラムと機能]** を開き、 **[Windows の機能の有効化または無効化]** を選択します。 **[Windows の機能]** で **[インターネット インフォメーション サービス]** を選択し、 **[OK]** を選択します。

![IIS が強調表示された [Windows の機能]](./media/windows-features-iis.png)

他のオペレーティング システムに IIS をインストールする手順については、「[Windows Vista および Windows 7 に IIS をインストールする](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7)」と「[Windows Server 2012 R2 に IIS 8.5 をインストールする](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2)」を参照してください。

コンピューター上に既に IIS が存在する場合は、.NET Framework のインストール プロセスによって WCF が自動的に IIS に登録されます。 .NET Framework の後に IIS をインストールした場合は、WCF を IIS と ASP.NET に登録するために追加の手順が必要になります。 使用しているオペレーティング システムに応じて、次のように実行します。

- Windows 7 および Windows Server 2003: [ServiceModel 登録ツール (ServiceModelReg.exe)](../servicemodelreg-exe.md) を使用して、WCF を IIS に登録します。 このツールを使用するには、[Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) に `ServiceModelReg.exe /i /x` と入力します。

- Windows 7: 最後に、ASP.NET が .NET Framework バージョン 4 以降を使用するように構成されていることを確認する必要があります。 これを行うには、`–i` オプションを指定して ASPNET_Regiis ツールを実行します。 詳細については、「[ASP.NET IIS 登録ツール](/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90))」を参照してください。

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>新しい IIS アプリケーションの作成、または既存の ASP.NET アプリケーションの再利用

IIS でホストされる WCF サービスは、IIS アプリケーションの内部に存在する必要があります。 WCF サービスのみをホストする新しい IIS アプリケーションを作成できます。 または、既に ASP.NET 2.0 コンテンツ (.aspx ページや ASP.NET Web サービス [ASMX] など) をホストしている既存のアプリケーションに WCF サービスを展開することもできます。 これらのオプションの詳細については、「[WCF サービスと ASP.NET](wcf-services-and-aspnet.md)」の「WCF を ASP.NET とサイドバイサイドでホストする」および「ASP.NET 互換モードでの WCF サービスのホスト」セクションを参照してください。

IIS 6.0 以降のバージョンでは、隔離されているオブジェクト指向プログラミング アプリケーションは定期的に再起動されることに注意してください。 既定値は 1740 分です。 サポートされている最大値は 71,582 分です。 この再起動は、無効にできます。 このプロパティの詳細については、「[PeriodicRestartTime](/previous-versions/iis/6.0-sdk/ms525914(v=vs.90))」を参照してください。

## <a name="create-an-svc-file-for-the-wcf-service"></a>WCF サービス用の .svc ファイルの作成

IIS でホストされる WCF サービスは、IIS アプリケーションの内部で特別なコンテンツ ファイル (.svc ファイル) として表現されます。 これは、ASMX ページが、IIS アプリケーションの内部で .asmx ファイルとして表現されるのと同様です。 .svc ファイルには、WCF ホスティング インフラストラクチャで、ホストされているサービスを受信メッセージに応えてアクティブ化できるようにする、WCF 固有の処理ディレクティブ ([\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md)) が含まれます。 .svc ファイルの最も一般的な構文を次のステートメントに示します。

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

これは [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) ディレクティブと 1 つの属性 `Service` で構成されます。 `Service` 属性の値は、サービス実装の共通言語ランタイム (CLR: Common Language Runtime) 型名です。 このディレクティブを使用することは、次のコードを使用してサービス ホストを作成することと基本的に同じです。

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

サービスのベース アドレスの一覧を作成するなど、追加のホスト構成を実行することもできます。 カスタム <xref:System.ServiceModel.Activation.ServiceHostFactory> を使用して、このディレクティブをカスタム ホスト ソリューション用に拡張することもできます。 WCF サービスをホストする IIS アプリケーションには、<xref:System.ServiceModel.ServiceHost> インスタンスの作成と有効期間を管理する責任はありません。 マネージド WCF ホスティング インフラストラクチャは、.svc ファイルに対する最初の要求を受け取ったときに、必要な <xref:System.ServiceModel.ServiceHost> インスタンスを動的に作成します。 このインスタンスは、コードによって明示的に閉じられるか、アプリケーションがリサイクルされるときまで解放されません。

.svc ファイルの構文の詳細については、「[\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md)」を参照してください。

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>IIS アプリケーションへのサービス実装の展開

IIS でホストされる WCF サービスでは、ASP.NET 2.0 と同一の動的なコンパイル モデルが使用されます。 ASP.NET の場合と同様に、IIS でホストされる WCF サービスの実装コードは、次のようにさまざまな方法でさまざまな場所に展開できます。

- グローバル アセンブリ キャッシュ (GAC: Global Assembly Cache) またはアプリケーションの \bin ディレクトリに配置される、プリコンパイルされた .dll ファイルとして展開します。 プリコンパイルされたバイナリは、新しいバージョンのクラス ライブラリが展開されるまで更新されません。

- アプリケーションの \App_Code ディレクトリ内に配置された、コンパイルされていないソース ファイルとして。 このディレクトリに配置されたソース ファイルは、アプリケーションの最初の要求を処理するときに動的に要求されます。 \App_Code ディレクトリ内のファイルを変更すると、次の要求を受け取ったときにアプリケーション全体がリサイクルされ、再コンパイルされます。

- .svc ファイル内に直接配置された、コンパイルされていないコードとして。 実装コードは、サービスの .svc ファイル内の \@ServiceHost ディレクティブの後にインラインで配置することもできます。 インライン コードを変更すると、次の要求を受け取ったときにアプリケーションがリサイクルされ、再コンパイルされます。

ASP.NET 2.0 のコンパイル モデルの詳細については、「[ASP.NET のコンパイルの概要](/previous-versions/aspnet/ms178466(v=vs.100))」を参照してください。

## <a name="configure-the-wcf-service"></a>WCF サービスの構成

IIS でホストされる WCF サービスの構成は、アプリケーションの Web.config ファイル内に格納されます。 IIS でホストされるサービスは、IIS の外部でホストされる WCF サービスと同じ構成要素と構文を使用します。 ただし、次の制約は、IIS ホスト環境に固有です。

- IIS でホストされるサービスのベース アドレス。

- IIS の外部の WCF サービスをホストするアプリケーションは、ベース アドレス URI のセットを <xref:System.ServiceModel.ServiceHost> コンストラクターに渡すか、サービスの構成内で [\<host>](../../configure-apps/file-schema/wcf/host.md) 要素を指定することによって、ホストするサービスのベース アドレスを制御できます。 IIS でホストされるサービスは、それぞれのベース アドレスを制御できません。IIS でホストされるサービスのベース アドレスは、その .svc ファイルのアドレスです。

### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS でホストされるサービスのエンドポイント アドレス

IIS でホストされるときのエンドポイント アドレスは、常にサービスを表す .svc ファイルのアドレスを基準にした相対アドレスと見なされます。 たとえば、WCF サービスのベース アドレスが `http://localhost/Application1/MyService.svc` で、エンドポイント構成が次のとおりであるとします。

```xml
<endpoint address="anotherEndpoint" />
```

これにより、`http://localhost/Application1/MyService.svc/anotherEndpoint` でアクセスできるエンドポイントが提供されます。

同様に、空の文字列が相対アドレスとして使用されるエンドポイント構成要素では、ベース アドレスである `http://localhost/Application1/MyService.svc` でアクセスできるエンドポイントが提供されます。

```xml
<endpoint address="" />
```

IIS でホストされるサービスのエンドポイントには、常に相対エンドポイント アドレスを使用する必要があります。 完全修飾されたエンドポイント アドレス (たとえば `http://localhost/MyService.svc`) を指定すると、エンドポイント アドレスが、エンドポイントを公開するサービスをホストする IIS アプリケーションを指していない場合、サービスの展開時にエラーが発生する可能性があります。 ホストされるサービスに相対エンドポイント アドレスを使用すると、このような競合が回避されます。

### <a name="available-transports"></a>利用可能なトランスポート

IIS 5.1 および IIS 6.0 でホストされる WCF サービスで使用できるのは、HTTP ベースの通信のみに制限されています。 これらの IIS プラットフォームでホストされるサービスで、非 HTTP バインドを使用するように構成すると、サービスをアクティブ化するときにエラーが発生します。 IIS 7.0 でサポートされるトランスポートには、既存の MSMQ アプリケーションとの後方互換性を実現する HTTP、Net.TCP、Net.Pipe、Net.MSMQ、msmq.formatname があります。

### <a name="http-transport-security"></a>HTTP トランスポート セキュリティ

IIS でホストされる WCF サービスでは、サービスが格納されている IIS 仮想ディレクトリで設定がサポートされていれば、HTTP トランスポート セキュリティ (たとえば、基本認証、ダイジェスト認証、Windows 統合認証などの HTTPS および HTTP 認証) を利用できます。 ホストされるエンドポイントのバインディングでの HTTP トランスポート セキュリティ設定は、そのエンドポイントを格納する IIS 仮想ディレクトリでのトランスポート セキュリティ設定と一致する必要があります。

たとえば、HTTP ダイジェスト認証を使用するように構成された WCF エンドポイントは、同じく HTTP ダイジェスト認証を使用できるように構成された IIS 仮想ディレクトリ内に存在する必要があります。 IIS の設定と WCF エンドポイントの設定の組み合わせが一致しない場合、サービスをアクティブ化するときにエラーが発生します。

## <a name="see-also"></a>関連項目

- [インターネット インフォメーション サービスでのホスティング](hosting-in-internet-information-services.md)
- [インターネット インフォメーション サービス ホスティングのベスト プラクティス](internet-information-services-hosting-best-practices.md)
- [AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))
