---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "97700862"
---
### <a name="include-specific-api-surfaces"></a><span data-ttu-id="a6945-101">特定の API サーフェイスを含める</span><span class="sxs-lookup"><span data-stu-id="a6945-101">Include specific API surfaces</span></span>

<span data-ttu-id="a6945-102">ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。</span><span class="sxs-lookup"><span data-stu-id="a6945-102">You can configure which parts of your codebase to run this rule on, based on their accessibility.</span></span> <span data-ttu-id="a6945-103">たとえば、非パブリック API サーフェイスでのみ規則を実行するように指定するには、プロジェクトの *.editorconfig* ファイルに次のキーと値のペアを追加します。</span><span class="sxs-lookup"><span data-stu-id="a6945-103">For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
