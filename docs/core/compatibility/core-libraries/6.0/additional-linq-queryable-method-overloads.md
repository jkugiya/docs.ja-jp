---
title: '.NET 6 の破壊的変更: LINQ Queryable メソッドの追加のオーバーロード'
description: System.Linq.Queryable 型にメソッド オーバーロードが追加されたコア .NET ライブラリにおける .NET 6 の破壊的変更について説明します。
ms.date: 03/31/2021
ms.openlocfilehash: 15a4e480f7d1b4e110084e736fc920a522439e69
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106123560"
---
# <a name="new-systemlinqqueryable-method-overloads"></a>新しい System.Linq.Queryable メソッドのオーバーロード

<https://github.com/dotnet/runtime/pull/47231> に実装されている新機能の一部として、追加のパブリック メソッド オーバーロードが <xref:System.Linq.Queryable?displayProperty=fullName> に追加されました。 メソッドの検索時にリフレクション コードの堅牢性が不足していると、これらの追加機能によってクエリ プロバイダーの実装が破損するおそれがあります。

## <a name="change-description"></a>変更の説明

.NET 6 では、新しいオーバーロードが「[影響を受ける API](#affected-apis)」セクションに記載されているメソッドに追加されました。 これらの追加の結果として、次の例に示すようなリフレクション コードが破損するおそれがあります。

```csharp
typeof(System.Linq.Queryable)
    .GetMethods(BindingFlags.Public | BindingFlags.Static)
    .Where(m => m.Name == "ElementAt")
    .Single();
```

このリフレクション コードは、"**シーケンスに複数の要素が含まれています**" といったメッセージと共に <xref:System.InvalidOperationException> をスローするようになりました。

## <a name="version-introduced"></a>導入されたバージョン

6.0 Preview 3 と Preview 4

## <a name="reason-for-change"></a>変更理由

LINQ `Queryable` API を拡張するために新しいオーバーロードが追加されました。

## <a name="recommended-action"></a>推奨される操作

クエリプロバイダー ライブラリの作成者は、リフレクション コードをメソッド オーバーロードの追加に確実に耐えられるようにします。 たとえば、メソッドのパラメーターの型を明示的に受け入れる <xref:System.Type.GetMethod%2A?displayProperty=nameWithType> オーバーロードを使用します。

## <a name="affected-apis"></a>影響を受ける API

次の <xref:System.Linq.Queryable> 拡張メソッドに新しいオーバーロードが追加されました。

- <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Zip%2A?displayProperty=fullName>

<!--

### Category

- Core .NET libraries
- LINQ

### Affected APIs

- `Overload:System.Linq.Queryable.ElementAt`
- `Overload:System.Linq.Queryable.ElementAtOrDefault`
- `Overload:System.Linq.Queryable.Take`
- `Overload:System.Linq.Queryable.Min`
- `Overload:System.Linq.Queryable.Max`
- `Overload:System.Linq.Queryable.FirstOrDefault`
- `Overload:System.Linq.Queryable.LastOrDefault`
- `Overload:System.Linq.Queryable.SingleOrDefault`
- `Overload:System.Linq.Queryable.Zip`

-->
