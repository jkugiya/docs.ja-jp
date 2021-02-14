---
description: '詳細情報: 依存関係プロパティ'
title: 依存関係プロパティ
ms.date: 10/22/2008
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: 78b141d6e8d1bb6bd5cf050a89aa67705111bae3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642306"
---
# <a name="dependency-properties"></a><span data-ttu-id="8ad9e-103">依存関係プロパティ</span><span class="sxs-lookup"><span data-stu-id="8ad9e-103">Dependency Properties</span></span>

<span data-ttu-id="8ad9e-104">依存関係プロパティ (DP) は、その値が、たとえば型変数 (フィールド) に格納されるのではなく、プロパティ ストアに格納される通常のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-104">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>

 <span data-ttu-id="8ad9e-105">添付依存関係プロパティは、オブジェクトとそのコンテナーの間の関係 (たとえば、`Panel` コンテナー上の `Button` オブジェクトの位置) を記述する "プロパティ" を表す静的な Get メソッドと Set メソッドとしてモデル化された、依存関係プロパティの一種です。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-105">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>

 <span data-ttu-id="8ad9e-106">✔️ スタイル設定、トリガー、データ バインディング、アニメーション、動的リソース、継承などの WPF の機能をサポートするためにプロパティが必要な場合は、依存関係プロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-106">✔️ DO provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>

## <a name="dependency-property-design"></a><span data-ttu-id="8ad9e-107">依存関係プロパティの設計</span><span class="sxs-lookup"><span data-stu-id="8ad9e-107">Dependency Property Design</span></span>

 <span data-ttu-id="8ad9e-108">✔️ 依存関係プロパティを実装するときは、<xref:System.Windows.DependencyObject> またはそのいずれかのサブタイプを継承します。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-108">✔️ DO inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="8ad9e-109">この型を使用すると、プロパティ ストアの非常に効率的な実装が提供され、WPF のデータ バインディングが自動的にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-109">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>

 <span data-ttu-id="8ad9e-110">✔️ 依存関係プロパティごとに、通常の CLR プロパティと、<xref:System.Windows.DependencyProperty?displayProperty=nameWithType> のインスタンスを格納するパブリックの静的読み取り専用フィールドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-110">✔️ DO provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>

 <span data-ttu-id="8ad9e-111">✔️ インスタンス メソッド <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> と <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> を呼び出すことにより、依存関係プロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-111">✔️ DO implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="8ad9e-112">✔️ 依存関係プロパティの静的フィールドの名前は、プロパティの名前に "Property" というサフィックスを付けたものにします。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-112">✔️ DO name the dependency property static field by suffixing the name of the property with "Property."</span></span>

 <span data-ttu-id="8ad9e-113">❌ 依存関係プロパティの既定値を、コードで明示的に設定しないでください。代わりに、メタデータで設定します。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-113">❌ DO NOT set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>

 <span data-ttu-id="8ad9e-114">プロパティの既定値を明示的に設定した場合、スタイル設定などの一部の暗黙的な方法によって、そのプロパティを設定できなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-114">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>

 <span data-ttu-id="8ad9e-115">❌ 静的フィールドにアクセスするための標準コード以外のコードを、プロパティ アクセサーに配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-115">❌ DO NOT put code in the property accessors other than the standard code to access the static field.</span></span>

 <span data-ttu-id="8ad9e-116">スタイル設定などの暗黙的な方法によってプロパティが設定された場合、そのコードは実行されません。これは、スタイルによって静的フィールドが直接使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-116">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>

 <span data-ttu-id="8ad9e-117">❌ 依存関係プロパティを使用して、セキュリティ保護されたデータを格納しないでください。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-117">❌ DO NOT use dependency properties to store secure data.</span></span> <span data-ttu-id="8ad9e-118">プライベートな依存関係プロパティであっても、パブリックにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-118">Even private dependency properties can be accessed publicly.</span></span>

