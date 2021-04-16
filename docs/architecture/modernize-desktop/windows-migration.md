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
# <a name="windows-10-migration"></a>Windows 10 の移行

次のような状況を考えてみます。Windows 7 時代に開発された動作中のデスクトップ アプリケーションがあります。 当時利用可能な WPF テクノロジが使われており、問題なく動作しますが、Windows 10 で実行した場合に、UI と動作が古くなっています。 これは、マトリックスなどの未来的な映画を鑑賞していて、ネオが Nokia 8110 デバイスを使用しているのに気付くようなものです。 映画は 20 年後でも十分に有効ですが、デバイスを現代化した方がメリットがあるでしょう。

Windows 10 のリリースによって、Microsoft では、これまで、タブレットやタッチ デバイスのようなシナリオをサポートし、Microsoft オペレーティング システムのユーザーに最高のエクスペリエンスを提供するために、多くのイノベーションを導入してきました。 たとえば、次のようなことができます。

- Windows Hello を使用して顔でサインインする。
- ペンを使用して、テキストを描画または手書き入力すると、自動的に認識され、デジタル化される。
- WinML を使用して、クラウドに構築されたローカルでカスタマイズされた AI モデルを実行する。

これらのすべての機能は、Windows ランタイム (WinRT) ライブラリを通じて Windows 開発者が使用できます。 ライブラリは .NET Framework と .NET の両方に公開されているため、これらの機能を既存のデスクトップ アプリで利用できます。 XAML Islands を使用して UI を現代化し、時代に即してアプリのビジュアルと動作を改善することもできます。

ここで注意すべき重要な点の 1 つは、この現代化のパスに従うために、.NET Framework テクノロジを捨てる必要がないことです。 .NET に移行する負担もなく、安全に現在の状態に留まり、Windows 10 のすべての利点を得ることができます。 そのように、現代化のパスを選択する能力と柔軟性の両方が得られます。

## <a name="winrt-apis"></a>WinRT API

WinRT API は、Windows 10 開発者が、オペレーティング システムで提供する必要があるすべてのものにアクセスできるようにする、オブジェクト指向の適切に構造化されたアプリケーション プログラミング インターフェイス (API) です。 WinRT API を使用して、特に、プッシュ通知、デバイス API、Microsoft Ink、WinML などの機能をデスクトップ アプリに組み込むことができます。

一般に、WinRT API は従来のデスクトップ アプリから呼び出すことができます。 ただし、次の 2 つの主な領域に、この規則の例外が存在します。

* パッケージ ID が必要な API。
* XAML や Composition などの視覚化を必要とする API。

### <a name="universal-windows-platform-uwp-packages"></a>ユニバーサル Windows プラットフォーム (UWP) パッケージ

#### <a name="application-package-identity"></a>アプリケーション パッケージ ID

UWP アプリには、OS によってアプリケーションのインストールとアンインストールを管理するデプロイ システムがあります。 それには、インストールを宣言型にする必要があります。つまり、インストール中にユーザー コードは実行されません。 代わりに、アプリでシステムと統合する必要があるすべてのもの (プロトコル、ファイルの種類、拡張機能など) をアプリケーション マニフェストで宣言します。 デプロイ時に、デプロイ パイプラインによってそれらの統合ポイントが構成されます。 OS でこのすべての機能を管理し、それを追跡する唯一の方法は、"パッケージ" ごとに、アプリケーションの一意の識別子である ID を持つことです。

一部の WinRT API では、このパッケージ ID が想定どおりに動作することを必要とします。 ただし、ネイティブ C++ や .NET アプリなどの従来のデスクトップ アプリでは、パッケージ ID を必要としない異なるデプロイ システムが使用されています。 これらの WinRT API をデスクトップ アプリケーションで使用する場合は、それらにパッケージ ID を指定する必要があります。

続行する 1 つの方法は、追加のパッケージ化プロジェクトを構築することです。 パッケージ化プロジェクト内で、元のソース コード プロジェクトを指し、提供する ID 情報を指定します。 パッケージをインストールし、インストールされたアプリを実行すると、自動的に ID が取得され、ID を必要とするすべての WinRT API をコードで呼び出すことができます。

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

