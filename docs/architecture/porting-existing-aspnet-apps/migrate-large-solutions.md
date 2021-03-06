---
title: 大規模なソリューションを ASP.NET Core に移行する
description: 大規模な ASP.NET MVC アプリを ASP.NET Core に移行する方法を見てみましょう。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: d3ebd71213e074ce80dc83fc3230c4e365275ad3
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401359"
---
# <a name="migrate-large-solutions-to-aspnet-core"></a>大規模なソリューションを ASP.NET Core に移行する

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

大規模なソリューションを .NET Framework から .NET Core に移行するには、いくつかの計画が必要です。 依存関係は、依存するプロジェクトの前に移行または更新する必要があります。 依存関係を識別し、.NET Core への移行に関するヘルプを提供するツールがあります。 アプリ、そのスコープ、現在の使用パターンに応じて、移行時にさまざまな戦略を採用できます。 現在のシステムと並行して、または時間の経過と共に移行しますか。 新しいシステムを新しいシステムにラップし、その機能を段階的に交換しますか。

この章では、大規模なソリューションの移行計画を作成する方法、移行を支援するツールの使用方法、移行自体について検討する必要があるいくつかの方法について説明します。

## <a name="references"></a>関連項目

- [大規模な MVC および Web API アプリを .NET Core に移行するには、どのトピックが重要ですか?](https://twitter.com/ardalis/status/1313669040859217921)
- [.NET Framework から .NET Core への移植](../../core/porting/index.md)

>[!div class="step-by-step"]
>[前へ](testing-differences.md)
>[次へ](identify-migration-sequence.md)
