---
title: '破壊的変更: Razor: コンパイラで 1 つのアセンブリが生成されるようになりました'
description: Razor コンパイラでは 2 つの個別のアセンブリを生成するのに 2 段階のコンパイル プロセスが使用されなくなりました、という ASP.NET Core 6.0 の破壊的変更について説明します。
no-loc:
- Razor
ms.date: 04/08/2021
ms.openlocfilehash: 8b6817563c4670aebfe681d5f24c8e309d2500ad
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299278"
---
# <a name="razor-compiler-no-longer-produces-a-views-assembly"></a>Razor: コンパイラによって Views アセンブリが生成されなくなりました

アプリケーションで定義された CSHTML ビューを含む個別の *Views.dll* ファイルが Razor コンパイラによって生成されなくなりました。

## <a name="version-introduced"></a>導入されたバージョン

ASP.NET Core 6.0 Preview 3

## <a name="old-behavior"></a>以前の動作

以前のバージョンで、Razor コンパイラには次の 2 つのファイルを生成する 2 段階コンパイル プロセスが利用されています。

- アプリケーションの種類を含むメインの *AppName.dll* アセンブリ。
- アプリで定義されている生成済みのビューを含む *AppName.Views.dll* アセンブリ。 生成されるビューの種類は、`public` であり、`AspNetCore` 名前空間の下に置かれます。

## <a name="new-behavior"></a>新しい動作

ビューとアプリケーションの種類は、どちらも 1 つの *AppName.dll* アセンブリに含まれています。 ビューの種類は既定では、アクセシビリティ修飾子 `internal` と `sealed` を持ち、`AspNetCoreGeneratedDocument` 名前空間の下に含められます。

## <a name="reason-for-change"></a>変更理由

2 段階コンパイル プロセスの削除

* Razor ビューを使用するアプリケーションのビルド パフォーマンスが向上します。
* Visual Studio の "ホット リロード" エクスペリエンスに Razor ビューを参加させることができます。

## <a name="recommended-action"></a>推奨アクション

なし。

## <a name="affected-apis"></a>影響を受ける API

なし。

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