どの API でパッケージ化されたアプリケーション ID を必要とするかをチェックするには、API を含む型が [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) 属性でマークされているかどうかを調べます。 そうであれば、パッケージ化されていない従来のデスクトップ アプリからそれを呼び出すことができます。 そうでない場合は、パッケージ化プロジェクトを使用して、従来のデスクトップ アプリを UWP に変換する必要があります。

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a>パッケージ化の利点

これらの API へのアクセスを提供するだけでなく、次のようなデスクトップ アプリケーション用の Windows アプリ パッケージを作成することによって、いくつかの追加の利点が得られます。

* **効率的なデプロイ**。 アプリには、ユーザーが自信を持ってアプリケーションをインストールして更新できるようにするための優れたデプロイ エクスペリエンスがあります。 ユーザーがアプリをアンインストールすることを選択した場合、それは跡形もなく完全に削除され、Windows の rot (腐敗) 問題を防ぎます。

* **自動更新とライセンス**。 アプリケーションは、Microsoft Store の組み込みライセンスと自動更新機能に参加できます。 自動更新機能は、ファイルの変更された部分だけがダウンロードされるため、非常に信頼性が高く効率的なメカニズムです。

* **リーチの拡大とシンプルな決済**。 当てはまらないかもしれませんが、Microsoft Store を通じてアプリケーションを配布することを選択すると、何百万もの Windows 10 ユーザーに到達できます。

* **UWP 機能の追加**。 UWP 機能は、自分のペースでアプリのパッケージに追加できます。

#### <a name="prepare-for-packaging"></a>パッケージ化の準備

デスクトップ アプリケーションのパッケージ化に進む前に、プロセスを開始する前に対処する必要があるポイントがいくつかあります。 アプリケーションでは、Microsoft Store のすべての規則とポリシーを遵守し、UWP アプリケーション モデルで実行される必要があります。 たとえば、それは 4.6.2 以降の .NET Framework で実行され、`HKEY_CURRENT_USER` レジストリ ハイブに書き込まれる必要があるため、AppData フォルダーはユーザー固有のアプリローカルの場所に仮想化されます。

パッケージ化の設計目標は、他のアプリとの互換性を維持しながら、アプリケーションの状態をシステム状態から分離することです。 Windows 10 では、アプリケーションを UWP パッケージ内に配置することによって、この目標を達成しています。 実行時にファイル システムとレジストリへのいくつかの変更が検出され、リダイレクトされることで、パッケージ化によって提供されるアプリケーションの信頼されたクリーン インストールとアンインストールの動作の約束が果たされます。

デスクトップ アプリケーション用に作成したパッケージは、サンドボックス化されないデスクトップ専用の完全に信頼できるアプリケーションですが、`HKCU` および `AppData` への書き込みに、軽量の仮想化がアプリに適用されます。 この仮想化により、従来のデスクトップ アプリケーションと同じように、他のアプリと連携することができます。

##### <a name="installation"></a>インストール

アプリ パッケージは、`app_name.exe` という名前の実行可能ファイルで、 *%ProgramFiles%\\WindowsApps\\package_name* の下にインストールされます。 各パッケージ フォルダーには、パッケージ化されたアプリの特別な XML 名前空間を含む `AppxManifest.xml` という名前のマニフェストが格納されます。 マニフェスト ファイル内の `<EntryPoint>` 要素で、完全信頼アプリを参照します。 そのアプリケーションが起動されると、アプリ コンテナー内で実行されるのではなく、通常どおりユーザーとして実行されます。

展開後、パッケージ ファイルは読み取り専用としてマークされ、オペレーティング システムによって厳重にロックダウンされます。 これらのファイルが改ざんされると、Windows によりアプリの起動が回避されます。

##### <a name="file-system"></a>ファイル システム

OS では、フォルダーの場所に応じて、パッケージ化されたデスクトップ アプリケーションに対してさまざまなレベルのファイル システム操作がサポートされています。

ユーザーの *AppData* フォルダーにアクセスしようとすると、システムによって、バックグラウンドでユーザーごと、アプリごとの場所が作成されます。 これにより、パッケージ化されたアプリケーションによって、実際にはプライベート コピーを変更しているときに、実際の *AppData* を編集しているという錯覚が生まれます。 このように書き込みのリダイレクトを行うことで、アプリによって行われたすべてのファイル変更をシステムで追跡できます。 それにより、アンインストール時にそれらのすべてのファイルをクリーンアップして、システムの "rot (腐敗)" を軽減し、ユーザーのアプリケーション削除エクスペリエンスを向上させることができます。

