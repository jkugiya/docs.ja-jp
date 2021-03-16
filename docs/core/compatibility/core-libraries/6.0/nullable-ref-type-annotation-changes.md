---
title: 破壊的変更:null 許容参照型の注釈の変更
description: .NET 6 のコア .NET ライブラリで、null 許容参照型の注釈が一部変更されたことによる破壊的変更について説明します。
ms.date: 02/11/2021
ms.openlocfilehash: fe56fd3006528238713bd08f353b5044092043a2
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256934"
---
# <a name="changes-to-nullable-reference-type-annotations"></a>null 許容参照型の注釈の変更

.NET 6 の .NET ライブラリの null 許容参照型の注釈が一部変更されました。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET では、一部の null 許容照型の注釈が正しくなく、ビルド警告がない、または正しくありませんでした。 .NET 6 以降では、以前適用されていた一部の注釈が更新されています。 影響を受ける API は、新しいビルド警告を生成し、正しくないビルド警告を生成しません。

これらの変更の一部は、ビルド時に新しい警告を発する可能性があるため、"*破壊的*" と見なされています。 .NET 6 に移行するときは、これらの API を参照するコードを更新する必要があります。

このページでは、破壊的と見なされないその他の変更についても説明しています。 更新された API を参照するコードには、不要になった演算子やプラグマを削除できることによってメリットがある場合があります。

## <a name="version-introduced"></a>導入されたバージョン

6.0

## <a name="reason-for-change"></a>変更理由

.NET Core 3.0 以降、null 値を許容する注釈が .NET ライブラリに適用されました。 この取り組みでは当初から、これらの注釈に誤りがあることが予想されていました。 フィードバックとさらなるテストから、影響を受ける API での null 値が許容される注釈は不正確であると判断されました。 更新された注釈では、それらの API に対して null 値の許容コントラクトが正しく表現されています。

## <a name="recommended-action"></a>推奨される操作

これらの API を呼び出すコードを更新し、修正された null 値の許容コントラクトを反映します。

## <a name="affected-apis"></a>影響を受ける API

影響を受ける API は、次の表のとおりです。

| API | 変更箇所 | 破壊的または非破壊的 | 追加されたバージョン |
| - | - | - |
| <xref:System.ComponentModel.ISite.Container?displayProperty=nameWithType> | プロパティ型が null 許容に | あり | Preview 1 |
| <xref:System.Xml.Linq.XContainer.Add(System.Object[])?displayProperty=nameWithType> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XContainer.AddFirst(System.Object[])?displayProperty=nameWithType> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])?displayProperty=nameWithType> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Object[])> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Xml.Linq.XDeclaration,System.Object[])> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | 2 番目のパラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XElement.ReplaceAll(System.Object[])?displayProperty=nameWithType> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])?displayProperty=nameWithType> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])?displayProperty=nameWithType> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])?displayProperty=nameWithType> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XNode.ReplaceWith(System.Object[])?displayProperty=nameWithType> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object)> | 2 番目のパラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | 2 番目のパラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Xml.Linq.XStreamingElement.Add(System.Object[])?displayProperty=nameWithType> | パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Net.Http.HttpClient.PatchAsync%2A?displayProperty=nameWithType> | `content` パラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Net.Http.HttpClient.PostAsync%2A?displayProperty=nameWithType> | `content` パラメーター型が null 許容に  | 非破壊的 | Preview 1 |
| <xref:System.Net.Http.HttpClient.PutAsync%2A?displayProperty=nameWithType> | `content` パラメーター型が null 許容に  | 非破壊的 | Preview 1 |
| <xref:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})?displayProperty=nameWithType> | 1 番目のパラメーター型が null 許容に | 非破壊的 | Preview 1 |
| <xref:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})?displayProperty=nameWithType> | 戻り値の型が null 許容ではない | 非破壊的 | Preview 1 |
| <xref:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | `buffer` パラメーター型が null 許容に | あり | Preview 1 |
| <xref:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | `buffer` パラメーター型が null 許容に | あり | Preview 1 |
| <xref:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | `buffer` パラメーター型が null 許容に | あり | Preview 1 |
| <xref:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | `buffer` パラメーター型が null 許容に | あり | Preview 1 |
| <xref:System.Net.HttpListenerContext.AcceptWebSocketAsync%2A?displayProperty=fullName> | `subProtocol` パラメーター型が null 許容に | 非破壊的 | Preview 2 |
| <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> と、[`bool` を返すその他のもの](https://github.com/dotnet/runtime/pull/47598/files)をオーバーライドするメソッド | 最初の null 許容パラメーターに `[NotNullWhen(true)]` を追加 | あり | Preview 2 |

## <a name="see-also"></a>関連項目

- [ASP.NET Core での null 許容参照型の注釈の変更](../../aspnet-core/6.0/nullable-reference-type-annotations-changed.md)

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.ComponentModel.ISite.Container`
- `M:System.Xml.Linq.XContainer.Add(System.Object[])`
- `M:System.Xml.Linq.XContainer.AddFirst(System.Object[])`
- `M:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Xml.Linq.XDeclaration,System.Object[])`
- `M:System.Xml.Linq.XElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAll(System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])`
- `M:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.ReplaceWith(System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object)`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.Add(System.Object[])`
- `O:System.Net.Http.HttpClient.PatchAsync`
- `O:System.Net.Http.HttpClient.PostAsync`
- `O:System.Net.Http.HttpClient.PutAsync`
- `M:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})`
- `M:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})`
- `M:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`

-->
