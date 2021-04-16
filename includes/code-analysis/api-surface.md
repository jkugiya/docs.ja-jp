---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "97700862"
---
### <a name="include-specific-api-surfaces"></a>特定の API サーフェイスを含める

ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。 たとえば、非パブリック API サーフェイスでのみ規則を実行するように指定するには、プロジェクトの *.editorconfig* ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