##### <a name="registry"></a>レジストリ

アプリ パッケージには、実際のレジストリ内の `HKLM\Software` と論理的に同等なものとして機能する、registry.dat ファイルが含まれています。 実行時には、この仮想レジストリのハイブの内容がネイティブ システム ハイブにマージされ、両方が一括して表示されます。

パッケージのアップグレード時にすべての書き込みが保持され、アプリケーションのアンインストール時にのみ削除されます。

##### <a name="uninstallation"></a>アンインストール

ユーザーがパッケージをアンインストールすると、`C:\Program Files\WindowsApps\package_name` 下にあるすべてのファイルとフォルダーが削除されるほか、プロセス中にキャプチャされた AppData またはレジストリへのリダイレクトされた書き込みもすべて削除されます。

パッケージ化されたアプリケーションで、インストール、ファイル アクセス、レジストリ、およびアンインストールが処理される方法の詳細については、<https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> を参照してください。

チェックすべき項目の完全な一覧は、<https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> で取得できます。

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a>デスクトップ プロジェクトに WinRT API を追加する方法

このセクションでは、既存の WPF アプリケーションでトースト通知を統合する方法に関するチュートリアルを紹介します。 コードの観点からは単純ですが、プロセス全体を明らかにするのに役立ちます。 通知は、.NET アプリで使用できる多数の利用可能な WinRT API の 1 つです。 この場合、API にはパッケージ ID が必要です。 API でパッケージ ID が不要な場合、このプロセスはさらに簡単になります。

ファイルを読み取り、その内容を画面に表示する既存の WPF サンプル アプリを見てみましょう。 目標は、アプリケーションの起動時にトースト通知を表示することです。

![サンプル アプリケーションが実行しているスクリーンショット](./media/windows-migration/sample-application.png)

最初に、使用する Windows 10 API にパッケージ ID が必要かどうかについて、次のリンクでチェックする必要があります。

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

このサンプルでは、パッケージ化された ID を必要とする <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> API を使用します。

![Microsoft ドキュメントの通知クラス](./media/windows-migration/notification-class-documentation.png)

WinRT API にアクセスするには、`Microsoft.Windows.SDK.Contracts` NuGet パッケージへの参照を追加すると、このパッケージによって、バックグラウンドで魔法が使われます (詳細については、<https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> を参照してください)。

これで、何らかのコードの追加を開始する準備ができました。

アプリケーションの起動時に呼び出される `ShowToastNotification` メソッドを作成します。 それは、XML パターンからトースト通知を構築するだけです。

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

プロジェクトが構築されますが、通知 API にはパッケージ ID が必要ですが、提供していないため、エラーが発生します。 Windows パッケージ化プロジェクトをソリューションに追加すると、問題が解決されます。

![Visual Studio の [新しいプロジェクトの追加] ダイアログ ボックスのスクリーンショット](./media/windows-migration/add-packaging-project.png)

サポートする Windows の最小バージョンとターゲットとするバージョンを選択します。 すべての WinRT API がすべての Windows 10 バージョンでサポートされているわけではありません。 Windows 10 の更新プログラムごとに、このバージョンからのみ使用できる新しい API が追加されます。下位レベルのサポートは使用できません。

![Windows の最小バージョンの選択](./media/windows-migration/select-versions.png)

次の手順は、プロジェクト参照を追加して WPF アプリケーションを Windows パッケージ化プロジェクトに追加することです。

![Windows パッケージ化プロジェクトへの WPF アプリケーションの追加](./media/windows-migration/add-application.png)

![参照マネージャー](./media/windows-migration/reference-manager.png)

Windows パッケージ化プロジェクトでは、複数のアプリをパッケージ化できるため、どれをエントリ ポイントにするかを設定する必要があります。

![エントリ ポイントの設定](./media/windows-migration/set-entry-point.png)

次の手順は、ソリューション構成で WPF プロジェクトをスタートアップ プロジェクトとして設定することです。 F5 キーを押して、コンパイルしてビルドし、結果を確認できます。

![実行して結果が表示されているサンプル アプリケーション](./media/windows-migration/sample-app-result.png)

アプリをインストールできるようにパッケージを生成してみましょう。 **[ストア]**  >  **[アプリ パッケージの作成]** を右クリックします。

