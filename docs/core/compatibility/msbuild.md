---
title: MSBuild に関する破壊的変更
description: MSBuild for .NET Core 2.1 から 3.1 の破壊的変更を一覧で示します。
ms.date: 02/22/2021
ms.openlocfilehash: 03fcd9807a83c4f679dc659b009c857e351b9b2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105644"
---
# <a name="msbuild-breaking-changes-in-net-core-21---31"></a>.NET Core 2.1 から 3.1 の MSBuild に関する破壊的変更

このページでは、次の破壊的変更について説明します。

| 互換性に影響する変更点 | 導入されたバージョン |
| - | - |
| [デザイン時のビルドから最上位のパッケージ参照のみが返される](#design-time-builds-only-return-top-level-package-references) | 3.1 |
| [リソース マニフェストのファイル名の変更](#resource-manifest-file-name-change) | 3.0 |
| [プロジェクト ツールが SDK に追加されました](#project-tools-now-included-in-sdk) | 2.1 |

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE [design-time-builds-return-top-level-package-refs](../../../includes/core-changes/msbuild/3.1/design-time-builds-return-top-level-package-refs.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](../../../includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [DotNetCliToolReference project elements removed for bundled tools](../../../includes/core-changes/msbuild/2.1/dotnetclitoolreference.md)]

***
