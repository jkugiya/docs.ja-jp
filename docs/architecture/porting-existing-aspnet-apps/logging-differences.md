---
title: ASP.NET MVC と ASP.NET Core でのログの相違点
description: ASP.NET MVC および Web API アプリと ASP.NET Core アプリで、ログはどのように異なるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0ad12463c8d13d13516ab027e56f809b67f713e4
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401362"
---
# <a name="logging-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core でのログの相違点

アプリケーション ログは、特に運用環境で実行されているアプリに対して、重要な診断情報を提供します。 ASP.NET Core では、標準化されたログをアプリに追加するための新しいシステムが導入されています。 多くの場合、既存の ASP.NET MVC アプリや Web API アプリではサードパーティのログ ソリューションが使用されていますが、これはおそらく ASP.NET Core でも引き続きサポートされるでしょう。

## <a name="aspnet-mvc-logging"></a>ASP.NET MVC のログ記録

ASP.NET MVC アプリと Web API アプリには、組み込みのログ ソリューションがありません。 代わりに、ほとんどのアプリで、サードパーティのログ ソリューション ([log4net](https://www.nuget.org/packages/log4net/)、[NLog](https://www.nuget.org/packages/NLog/)、[Serilog](https://www.nuget.org/packages/Serilog) など) が使用されています。 また、多くのチームが、独自のログ ソリューションを展開することを選択しています。 ログ フレームワークでは通常、テキスト ファイル、データベース、電子メールなど、ログ出力のための複数の "シンク" (ターゲットやアペンダーとも呼ばれます) がサポートされています。 これらは構成を使用して、システムのどの部分からどのレベルのログ メッセージをさまざまなリンクにルーティングするかを決定します。 アプリのログを .NET Core に移行する方法を検討する際は、アプリ内でログがどのように実行および[構成](configuration-differences.md)されているかを確認してください。

## <a name="aspnet-core-logging"></a>ASP.NET Core のログ記録

ASP.NET Core では、[ログは組み込みの機能であり](/aspnet/core/fundamentals/logging/)、アプリの起動時に構成および拡張できます。 前述のようなサードパーティのロガーを ASP.NET Core と統合して、その機能を強化できます。

ASP.NET Core のログでは、カテゴリとレベルを使用してログの対象と方法を制御します。 通常、クラスでは `ILogger<T>` インターフェイスのインスタンスが使用され、クラスの型がジェネリック `T` 型として使用されます。 このシナリオでは、クラスの完全修飾名がカテゴリとして使用されます。 `ILoggerFactory` を使用して、カスタム カテゴリでロガーを作成することもできます。 ログのレベルには、最も詳細な `Trace` から、最も重要な `Critical` までがあります。 アプリでは、構成を使用して、カテゴリごと (ワイルドカードを含む) に含めるログの最小レベルを指定できます。

一般的なログの構成では、既定では `Information` 以上の情報をログしますが、`Microsoft` のプレフィックスが付いたカテゴリからのみ `Warning` 以上の情報をログします。

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

ASP.NET Core でのログのサポートは広範囲で柔軟性があります。 詳細については、[ドキュメントを参照してください](/aspnet/core/fundamentals/logging/)。

## <a name="migrate-logging"></a>ログの移行

.NET Framework アプリのログを .NET Core に移行する方法は、アプリで現在どのようにログが行われているかによって異なります。 サードパーティの NuGet パッケージを使用している場合は、そのパッケージのアップグレードに関するドキュメントを参照してください。 ほとんどの場合、アップグレード パスは非常に簡単です。 独自のログ ソリューションを使用している場合は、次のいずれかのアクションを実行します。

1. ログ ソリューションを自分で移行する
1. サードパーティのログ ソリューションに移行する
1. ASP.NET Core に組み込まれているログ サポートを使用する

.NET Framework アプリが NuGet 4.3 以降を使用していて、.NET Framework 4.6.1 以降で実行されている場合は、アプリから `Microsoft.Extensions.Logging` パッケージを参照できます。 アプリがこのパッケージを参照したら、アプリを .NET Core に移行する前に、新しい拡張機能を使用するようにログ ステートメントを変換できます。 これにより、アプリを引き続き .NET Framework 上で実行しながら新しい拡張機能パッケージを使用してログできるため、完全な移行への足がかりとなります。

## <a name="references"></a>リファレンス

- [.NET Core と ASP.NET Core のログ](/aspnet/core/fundamentals/logging/)
- [Microsoft.Extensions.Logging NuGet パッケージ](https://www.nuget.org/packages/microsoft.extensions.logging/)

>[!div class="step-by-step"]
>[前へ](middleware-modules-handlers.md)
>[次へ](routing-differences.md)