![[アプリ パッケージの作成] ダイアログ](./media/windows-migration/create-app-packages.png)

サイドローディング オプションを選択して、コンピューターからアプリをデプロイします。

![サイドローディング オプションの選択](./media/windows-migration/select-sideloading-option.png)

アプリのアプリケーション アーキテクチャを選択します。

![アプリケーション アーキテクチャの選択](./media/windows-migration/select-app-architecture.png)

最後に、 **[作成]** をクリックしてパッケージを作成します。

## <a name="xaml-islands"></a>XAML Islands

XAML Islands は、Windows デスクトップ開発者が既存の Win32 アプリケーション (Windows Forms や WPF など) で UWP XAML コントロールを使用できるようにする一連のコンポーネントです。

![XAML Islands の構造](./media/windows-migration/xaml-islands.png)

標準のコントロールと、それらの中でも最新のコントロールを含む UWP UI の "アイランド" を使用した Win32 アプリを想像できます。 この概念は、Web ページ内に `different page.` のコンテンツを表示する iFrame があることと似ています

Windows 10 API からの機能を追加するだけでなく、XAML Islands を使用して、アプリ内に UWP XAML を追加できます。

Windows 10 1903 更新プログラムでは、Win32 ウィンドウで UWP XAML コンテンツをホストできるようにする一連の API が導入されています。 XAML Islands を使用できるのは、Windows 10 1903 で実行されているアプリのみです。

### <a name="the-road-to-xaml-islands"></a>XAML Islands への道

XAML Islands への道は 2012 年から始まり、そのときに Microsoft では Win32 アプリを現代化するためのフレームワーク (Windows Forms、WPF、およびネイティブ Win32 アプリ) として WinRT API を導入しました。 ただし、WinRT 内の新しい UI コントロールは、新しいアプリケーションでは使用できましたが、既存のアプリケーションでは使用できませんでした。

2015 年に、Windows 10 と共に UWP が誕生しました。 UWP により、XBox、Mobile、Desktop などの Windows デバイス全体で動作するアプリを作成できます。 1 年後、Microsoft はデスクトップ ブリッジ (旧称 Project Centennial) を発表しました。 デスクトップ ブリッジは、開発者が既存の Win32 アプリを Microsoft Store に持ち込めるようにする一連のツールです。 2017 年にさらに機能が追加され、開発者は、アクション センターのライブ タイルや通知など、新しい Windows 10 API を利用して、Win32 アプリを拡張できるようになりました。 しかしまだ、新しい UI コントロールはありませんでした。

ビルド 2018 で、Microsoft は、開発者がアプリを UWP に完全に移行することなく、新しい Windows 10 XAML コントロールを現在の Win32 アプリに組み込む方法を発表しました。 それは、UWP XAML Islands としてブランド化されました。

### <a name="how-it-works"></a>しくみ

Windows 10 1903 更新プログラムでは、いくつかの XAML ホスティング API が導入されています。 そのうちの 2 つは `WindowsXamlManager` と `DesktopWindowXamlSource` です。

`WindowsXamlManager` クラスで、UWP XAML フレームワークを処理します。 その `InitializeForCurrentThread` メソッドで、Win32 アプリの現在のスレッド内に UWP XAML フレームワークを読み込みます。

`DesktopWindowXamlSource` は、XAML Island コンテンツのインスタンスです。 それには、`Content` プロパティがあり、ユーザーがインスタンス化して設定する必要があります。 `DesktopWindowXamlSource` では、HWND からその入力をレンダリングして取得します。 それは、XAML Island の HWND のアタッチ先となる他の HWND を認識している必要があります。また、ユーザーが親の HWND のサイズと配置を指定する必要があります。

WPF や Windows Forms の開発者は、通常コード内で HWND を処理しないので、HWND ポインターや、Win32 や UWP の世界と通信するための基になる接続に関する事項を理解し、処理するのは困難な場合があります。

#### <a name="the-xaml-islands-net-wrappers"></a>XAML Islands .NET ラッパー

Windows Community Toolkit には、XAML Islands を使いやすくする WPF または Windows Forms 用の XAML Islands .NET ラッパー セットが用意されています。 これらのラッパーによって、HWND、フォーカス管理などを管理します。 Windows Forms および WPF 開発者は、これらのラッパーを使用する必要があります。

