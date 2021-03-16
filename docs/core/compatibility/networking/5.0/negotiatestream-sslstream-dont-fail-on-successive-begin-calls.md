---
title: 破壊的変更:NegotiateStream と SslStream によって連続した Begin 操作を許可する
description: .NET 5 での破壊的変更について学習します。セキュリティ ストリームのエラー ケースは異なる方法で処理され、BeginAuthenticateAsServer または BeginAuthenticateAsClient に対する連続した呼び出しが失敗しなくなりました。
ms.date: 10/18/2020
ms.openlocfilehash: 5c042be01873849cc154111a31fc007521508c7b
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256440"
---
# <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a>NegotiateStream と SslStream によって連続した Begin 操作を許可する

セキュリティ ストリームでのエラー ケースの処理は異なり、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` に対する連続した呼び出しが失敗しなくなりました。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、最初に `EndAuthenticateAsServer` または `EndAuthenticateAsClient` を呼び出さずに、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` を連続して呼び出すと、<xref:System.NotSupportedException> になります。 .NET 5 以降では、これらの API は <xref:System.Threading.Tasks.Task> ベースの実装によってサポートされるため、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` を連続して呼び出しても <xref:System.NotSupportedException> にはなりません。

## <a name="reason-for-change"></a>変更理由

内部実装を非同期プログラミング モデル (APM) から <xref:System.Threading.Tasks.Task> ベースに切り替えると、パフォーマンスが向上し、コードの複雑さが軽減されます。

## <a name="recommended-action"></a>推奨アクション

開発者側では、何も行う必要はありません。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

### Category

Networking

-->
