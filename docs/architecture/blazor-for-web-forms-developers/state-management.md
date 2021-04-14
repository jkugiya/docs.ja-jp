---
title: 状態管理
description: ASP.NET Web Forms と Blazor で状態を管理するためのさまざまなアプローチについて説明します。
author: csharpfritz
ms.author: jefritz
ms.date: 05/15/2020
ms.openlocfilehash: 2ca811f886c6a245ac16c2bd66a68ff16e5bfc44
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "88267725"
---
# <a name="state-management"></a>状態管理

状態管理は Web Forms アプリケーションのカギを握る概念であり、ビュー状態、セッション状態、アプリケーション状態、およびポストバックの機能を使用することで容易になります。 このフレームワークのステートフル機能は、アプリケーションに必要な状態管理を隠し、アプリケーション開発者が機能の提供に専念できるようにするために役立ちました。 ASP.NET Core と Blazor を使用する場合、これらの機能の一部は再配置され、一部は完全に削除されました。 この章では、Blazor の新機能を使用して、状態を維持し、同じ機能を提供する方法について説明します。

## <a name="request-state-management-with-viewstate"></a>ViewState を使用した要求の状態管理

Web Forms アプリケーションでの状態管理を説明する際には、多くの開発者がすぐに ViewState のことを考えます。 Web Forms では、ViewState によって HTTP 要求間のコンテンツの状態が管理されます。それには、大きなエンコードされたテキストのブロックがブラウザーとの間で送受信されます。 ViewState フィールドは、多くの要素を含むページからのコンテンツでいっぱいになり、サイズが数メガバイトにまで拡大する可能性があります。

Blazor Server では、アプリによってサーバーとの継続的な接続が維持されます。 接続がアクティブと見なされている間、アプリの状態 ("*回線*" と呼ばれます) はサーバー メモリに保持されます。 状態は、ユーザーがアプリやアプリ内の特定のページから移動したときにのみ破棄されます。 アクティブなコンポーネントのすべてのメンバーは、サーバーとの各対話の間で使用できます。

この機能にはいくつかの利点があります。

- コンポーネントの状態はいつでも使用でき、対話間で再構築されることはありません。
- 状態はブラウザーに送信されません。

ただし、メモリ内のコンポーネント状態の永続化には、注意すべきいくつかの欠点があります。

- 要求の間でサーバーが再起動した場合、状態は失われます。
- アプリケーション Web サーバーの負荷分散ソリューションには、同じブラウザーからのすべての要求が同じサーバーに返されるようにするために、スティッキー セッションが含まれている必要があります。 要求が別のサーバーに送信されると、状態は失われます。
- サーバー上でのコンポーネント状態の永続化は、Web サーバーのメモリ負荷につながる可能性があります。

上記の理由から、サーバー上のメモリ内に存在するコンポーネントの状態のみに依存することは避けてください。 アプリケーションには、要求間のデータ用にバッキング データ ストアも含まれている必要があります。 この戦略のシンプルな例をいくつか次に示します。

- ショッピング カート アプリケーションで、カートに追加された新しいアイテムの内容をデータベース レコードに保持します。 サーバー上にある状態が失われた場合は、データベース レコードから再構築できます。
- マルチパート Web フォームでは、ユーザーは、各要求の間にアプリケーションによって値が記憶されることを期待します。 ユーザーの各投稿の間でデータ ストアにデータを書き込み、マルチパート フォームが完了したときに、そのデータをフェッチして最終的なフォーム応答構造にまとめられるようにします。

Blazor アプリでの状態管理の詳細については、「[ASP.NET Core Blazor の状態管理](/aspnet/core/blazor/state-management)」を参照してください。

## <a name="maintain-state-with-session"></a>セッションで状態を維持する

Web Forms 開発者は、<xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> ディクショナリ オブジェクトを使用して、現在操作しているユーザーに関する情報を保持できます。 文字列キーを使用して `Session` にオブジェクトを追加するのはとても簡単です。そのオブジェクトは、その後ユーザーがアプリケーションと対話している間に使用できるようになります。 HTTP との対話の管理を回避しようとする際には、`Session` オブジェクトによって状態が管理しやすくなりました。