Windows Community Toolkit には、ラップされたコントロールとホスティング コントロールの 2 種類のコントロールが用意されています。

##### <a name="wrapped-controls"></a>ラップされたコントロール

これらのラップされたコントロールによって、いくつかの UWP コントロールが Windows Forms または WPF コントロールにラップされ、それらの開発者に UWP の概念が隠されます。 これらのコントロールは:

* WebView と WebViewCompatible
* InkCanvas と InkToolbar
* MediaPlayerElement
* MapControl

`Microsoft.Toolkit.Wpf.UI.Controls` パッケージをプロジェクトに追加し、名前空間に参照を含めて、それらの使用を開始します。

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

##### <a name="hosting-controls"></a>ホスティング コントロール

XAML Islands の機能は、ほとんどのファーストパーティ コントロール、サードパーティ コントロール、および UWP 用に開発されたカスタム コントロールに拡張され、完全に機能する UI を含む "アイランド" として Windows Forms および WPF に統合できます。 WPF と Windows Forms の `WindowsXamlHost` コントロールにより、これを実行できます。

たとえば、WPF で `WindowsXamlHost` コントロールを使用するには、Windows Community Toolkit によって提供される `Microsoft.Toolkit.Wpf.UI.XamlHost` パッケージへの参照を追加します。

`WindowsXamlHost` を UI コードに配置したら、読み込む UWP の種類を指定します。 `Button` のようなラップされたコントロールまたは、カスタム UWP コントロールである複数の異なるコントロールによって構成されるより複雑なコントロールを使用することを選択できます。

次の例に、UWP `Button` ボタンを追加する方法を示します。

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

このアプローチ方法については明確な推奨事項があり、それぞれ 1 つのコントロールを含む複数のアイランドを使用するよりも、カスタム複合コントロールを含む 1 つの大きな XAML アイランドを使用する方が推奨されます。

XAML のコア機能の 1 つがバインディングであり、Win32 コードとアイランドの間で機能します。 そのため、たとえば、Win32 `Textbox` と UWP `Textbox` をバインドできます。 考慮すべき重要な点の 1 つとして、これらのバインディングは UWP から Win32 への一方向のバインディングであるため、XAML Island 内で `Textbox` を更新すると、Win32 テキストボックスが更新されますが、その逆は更新されません。

XAML Islands の使用方法に関するチュートリアルについては、次を参照してください。

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a>UWP XAML カスタム コントロールの追加

XAML カスタム コントロールは、ユーザーまたはサードパーティ (WinUI 2.x コントロールを含む) によって作成されたコントロール (またはユーザー コントロール) です。 Windows Forms または WPF アプリでカスタム UWP コントロールをホストするには、次が必要です。

- .NET アプリで `WindowsXamlHost` UWP コントロールを使用する。
- `XamlApplication` オブジェクトを定義する UWP アプリ プロジェクトを作成する。

WPF または Windows Forms プロジェクトでは、Windows Community Toolkit によって提供される `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` クラスのインスタンスにアクセスできる必要があります。 このオブジェクトは、アプリケーションの現在のディレクトリにあるアセンブリにカスタム UWP XAML 型のメタデータを読み込むためのルート メタデータ プロバイダーとして機能します。 これを行うために推奨される方法は、WPF または Windows Forms プロジェクトと同じソリューションに空のアプリ (ユニバーサル Windows) プロジェクトを追加し、このプロジェクトの既定のアプリ クラスを変更することです。

カスタム UWP XAML コントロールは、この UWP アプリか、または WPF や Windows Forms プロジェクトと同じソリューションで参照する独立した UWP クラス ライブラリ プロジェクトに含めることができます。

次で詳細な手順を追ったプロセスの説明を確認できます。

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a>Windows UI ライブラリ (WinUI 2)

OS に付属する受信トレイ Windows 10 コントロール以外にも、同じ UWP XAML チームが Windows UI ライブラリ (**WinUI 2**) に追加のコントロールを提供しています。 WinUI 2 には、Windows UWP アプリ用のネイティブ Microsoft UI コントロールおよび機能が用意されており、これらのコントロールは、XAML Islands 内で使用できます。

WinUI 2 はオープン ソースであり、<https://github.com/microsoft/microsoft-ui-xaml> で、情報を見つけることができ ます。

次の記事で、WinUI 2 ライブラリの UWP コントロールをホストする方法について説明しています。<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

