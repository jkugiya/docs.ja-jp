---
title: NETSDK1059:プロジェクトに古い .NET CLI ツールが含まれています
description: プロジェクトに古い .NET CLI ツールが含まれている問題を解決する方法。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1059
ms.openlocfilehash: cad546ed1636b71be6b77aa00ef2f3a20095daa5
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653037"
---
# <a name="netsdk1059-project-contains-obsolete-net-cli-tool"></a>NETSDK1059:プロジェクトに古い .NET CLI ツールが含まれています

**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン

.NET SDK によって警告 NETSDK1059 が発行される場合、プロジェクトには古い .NET CLI ツールが含まれています。 .NET Core 2.1 では、これらのツールは .NET SDK に含まれており、プロジェクトによって明示的に参照される必要はありません。 詳細については、「[プロジェクト ツールが SDK に追加されました](../../compatibility/2.1.md#project-tools-now-included-in-sdk)」を参照してください。
