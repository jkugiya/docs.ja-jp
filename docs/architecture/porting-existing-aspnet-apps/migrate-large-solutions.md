---
title: 大規模なソリューションを ASP.NET Core に移行する
description: 大規模な ASP.NET MVC アプリを ASP.NET Core に移行する方法を見てみましょう。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: d3ebd71213e074ce80dc83fc3230c4e365275ad3
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401359"
---
# <a name="migrate-large-solutions-to-aspnet-core"></a>大規模なソリューションを ASP.NET Core に移行する

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

大規模なソリューションを .NET Framework から .NET Core に移行するには、いくつかの計画が必要です。 依存関係は、それに依存するプロジェクトよりも前に移行または更新する必要があります。 依存関係を特定し、.NET Core への移行を支援するツールがあります。 移行時には、アプリ、そのスコープ、および現在の使用パターンに応じてさまざまな戦略を使用できます。 すべてを一度に移行しますか、それとも、現在のシステムとサイドバイサイドで時間をかけて移行しますか? 現在のシステムを新しいシステム内にラップし、その機能を段階的に置き換えますか?

この章では、大規模なソリューションの移行計画を作成する方法、移行を支援するツールの使用方法、移行自体に関して検討すべきいくつかの戦略について説明します。

## <a name="references"></a>リファレンス

- [大規模な MVC アプリおよび Web API アプリを .NET Core に移行するために重要なトピックは何ですか?](https://twitter.com/ardalis/status/1313669040859217921)
- [.NET Framework から .NET Core への移植](../../core/porting/index.md)

>[!div class="step-by-step"]
>[前へ](testing-differences.md)
>[次へ](identify-migration-sequence.md)
