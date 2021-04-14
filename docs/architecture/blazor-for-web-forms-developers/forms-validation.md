---
title: フォームと検証
description: Blazor でクライアント側の検証を使用したフォームを構築する方法について説明します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- Blazor WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: d2dce23996e996a736b04c9cdd1ccf3b549ff3ff
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "88267556"
---
# <a name="forms-and-validation"></a>フォームと検証

ASP.NET Web Forms フレームワークには、フォームに入力されたユーザー入力の検証を処理する一連の検証サーバー コントロールが含まれています (`RequiredFieldValidator`、`CompareValidator`、`RangeValidator` など)。 ASP.NET Web Forms フレームワークでは、モデル バインドと、データの注釈に基づくモデルの検証もサポートされています (`[Required]`、`[StringLength]`、`[Range]` など)。 検証ロジックは、サーバーとクライアントの両方に、控えめな JavaScript ベースの検証を使用して適用できます。 `ValidationSummary` サーバー コントロールは、検証エラーの概要をユーザーに表示するために使用されます。

Blazor では、クライアントとサーバー両方の間での検証ロジックの共有がサポートされています。 ASP.NET には、多くの一般的なサーバー検証の事前構築済みの JavaScript 実装が用意されています。 多くの場合、開発者は、アプリ固有の検証ロジックを完全に実装するために、引き続き JavaScript を記述する必要があります。 サーバーとクライアントの両方で、同じモデル型、データ注釈、および検証ロジックを使用できます。

Blazor には、一連の入力コンポーネントが用意されています。 この入力コンポーネントでは、モデルへのフィールド データのバインドと、フォームが送信されたときのユーザー入力の検証が処理されます。

|入力コンポーネント|レンダリングされる HTML 要素    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

`EditForm` コンポーネントによってこれらの入力コンポーネントがラップされ、`EditContext` を使用して検証プロセスが調整されます。 `EditForm` を作成するときは、`Model` パラメーターを使用して、バインドするモデル インスタンスを指定します。 通常、検証はデータ注釈を使用して行われ、それは拡張可能です。 データ注釈に基づく検証を有効にするには、`EditForm` の子として `DataAnnotationsValidator` コンポーネントを追加します。 `EditForm` コンポーネントには、有効な (`OnValidSubmit`) 送信と無効な (`OnInvalidSubmit`) 送信を処理するための便利なイベントが用意されています。 また、検証を自分でトリガーして処理できるようにする、より汎用的な `OnSubmit` イベントもあります。

検証エラーの概要を表示するには、`ValidationSummary` コンポーネントを使用します。 特定の入力フィールドに対する検証メッセージを表示するには、`ValidationMessage` コンポーネントを使用して、`For` パラメーターに適切なモデル メンバーを指すラムダ式を指定します。

次のモデル型では、データ注釈を使用していくつかの検証規則が定義されています。

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16,
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000,
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true",
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

次のコンポーネントは、`Starship` モデル型に基づいて、Blazor でフォームを構築する方法を示しています。

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

フォームの送信後、モデル バインドされたデータは、データベースなどのデータ ストアに保存されていません。 Blazor WebAssembly アプリでは、データをサーバーに送信する必要があります。 たとえば、HTTP POST 要求を使用します。 Blazor Server アプリでは、データは既にサーバー上にありますが、永続化する必要があります。 Blazor アプリでのデータ アクセスの処理は、[データの処理](data.md)に関するセクションのテーマです。

## <a name="additional-resources"></a>その他のリソース

Blazor アプリの[フォームと検証](/aspnet/core/blazor/forms-validation)の詳細については、Blazor のドキュメントを参照してください。

>[!div class="step-by-step"]
>[前へ](state-management.md)
>[次へ](data.md)
