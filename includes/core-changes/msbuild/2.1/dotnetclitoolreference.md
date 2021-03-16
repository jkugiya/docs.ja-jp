---
ms.openlocfilehash: 370c6eb23a50ed388f0b10a5c5f4779ba2a1b144
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102623367"
---
### <a name="project-tools-now-included-in-sdk"></a>プロジェクト ツールが SDK に追加されました

.NET Core 2.1 SDK に一般的な CLI ツールが追加されました。これらのツールをプロジェクトから参照する必要がなくなりました。

#### <a name="change-description"></a>変更内容

.NET Core 2.0 では、`<DotNetCliToolReference>` プロジェクト設定で外部 .NET ツールがプロジェクトによって参照されます。 .NET Core 2.1 では、これらのツールの一部が .NET Core SDK に付属します。この設定は不要になりました。 プロジェクトにこれらのツールへの参照を含めると、"**ツール 'Microsoft.EntityFrameworkCore.Tools.DotNet' は .NET Core SDK に付属するようになりました**" のようなエラーが届きます。

.NET Core 2.1 SDK に追加されたツール:

| \<DotNetCliToolReference> 値                   | ツール                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | `dotnet-watch`               |
| `Microsoft.Extensions.SecretManager.Tools`     | [dotnet-user-secrets](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [dotnet-sql-cache](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [dotnet-ef](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a>導入されたバージョン

.NET Core SDK 2.1.300

#### <a name="recommended-action"></a>推奨アクション

プロジェクトから `<DotNetCliToolReference>` 設定を削除します。

#### <a name="category"></a>カテゴリ

MSBuild

#### <a name="affected-apis"></a>影響を受ける API

N/A
