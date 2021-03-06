---
title: ミドルウェアとモジュールおよびハンドラーの比較
description: このセクションでは、要求処理パイプラインのミドルウェアを定義する ASP.NET Core アプリでハンドラーとモジュールを使用する ASP.NET アプリの構造の違いについて説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 040ae49d1307ef4dcc9dbf49b20544e9cd2bc913
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401361"
---
# <a name="compare-middleware-to-modules-and-handlers"></a>ミドルウェアとモジュールおよびハンドラーの比較

既存の ASP.NET MVC または Web API アプリが OWIN/Katana を使用している場合は、ミドルウェアの概念を理解している可能性が高く、ASP.NET Core に移植するのは非常に簡単です。 ただし、ほとんどの ASP.NET アプリは、ミドルウェアではなく HTTP モジュールと HTTP ハンドラーに依存しています。 これらの ASP.NET Core に移行するには、余分な作業が必要です。

## <a name="aspnet-modules-and-handlers"></a>ASP.NET モジュールとハンドラー

[Http モジュールと http ハンドラー](/troubleshoot/aspnet/http-modules-handlers) は、ASP.NET アーキテクチャの不可欠な部分です。 要求が処理されている間、各要求は複数の HTTP モジュール (たとえば、認証モジュールとセッションモジュール) によって処理され、1つの HTTP ハンドラーによって処理されます。 ハンドラーが要求を処理した後、要求は HTTP モジュールを経由して返されます。

アプリでカスタム HTTP モジュールまたは HTTP ハンドラーが使用されている場合は、ASP.NET Core に移行するための計画が必要です。 ASP.NET Core に代わる可能性が高いのはミドルウェアです。

## <a name="aspnet-core-middleware"></a>ASP.NET Core ミドルウェア

ASP.NET Core は、各アプリのメソッドで要求パイプラインを定義 `Configure` します。 この要求パイプラインは、アプリによる受信要求の処理方法を定義します。パイプライン内の各メソッドは、最終的にメソッドが終了するまで次のメソッドを呼び出し、 *ミドルウェア* のチェーンは終了してスタックを戻します。 ミドルウェアは、すべての要求を対象にすることも、要求されたパスまたはその他の要因に基づいて特定の要求にのみマップするように構成することもできます。 アプリのメソッドで完全に構成することも `Configure` 、別のクラスに実装することもできます。

HTTP モジュールを使用する ASP.NET MVC アプリでの動作は、 [カスタムミドルウェア](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)に最適な場合があります。 カスタム HTTP ハンドラーは、同じパスに応答するカスタムルートまたはエンドポイントに置き換えることができます。

## <a name="references"></a>関連項目

- [ASP.NET HTTP モジュールと HTTP ハンドラー](/troubleshoot/aspnet/http-modules-handlers)
- [ASP.NET Core ミドルウェア](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
>[前へ](dependency-injection-differences.md)
>[次へ](configuration-differences.md)