.NET Framework `Session` オブジェクトのシグネチャは、ASP.NET Core `Session` オブジェクトと同じではありません。 移行して新しいセッション状態機能を使用することを決定する前に、[新しい ASP.NET Core セッションのドキュメント](/dotnet/api/microsoft.aspnetcore.http.isession)を検討してください。

セッションは ASP.NET Core と Blazor Server で使用できますが、データを適切にデータ リポジトリに格納することが推奨されるため、使用はお勧めできません。 また、訪問者がプライバシーの懸念からアプリケーションでの HTTP Cookie の使用を拒否した場合も、セッション状態は機能しません。

ASP.NET Core とセッション状態の構成については、[「ASP.NET Core でのセッションと状態の管理」の記事](/aspnet/core/fundamentals/app-state#session-state)を参照してください。

## <a name="application-state"></a>アプリケーションの状態

Web Forms フレームワークの `Application` オブジェクトには、アプリケーション スコープの構成および状態と対話するための、大規模なクロス要求リポジトリが用意されています。 アプリケーション状態は、要求を行うユーザーに関係なく、すべての要求で参照される、さまざまなアプリケーション構成プロパティを格納するための理想的な場所でした。 `Application` オブジェクトの問題は、データが複数のサーバーにわたって保持されないということでした。 アプリケーション オブジェクトの状態は、再起動の間に失われました。

`Session` と同様に、複数のサーバー インスタンスからアクセスできる永続的なバッキング ストアにデータを移動することをお勧めします。 複数の要求およびユーザー間でアクセスできるようにしたい揮発性のデータがある場合は、シングルトン サービスに簡単に格納して、それをこの情報または対話を必要とするコンポーネントに挿入することができます。

アプリケーション状態を維持するためのオブジェクトの構築とその使用は、次の実装のようになります。

```csharp
public class MyApplicationState
{
    public int VisitorCounter { get; private set; } = 0;

    public void IncrementCounter() => VisitorCounter += 1;
}
```

```csharp
app.AddSingleton<MyApplicationState>();
```

```razor
@inject MyApplicationState AppState

<label>Total Visitors: @AppState.VisitorCounter</label>
```

`MyApplicationState` オブジェクトはサーバーで 1 回だけ作成され、値 `VisitorCounter` がフェッチされて、コンポーネントのラベルに出力されます。 持続性とスケーラビリティのために、`VisitorCounter` 値は永続化され、バッキング データ ストアから取得される必要があります。

## <a name="in-the-browser"></a>ブラウザー内

アプリケーション データは、クライアント側でユーザーのデバイスに格納し、後で使用できるようにすることもできます。 ユーザーのブラウザーの異なるスコープでデータの永続化を可能にするブラウザー機能が 2 つあります。

- `localStorage` - スコープはユーザーのブラウザー全体です。 ページを再読み込みしたり、ブラウザーを閉じて再度開いたり、同じ URL で別のタブを開いたりすると、ブラウザーによって同じ `localStorage` が提供されます
- `sessionStorage` - スコープはユーザーの現在のブラウザー タブです。タブが再読み込みされた場合、状態は維持されます。 しかし、ユーザーが別のタブでアプリケーションを開いたり、ブラウザーを閉じてから再度開いたりすると、状態は失われます。

これらの機能と対話するカスタム JavaScript コードを記述することもできますし、この機能を提供する多数の NuGet パッケージも使用可能です。 そのようなパッケージの 1 つは [Microsoft.AspNetCore.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage) です。

このパッケージを使用して `localStorage` や `sessionStorage` と対話する方法については、[Blazor 状態管理](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package)に関する記事を参照してください。

>[!div class="step-by-step"]
>[前へ](pages-routing-layouts.md)
>[次へ](forms-validation.md)
