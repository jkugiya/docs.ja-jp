---
title: ASP.NET MVC と ASP.NET Core の構成の違い
description: ASP.NET と ASP.NET Core の間で、構成値の格納方法と読み取り方法が大きく変化しました。 このセクションでは、詳細と、ASP.NET から ASP.NET Core に構成を移行する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 1e8e4d4ac408862f0216a5744476047186222304
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401395"
---
# <a name="configuration-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core の構成の違い

ASP.NET と ASP.NET Core の間で、構成値の格納方法と読み取り方法が大きく変化しました。

## <a name="aspnet-mvc-configuration"></a>ASP.NET MVC の構成

ASP.NET apps では、構成は組み込みの .NET 構成ファイルを使用し、アプリフォルダー内の *web.config* とサーバー上の *machine.config* ます。 ほとんどの ASP.NET MVC および Web API アプリの設定は、構成ファイルの `appSettings` 要素または要素に格納さ `connectionStrings` れます。 また、設定クラスにマップできるカスタム構成セクションも使用します。

.NET Framework アプリの構成には、クラスを使用してアクセスし `System.Configuration.ConfigurationManager` ます。 残念ながら、このクラスは構成要素への静的アクセスを提供します。 その結果、ASP.NET MVC アプリは、構成設定へのアクセスを抽象化したり、必要に応じてそれらを挿入したりする傾向があります。 その代わり、ほとんどの .NET Framework アプリは、アプリが設定を使用する必要があるどこでも、構成システムに直接アクセスする傾向があります。

標準的な ASP.NET MVC 構成アクセス:

```csharp
string connectionString =
    ConfigurationManager.ConnectionStrings["DefaultConnection"]
        .ConnectionString;
```

## <a name="aspnet-core-configuration"></a>ASP.NET Core 構成

ASP.NET Core アプリでは、構成がそれ自体で構成可能です。 ただし、ほとんどのアプリでは、標準のプロジェクトテンプレートの一部として提供される既定のセットと、 `ConfigureWebHostDefaults` それらで使用されるメソッドを使用します。 既定の設定では、JSON 形式のファイルを使用します。ファイル *の基本appsettings.js* の設定は、 *のappsettings.Development.jsの* ような環境固有のファイルでオーバーライドできます。 また、既定の構成システムでは、同じ名前付き設定に存在する環境変数を使用して、すべてのファイルベースの設定がさらに優先されます。 これは多くのシナリオで便利であり、ホスト環境に展開するときに特に便利です。これは、構成ファイルの展開によって重要な運用構成設定が誤って上書きされるかどうかを心配する必要がなくなるためです。 構成値は、コマンドライン引数として指定することもできます。

.NET Core では、さまざまな方法で構成値にアクセスできます。 依存関係の挿入は .NET Core に組み込まれているため、構成値は、必要なクラスに挿入されるインターフェイスを使用して一般にアクセスされます。 これには、のようなインターフェイスを渡すことが含まれます <xref:Microsoft.Extensions.Configuration.IConfiguration> が、通常は、 [オプションパターン](/aspnet/core/fundamentals/configuration/options)を使用して、クラスに必要な設定だけを渡すことをお勧めします。

図2-2 は、 `IConfiguration` Razor ページに渡し、そこから構成設定にアクセスする方法を示しています。

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

**図 2-2** を使用した構成値へのアクセス `IConfiguration` 。

オプションパターンを使用すると、設定アクセスは似ていますが、図2-3 に示すように、使用するクラスで必要な設定に厳密に型指定され、さらに具体的に指定できます。

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

**図 2-3** ASP.NET Core のオプションパターンを使用します。

オプションパターンを機能させるには、アプリの起動時にオプションの種類をで構成する必要があり `ConfigureServices` ます。

```csharp
// required in ConfigureServices
services.Configure<PositionOptions>(Configuration.GetSection(PositionOptions.Position));
```

## <a name="migrate-configuration"></a>構成の移行

アプリの構成設定を .NET Framework から .NET Core に移植する方法を検討する場合、最初の手順は、使用されているすべての構成設定を特定することです。 これらのほとんどは、アプリのルートフォルダーにある *web.config* ファイルに含まれますが、一部のアプリでは、共有 *machine.config* ファイルにも設定が必要です。

構成ファイルのすべての設定がカタログ化されたら、次の手順では、アプリ自体で設定を使用する場所と方法を指定します。 一部の設定が使用されていない場合は、移行から除外される可能性があります。 各設定については、使用されているすべての場所に注意してください。これにより、コードを移行するときに、それが漏れないようにすることができます。

ASP.NET アプリを引き続き維持している場合は、への静的参照を回避 `ConfigurationManager` し、インターフェイスを使用してアクセスに置き換えることが役に立つことがあります。 これにより、ASP.NET Core の構成システムへの移行が容易になります。 一般に、外部リソースへの静的アクセスでは、コードのテストと保守が困難になります。そのため、他の場所では、アプリがこのパターンに従う可能性があります。

## <a name="references"></a>関連項目

- [ASP.NET Core での構成](/aspnet/core/fundamentals/configuration/)
- [ASP.NET Core のオプション パターン](/aspnet/core/fundamentals/configuration/options)
- [構成を ASP.NET Core に移行する](/aspnet/core/migration/configuration)
- [静的構成アクセスのリファクタリング](https://ardalis.com/refactoring-static-config-access/)

>[!div class="step-by-step"]
>[前へ](middleware-modules-handlers.md)
>[次へ](routing-differences.md)
