---
ms.openlocfilehash: b26e346f7076a57aef8ae7587ab1222b4100a323
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957937"
---
## <a name="suppress-a-warning"></a><span data-ttu-id="44aaa-101">警告の非表示</span><span class="sxs-lookup"><span data-stu-id="44aaa-101">Suppress a warning</span></span>

<span data-ttu-id="44aaa-102">規則違反を抑制するには、特定の規則 ID の重大度オプションを `none` EditorConfig ファイルでに設定します。</span><span class="sxs-lookup"><span data-stu-id="44aaa-102">To suppress a rule violation, set the severity option for the specific rule ID to `none` in an EditorConfig file.</span></span> <span data-ttu-id="44aaa-103">例:</span><span class="sxs-lookup"><span data-stu-id="44aaa-103">For example:</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.CA1822.severity = none
```

<span data-ttu-id="44aaa-104">Visual Studio には、コード分析規則からの警告を抑制するための追加の方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="44aaa-104">Visual Studio provides additional ways to suppress warnings from code analysis rules.</span></span> <span data-ttu-id="44aaa-105">詳細については、「 [違反の抑制](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44aaa-105">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span></span>

<span data-ttu-id="44aaa-106">規則の重大度の詳細については、「 [規則の重要度の構成](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44aaa-106">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>
