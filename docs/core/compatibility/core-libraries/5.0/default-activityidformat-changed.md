---
title: '破壊的変更: 既定の ActivityIdFormat は W3C'
description: Core .NET ライブラリでの .NET 5 に関する破壊的変更について学習します。この変更により、既定の ActivityIdFormat は W3C になりました。
ms.date: 11/01/2020
ms.openlocfilehash: f15c2d61443117cfbcb2be7de9561fecbff9a1d9
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257506"
---
# <a name="default-activityidformat-is-w3c"></a>既定の ActivityIdFormat は W3C

アクティビティ (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) の既定の ID 形式が <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> になりました。

## <a name="change-description"></a>変更の説明

W3C アクティビティ ID 形式は、階層 ID 形式の代替として .NET Core 3.0 で導入されました。 ただし、互換性を維持するため、W3C 形式は .NET 5.0 まで既定になりませんでした。 [W3C 形式が承認](https://www.w3.org/TR/trace-context/)され、複数の言語実装で牽引力を得たため、.NET 5 で既定が変更されました。

アプリのターゲットが .NET 5 以降のプラットフォームであれば、<xref:System.Diagnostics.ActivityIdFormat.Hierarchical> が既定の形式となる以前の動作が見られます。 この既定は net45+、netstandard1.1+、netcoreapp (1.x、2.x、3.x) に適用されます。 .NET 5 以降では、<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> は <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> に設定されます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

分散トレースに使用されている ID にアプリケーションが依存しない場合、何の措置も必要ありません。 ASP.NET Core や <xref:System.Net.Http.HttpClient> などのライブラリでは、両方のバージョンの <xref:System.Diagnostics.ActivityIdFormat> を使用したり、伝搬したりできます。

既存のシステムとの相互運用性が必要であるか、現行のシステムが ID の形式に依存している場合、<xref:System.Diagnostics.Activity.DefaultIdFormat> を <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> に設定することで以前の動作を保持できます。 あるいは、次の 3 つの方法のいずれかで AppContext スイッチを設定できます。

- プロジェクト ファイルで。

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- *runtimeconfig.json ファイル* で。

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- 環境変数を利用して。

  `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` を `true` または 1 に設定します。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
