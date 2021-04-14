---
title: ASP.NET MVC と ASP.NET Core の構成の相違点
description: 構成値の格納と読み取りの方法は、ASP.NET と ASP.NET Core の間で大きく変わりました。 ここでは、その詳細および ASP.NET から ASP.NET Core に構成を移行する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 1e8e4d4ac408862f0216a5744476047186222304
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401395"
---
# <a name="configuration-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core の構成の相違点

構成値の格納と読み取りの方法は、ASP.NET と ASP.NET Core の間で大きく変わりました。

## <a name="aspnet-mvc-configuration"></a>ASP.NET MVC の構成

ASP.NET アプリでは、構成はアプリ フォルダー内の組み込みの .NET 構成ファイルである *web.config* とサーバー上の *machine.config* を使用します。 ほとんどの ASP.NET MVC アプリおよび Web API アプリの設定は、構成ファイルの `appSettings` 要素または `connectionStrings` 要素に格納されます。 一部のアプリは、設定クラスにマップできるカスタム構成セクションも使用します。

.NET Framework アプリ内の構成には、`System.Configuration.ConfigurationManager` クラスを使用してアクセスします。 残念ながら、このクラスが提供するのは構成要素への静的アクセスです。 そのため、構成設定へのアクセスを抽象化したり、必要に応じて構成設定を挿入したりする傾向のある ASP.NET MVC アプリはほとんどありません。 代わりに、ほとんどの .NET Framework アプリは、アプリが設定を使用する必要のあるすべての場所で構成システムに直接アクセスする傾向があります。

一般的な ASP.NET MVC の構成アクセスを次に示します。

```csharp
string connectionString =
    ConfigurationManager.ConnectionStrings["DefaultConnection"]
        .ConnectionString;
```

## <a name="aspnet-core-configuration"></a>ASP.NET Core 構成

ASP.NET Core アプリでは、構成自体を構成できます。 ただし、ほとんどのアプリでは、標準のプロジェクト テンプレートの一部として提供される既定値のセットと、それらで使用される `ConfigureWebHostDefaults` メソッドを使用します。 既定の設定では、JSON 形式のファイルを使用します。これにより、基本ファイル *appsettings.json* 内の設定を *appsettings.Development.json* などの環境固有のファイルでオーバーライドできます。 また、既定の構成システムでは、同じ名前付き設定用の環境変数を使用して、ファイル ベースのすべての設定がオーバーライドされます。 構成ファイルのデプロイによって運用環境の重要な構成設定が誤って上書きされるかどうかを心配する必要がなくなるため、これは多くのシナリオ (特にホスティング環境へのデプロイ時) に役立ちます。 構成値をコマンド ライン引数として指定することもできます。

.NET Core では、さまざまな方法で構成値にアクセスできます。 依存関係の挿入が .NET Core に組み込まれているため、通常は、構成値を必要とするクラスに挿入されるインターフェイスを使用してその値にアクセスします。 その際、<xref:Microsoft.Extensions.Configuration.IConfiguration> などのインターフェイスを渡す場合がありますが、通常は[オプション パターン](/aspnet/core/fundamentals/configuration/options)を使用して、クラスに必要な設定だけを渡すことをお勧めします。

図 2-2 は、`IConfiguration` を Razor ページに渡し、そこから構成設定にアクセスする方法を示しています。

```csharp
using Microsoft.Extensions.Configuration;

public class TestModel : PageModel
{
    private readonly IConfiguration _configuration;

    public TestModel(IConfiguration configuration)
    {
        _configuration= configuration;
    }

    public ContentResult OnGet()
    {
        var myKeyValue = _configuration["MyKey"];

        // ...
    }
}
```

**図 2-2** `IConfiguration` を使用した構成値へのアクセス。

オプション パターンを使用した設定へのアクセスも同様ですが、図 2-3 に示すように、厳密に型指定されており、使用するクラスで必要な設定に固有のものです。

```csharp
public class PositionOptions
{
    public const string Position = nameof(Position);

    public string Title { get; set; }
    public string Name { get; set; }
}

public class Test2Model : PageModel
{
    private readonly PositionOptions _options;

    public Test2Model(IOptions<PositionOptions> options)
    {
        _options = options.Value;
    }

    public ContentResult OnGet()
    {
        return Content($"Title: {_options.Title}\nName: {_options.Name}");
    }
}
```

**図 2-3** ASP.NET Core でのオプション パターンの使用。

オプション パターンを機能させるには、アプリの起動時にオプションの型を `ConfigureServices` で構成する必要があります。

```csharp
// required in ConfigureServices
services.Configure<PositionOptions>(Configuration.GetSection(PositionOptions.Position));
```

## <a name="migrate-configuration"></a>構成の移行

アプリの構成設定を .NET Framework から .NET Core に移植する方法を検討する場合は、最初の手順として、使用されているすべての構成設定を特定します。 これらのほとんどは、アプリのルート フォルダーにある *web.config* ファイルに含まれていますが、一部のアプリでは共有ファイル *machine.config* にも設定が含まれている場合があります。

構成ファイル内のすべての設定がカタログ化されたら、次の手順では、アプリ自体で設定を使用する場所と方法を特定します。 一部の設定が使用されていない場合は、移行から除外される可能性があります。 コードの移行時に設定の漏れが発生しないように、それぞれの設定が使用されているすべての場所に注意してください。

ASP.NET アプリを引き続き維持する場合は、`ConfigurationManager` への静的参照を回避し、それらをインターフェイスを使用したアクセスに置き換えると役立つ可能性があります。 これにより、ASP.NET Core の構成システムへの移行が容易になります。 一般に、外部リソースへの静的アクセスでは、コードのテストと保守が困難になります。そのため、アプリがこのパターンに従っている可能性のある他の場所に注意してください。

## <a name="references"></a>リファレンス

- [ASP.NET Core での構成](/aspnet/core/fundamentals/configuration/)
- [ASP.NET Core のオプション パターン](/aspnet/core/fundamentals/configuration/options)
- [構成を ASP.NET Core に移行する](/aspnet/core/migration/configuration)
- [Refactoring Static Config Access (静的構成アクセスのリファクタリング)](https://ardalis.com/refactoring-static-config-access/)

>[!div class="step-by-step"]
>[前へ](middleware-modules-handlers.md)
>[次へ](routing-differences.md)