## <a name="attached-dependency-property-design"></a><span data-ttu-id="8ad9e-119">添付依存関係プロパティの設計</span><span class="sxs-lookup"><span data-stu-id="8ad9e-119">Attached Dependency Property Design</span></span>

 <span data-ttu-id="8ad9e-120">前のセクションで説明した依存関係プロパティは、宣言する型の組み込みプロパティを表します。たとえば、`Text` プロパティは、それを宣言している `TextButton` のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-120">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="8ad9e-121">添付依存関係プロパティは、特別な種類の依存関係プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-121">A special kind of dependency property is the attached dependency property.</span></span>

 <span data-ttu-id="8ad9e-122">添付プロパティの典型的な例は、<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-122">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8ad9e-123">このプロパティは、(Grid ではなく) Button の列位置を表しますが、Button が Grid に含まれている場合にのみ関連があるので、Grid によって Button に "添付" されています。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-123">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 <span data-ttu-id="8ad9e-124">添付プロパティの定義は、通常の依存関係プロパティとほとんど同じように見えますが、アクセサーが静的な Get と Set メソッドによって表される点が異なります。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-124">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a><span data-ttu-id="8ad9e-125">依存関係プロパティの検証</span><span class="sxs-lookup"><span data-stu-id="8ad9e-125">Dependency Property Validation</span></span>

 <span data-ttu-id="8ad9e-126">通常、プロパティによって検証と呼ばれるものが実装されています。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-126">Properties often implement what is called validation.</span></span> <span data-ttu-id="8ad9e-127">プロパティの値を変更しようとすると、検証ロジックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-127">Validation logic executes when an attempt is made to change the value of a property.</span></span>

 <span data-ttu-id="8ad9e-128">残念ながら、依存関係プロパティのアクセサーに任意の検証コードを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-128">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="8ad9e-129">代わりに、プロパティを登録するときに、依存関係プロパティの検証ロジックを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-129">Instead, dependency property validation logic needs to be specified during property registration.</span></span>

 <span data-ttu-id="8ad9e-130">❌ 依存関係プロパティの検証ロジックを、プロパティのアクセサーに配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-130">❌ DO NOT put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="8ad9e-131">代わりに、検証コールバックを `DependencyProperty.Register` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-131">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>

## <a name="dependency-property-change-notifications"></a><span data-ttu-id="8ad9e-132">依存関係プロパティの変更通知</span><span class="sxs-lookup"><span data-stu-id="8ad9e-132">Dependency Property Change Notifications</span></span>

 <span data-ttu-id="8ad9e-133">❌ 変更通知のロジックを依存関係プロパティのアクセサーに実装しないでください。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-133">❌ DO NOT implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="8ad9e-134">依存関係プロパティには組み込みの変更通知機能があり、変更通知コールバックを <xref:System.Windows.PropertyMetadata> に提供することによって、それを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-134">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>

## <a name="dependency-property-value-coercion"></a><span data-ttu-id="8ad9e-135">依存関係プロパティの値の強制型変換</span><span class="sxs-lookup"><span data-stu-id="8ad9e-135">Dependency Property Value Coercion</span></span>

 <span data-ttu-id="8ad9e-136">プロパティの強制型変換は、プロパティのセッターに渡された値が、プロパティ ストアが実際に変更される前に、セッターによって変更されるときに行われます。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-136">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>

 <span data-ttu-id="8ad9e-137">❌ 依存関係プロパティのアクセサーに、強制型変換のロジックを実装しないでください。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-137">❌ DO NOT implement coercion logic in dependency property accessors.</span></span>

 <span data-ttu-id="8ad9e-138">依存関係プロパティには組み込みの強制型変換機能があり、強制型変換コールバックを `PropertyMetadata` に渡すことによって使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ad9e-138">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>

 <span data-ttu-id="8ad9e-139">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="8ad9e-139">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="8ad9e-140">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="8ad9e-140">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="8ad9e-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ad9e-141">See also</span></span>

- [<span data-ttu-id="8ad9e-142">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="8ad9e-142">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="8ad9e-143">共通デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="8ad9e-143">Common Design Patterns</span></span>](common-design-patterns.md)
