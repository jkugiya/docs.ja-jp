---
title: '破壊的変更: MVC:ObjectModelValidator は、ValidationVisitor.Validate の新しいオーバーロードを呼び出す'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: MVC: ObjectModelValidator は、ValidationVisitor.Validate の新しいオーバーロードを呼び出す'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 7bf07360f5d5e93641b7fbc6634fda2e9f3e649f
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497594"
---
# <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a><span data-ttu-id="3032a-103">MVC:ObjectModelValidator は、ValidationVisitor.Validate の新しいオーバーロードを呼び出す</span><span class="sxs-lookup"><span data-stu-id="3032a-103">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>

<span data-ttu-id="3032a-104">ASP.NET Core 5.0 で、<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> のオーバーロードが追加されました。</span><span class="sxs-lookup"><span data-stu-id="3032a-104">In ASP.NET Core 5.0, an overload of the <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> was added.</span></span> <span data-ttu-id="3032a-105">新しいオーバーロードは、次のプロパティを含む最上位レベルのモデル インスタンスを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="3032a-105">The new overload accepts the top-level model instance that contains properties:</span></span>

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<span data-ttu-id="3032a-106"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> は検証を実行するためにこの `ValidationVisitor` の新しいオーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3032a-106"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invokes this new overload of `ValidationVisitor` to perform validation.</span></span> <span data-ttu-id="3032a-107">この新しいオーバーロードは、検証ライブラリが ASP.NET Core MVC のモデル検証システムと統合されている場合に関連します。</span><span class="sxs-lookup"><span data-stu-id="3032a-107">This new overload is pertinent if your validation library integrates with ASP.NET Core MVC's model validation system.</span></span>

<span data-ttu-id="3032a-108">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3032a-108">For discussion, see GitHub issue [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3032a-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="3032a-109">Version introduced</span></span>

<span data-ttu-id="3032a-110">5.0</span><span class="sxs-lookup"><span data-stu-id="3032a-110">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="3032a-111">以前の動作</span><span class="sxs-lookup"><span data-stu-id="3032a-111">Old behavior</span></span>

<span data-ttu-id="3032a-112">`ObjectModelValidator` は、モデル検証中に、次のオーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3032a-112">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

## <a name="new-behavior"></a><span data-ttu-id="3032a-113">新しい動作</span><span class="sxs-lookup"><span data-stu-id="3032a-113">New behavior</span></span>

<span data-ttu-id="3032a-114">`ObjectModelValidator` は、モデル検証中に、次のオーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3032a-114">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

## <a name="reason-for-change"></a><span data-ttu-id="3032a-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="3032a-115">Reason for change</span></span>

<span data-ttu-id="3032a-116">この変更は、他のプロパティの検査に依存する、<xref:System.ComponentModel.DataAnnotations.CompareAttribute> などの検証コントロールをサポートするために導入されました。</span><span class="sxs-lookup"><span data-stu-id="3032a-116">This change was introduced to support validators, such as <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, that rely on inspection of other properties.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3032a-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="3032a-117">Recommended action</span></span>

<span data-ttu-id="3032a-118">`ValidationVisitor` の既存のオーバーロードを呼び出すために `ObjectModelValidator` に依存する検証フレームワークは、.NET 5.0 以降を対象とする場合に、新しいメソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3032a-118">Validation frameworks that rely on `ObjectModelValidator` to invoke the existing overload of `ValidationVisitor` must override the new method when targeting .NET 5.0 or later:</span></span>

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

## <a name="affected-apis"></a><span data-ttu-id="3032a-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="3032a-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
