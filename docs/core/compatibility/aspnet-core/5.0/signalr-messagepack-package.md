---
title: '破壊的変更: SignalR:MessagePack ハブ プロトコルが MessagePack 2.x パッケージに移動された'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: SignalR:MessagePack ハブ プロトコルが MessagePack 2.x パッケージに移動された'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 6851c4fdbaab61e7655dd71ba3c21b8835b2b855
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497113"
---
# <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>SignalR:MessagePack ハブ プロトコルが MessagePack 2.x パッケージに移動された

ASP.NET Core SignalR [MessagePack ハブ プロトコル](/aspnet/core/signalr/messagepackhubprotocol)では、MessagePack のシリアル化に [MessagePack NuGet パッケージ](https://www.nuget.org/packages/MessagePack)が使用されています。 ASP.NET Core 5.0 では、パッケージが 1.x から最新の 2.x パッケージ バージョンにアップグレードされます。

この問題に関するディスカッションについては、[dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 1

## <a name="old-behavior"></a>以前の動作

ASP.NET Core SignalR では、MessagePack 1.x パッケージを使用して、MessagePack メッセージのシリアル化と逆シリアル化が行われていました。

## <a name="new-behavior"></a>新しい動作

ASP.NET Core SignalR では、MessagePack 2.x パッケージを使用して、MessagePack メッセージのシリアル化と逆シリアル化が行われます。

## <a name="reason-for-change"></a>変更理由

MessagePack 2.x パッケージの最新の機能強化により、便利な機能が追加されています。

## <a name="recommended-action"></a>推奨アクション

この破壊的変更は、次の場合に適用されます。

* <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> での値の設定または構成。
* MessagePack API の直接的な使用、および同じプロジェクトでの ASP.NET Core SignalR MessagePack ハブ プロトコルの使用。 以前のバージョンの代わりに、新しいバージョンが読み込まれます。

パッケージ作成者からの移行ガイダンスについては、「[MessagePack v1 から MessagePack v2.x への移行](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)」を参照してください。 メッセージのシリアル化と逆シリアル化のいくつかの側面が影響を受けます。 具体的には、[DateTime 値をシリアル化する方法の動作が変わります](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)。

## <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
