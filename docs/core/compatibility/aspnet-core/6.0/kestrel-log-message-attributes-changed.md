---
title: '破壊的変更:Kestrel: 変更されたログ メッセージ属性'
description: 'ASP.NET Core 6.0 での破壊的変更について学習します。タイトル: Kestrel: 変更されたログ メッセージ属性'
ms.author: scaddie
ms.date: 02/01/2021
ms.openlocfilehash: daeb9ae418f343a00e9563ef3e2b5090a7f016a9
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255169"
---
# <a name="kestrel-log-message-attributes-changed"></a>Kestrel: 変更されたログ メッセージ属性

Kestrel ログ メッセージには ID と名前が関連付けられています。 これらの属性により、さまざまな種類のログ メッセージが一意に識別されます。 それらの ID と名前の一部が誤って重複していました。 この重複の問題は、ASP.NET Core 6.0 で修正されています。

## <a name="version-introduced"></a>導入されたバージョン

ASP.NET Core 6.0

## <a name="old-behavior"></a>以前の動作

ASP.NET Core 6.0 より前の、影響を受けたログ メッセージの状態を次の表に示します。

| メッセージの説明                   | 名前                    | id |
|---------------------------------------|-------------------------|----|
| 閉じられた HTTP/2 接続に関するログ メッセージ | `Http2ConnectionClosed` | 36 |
| HTTP/2 フレームの送信に関するログ メッセージ     | `Http2FrameReceived`    | 37 |

## <a name="new-behavior"></a>新しい動作

ASP.NET Core 6.0 の、影響を受けたログ メッセージの状態を次の表に示します。

| メッセージの説明                   | 名前                    | id |
|---------------------------------------|-------------------------|----|
| 閉じられた HTTP/2 接続に関するログ メッセージ | `Http2ConnectionClosed` | 48 |
| HTTP/2 フレームの送信に関するログ メッセージ     | `Http2FrameSending`     | 49 |

## <a name="reason-for-change"></a>変更理由

さまざまなメッセージの種類を識別できるように、ログの ID と名前は一意である必要があります。

## <a name="recommended-action"></a>推奨される操作

古い ID と名前を参照するコードまたは構成がある場合は、新しい ID と名前を使用するようにそれらの参照を更新してください。

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
