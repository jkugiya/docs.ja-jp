---
title: ASP.NET MVC と ASP.NET Core の相違点のログ記録
description: ASP.NET MVC と Web API アプリと ASP.NET Core アプリの間でのログ記録はどのように異なりますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0ad12463c8d13d13516ab027e56f809b67f713e4
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401362"
---
# <a name="logging-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core の相違点のログ記録

アプリケーションログには、特に運用環境で実行されているアプリに関する重要な診断情報が表示されます。 ASP.NET Core には、標準化されたログをアプリに追加するための新しいシステムが導入されています。 既存の ASP.NET MVC および Web API アプリでは、ほとんどの場合、サードパーティのログソリューションが使用されますが、これは引き続き ASP.NET Core でサポートされる可能性があります。

## <a name="aspnet-mvc-logging"></a>ASP.NET MVC のログ記録

ASP.NET MVC と Web API apps には組み込みのログソリューションがありません。 代わりに、ほとんどのアプリでは、 [log4net](https://www.nuget.org/packages/log4net/)、 [Nlog](https://www.nuget.org/packages/NLog/)、 [serilog](https://www.nuget.org/packages/Serilog)などのサードパーティ製のログ記録ソリューションを使用します。 多くのチームは、独自のログソリューションをロールすることもできます。 ログフレームワークでは、通常、テキストファイル、データベース、電子メールなど、ログ出力用に複数の "シンク" (ターゲットまたはアペンダー) がサポートされています。 これらは、構成を使用して、システムのどの部分からどのレベルのログメッセージを別のシンクにルーティングするかを決定します。 アプリのログ記録を .NET Core に移行する方法を検討するときは、アプリでのログ記録の実行方法と [構成](configuration-differences.md) 方法を確認してください。

## <a name="aspnet-core-logging"></a>ASP.NET Core のログ記録

ASP.NET Core で [は、ログ記録は](/aspnet/core/fundamentals/logging/) 、アプリの起動時に構成および拡張できる組み込みの機能です。 上記のような logger を含むサードパーティの logger を ASP.NET Core と統合して、その機能を強化することができます。

ASP.NET Core ログは、カテゴリとレベルを使用して、ログ記録と方法を制御します。 通常、クラスは、 `ILogger<T>` ジェネリック型として使用されるクラスの型を使用して、インターフェイスのインスタンスを使用し `T` ます。 このシナリオでは、クラスの完全修飾名がカテゴリとして使用されます。 また、を使用して、カスタムカテゴリで logger を作成することもでき `ILoggerFactory` ます。 ログレベルは、最も詳細なものから最も重要なものまでの範囲 `Trace` `Critical` です。 アプリでは、構成を使用して、カテゴリごと (ワイルドカードを含む) に含める必要があるログの最小レベルを指定できます。

一般的なログ構成では、既定では情報をログに記録すること `Information` ができますが、先頭にプレフィックスが付いたカテゴリのみが `Warning` `Microsoft` あります。

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning"
    }
  }
}
```

ASP.NET Core でのログインのサポートは広範で柔軟です。 詳細については、 [ドキュメントを参照して](/aspnet/core/fundamentals/logging/)ください。

## <a name="migrate-logging"></a>ログの移行

.NET Framework アプリのログ記録を .NET Core に移行する方法は、アプリがどのようにログに記録されるかによって異なります。 サードパーティの NuGet パッケージを使用している場合は、そのパッケージのアップグレードに関するドキュメントを参照してください。 ほとんどの場合、アップグレードパスは非常に簡単です。 独自のログソリューションを使用している場合は、次のいずれかの操作を実行します。

1. ログソリューションを自分で移行する
1. サードパーティ製のログ記録ソリューションへの移行
1. ASP.NET Core の組み込みのログ記録のサポートを使用する

`Microsoft.Extensions.Logging`NuGet 4.3 以降を使用しており、.NET Framework 4.6.1 以降にある限り、.NET Framework アプリからパッケージを参照できます。 アプリがこのパッケージを参照したら、アプリケーションを .NET Core に移行する前に、新しい拡張機能を使用するようにログ記録ステートメントを変換できます。 これにより、新しい拡張機能パッケージを使用してログを記録しながら、.NET Framework でアプリを実行し続けることができるため、完全な移行に向けたステップ実行のストーンが提供されます。

## <a name="references"></a>関連項目

- [.NET Core と ASP.NET Core のログ](/aspnet/core/fundamentals/logging/)
- [Microsoft. Extensions. ログ NuGet パッケージ](https://www.nuget.org/packages/microsoft.extensions.logging/)

>[!div class="step-by-step"]
>[前へ](middleware-modules-handlers.md)
>[次へ](routing-differences.md)