### <a name="do-you-need-xaml-islands"></a>XAML Islands が必要か

XAML Islands は、アプリを完全に書き換えずに新しい UWP コントロールと動作を利用することで、ユーザー エクスペリエンスを向上させる必要がある既存の Win32 アプリを対象としています。 既に [Windows 10 API を利用](/windows/uwp/porting/desktop-to-uwp-enhance)できますが、XAML Islands までは UI に関連しない API のみを利用できます。

新しい Windows アプリを開発している場合、[UWP アプリ](/windows/uwp/get-started/universal-application-platform-guide)が適切なアプローチであると考えられます。

### <a name="the-road-ahead-xaml-islands-winui-30"></a>XAML Islands への道: WinUI 3.0

Windows 8 以降、Windows UI プラットフォーム (XAML UI フレームワーク、ビジュアル コンポジション レイヤー、入力処理など) が Windows の不可欠な部分として出荷されています。 これは、UI テクノロジの最新の機能強化から利点を得るためには、最新バージョンの UI にアップグレードする必要があり、アプリの開発時にイノベーションのペースが低下することを意味します。 これらの 2 つの発展サイクルを分離し、イノベーションを促進するために、Microsoft は、WinUI プロジェクトに積極的に取り組んでいます。

2018 年の WinUI 2 以降、Microsoft は、UWP SDK に基づいて構築された個別の NuGet パッケージとして、いくつかの新しい XAML UI コントロールと機能の出荷を開始しました。

![WinUI 2.0 の構造](./media/windows-migration/winui2.png)

WinUI 3 は、活発な開発段階にあり、完全な UI プラットフォームを含めるように、WinUI の範囲を大幅に拡大しており、UWP SDK から完全に分離されます。

![WinUI 3.0 の構造](./media/windows-migration/winui3.png)

XAML フレームワークは、GitHub で開発され、[NuGet](/nuget/what-is-nuget) パッケージとしてアウトオブバンドで出荷されるようになります。

OS の一部として同梱されている既存の UWP XAML API に対して、新しい機能更新プログラムが提供されることはなくなります。 それらには、Windows 10 のサポート ライフサイクルに従って、セキュリティ更新プログラムと重要な修正プログラムが引き続き提供されます。

ユニバーサル Windows プラットフォームに含まれるものは、XAML フレームワークだけでなく (アプリケーションおよびセキュリティ モデル、メディア パイプライン、Xbox と Windows 10 のシェル統合、広範なデバイス サポートなど)、進化し続けています。 すべての新しい XAML 機能は、代わりに WinUI の一部として開発され、出荷されます。

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a>デスクトップ アプリの WinUI 3 と WinUI XAML Islands

ご覧のように、WinUI 3 は UWP XAML の進化形であり、UWP アプリ モデルとそのすべての要件 (MSIX パッケージ ID、サンドボックス、CoreWindow など) 内で自然に機能します。 Win32 アプリ モデルで WinUI 3 だけを使用するには、WinUI コンテンツを、**WinUI XAML Islands** を使用する別の UI フレームワーク (Windows Forms、WPF など) でホストする必要があります。 これは、アプリを進化させ、テクノロジを混在させる場合の適切なパスです。 ただし、古い UI 全体を WinUI に置き換える場合は、アプリで、WinUI をホストするためだけに UI フレームワークを読み込まないでください。

WinUI 3 によって、**デスクトップアプリへの WinUI** の追加に関するこの重要なフィードバックに対処します。 これにより、Win32 アプリで、スタンドアロン UI フレームワークとして、WinUI 3 を使用できるようになります。Windows Forms や WPF を読み込む必要はありません。

この集合体の中で、WinUI 3 によって、開発者は次の正しい組み合わせを簡単に組み合わせることができるようになります。

* アプリ モデル: UWP、Win32
* プラットフォーム: .NET またはネイティブ
* 言語: .NET (C \#、Visual Basic)、標準 C++
* パッケージ化: MSIX、Microsoft Store 用 AppX、パッケージ化されない
* 相互運用: WinUI 3 を使用し、WinUI XAML Islands を使用する既存の WPF、WinForms、および MFC アプリを拡張する。

詳細については、Microsoft が <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> でこのロードマップを公表しています。

>[!div class="step-by-step"]
>[前へ](migrate-modern-applications.md)
>[次へ](example-migration.md)
