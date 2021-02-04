---
title: .NET の依存関係を管理する
description: .NET アプリケーションのプロジェクトの依存関係を管理する方法について説明します。
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.topic: how-to
ms.date: 01/28/2021
ms.openlocfilehash: 9f5f814d0b4dc7aa3ff1a938c172475169a55bf2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216129"
---
# <a name="manage-dependencies-in-net-applications"></a><span data-ttu-id="e6973-103">.NET アプリケーションの依存関係を管理する</span><span class="sxs-lookup"><span data-stu-id="e6973-103">Manage dependencies in .NET applications</span></span>

<span data-ttu-id="e6973-104">この記事では、プロジェクト ファイルを編集するか、CLI を使用して依存関係を追加および削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6973-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="e6973-105">\<PackageReference> 要素</span><span class="sxs-lookup"><span data-stu-id="e6973-105">The \<PackageReference> element</span></span>

<span data-ttu-id="e6973-106">`<PackageReference>` プロジェクト ファイル要素の構造は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e6973-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="e6973-107">`Include` 属性では、プロジェクトに追加するパッケージの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="e6973-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="e6973-108">`Version` 属性では、取得するバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6973-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="e6973-109">バージョンは、[NuGet のバージョン ルール](/nuget/create-packages/dependency-versions#version-ranges)に従って指定します。</span><span class="sxs-lookup"><span data-stu-id="e6973-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="e6973-110">プロジェクト ファイルの構文に詳しくない場合は、詳細について、[MSBuild プロジェクトのリファレンス](/visualstudio/msbuild/msbuild-project-file-schema-reference) ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6973-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="e6973-111">次の例に示すように、条件を使用して、特定のターゲットでのみ使用できる依存関係を追加します。</span><span class="sxs-lookup"><span data-stu-id="e6973-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="e6973-112">前の例の依存関係は、指定されたターゲットでビルドが行われている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="e6973-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="e6973-113">条件の `$(TargetFramework)` は、プロジェクトで設定される MSBuild プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e6973-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="e6973-114">最も一般的な .NET アプリケーションの場合、これを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e6973-114">For most common .NET applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="e6973-115">プロジェクト ファイルを編集して依存関係を追加する</span><span class="sxs-lookup"><span data-stu-id="e6973-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="e6973-116">依存関係を追加するには、`<ItemGroup>` 要素内に `<PackageReference>` 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="e6973-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="e6973-117">既存の `<ItemGroup>` に追加するか、新しく作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e6973-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="e6973-118">次の例では、`dotnet new console` によって作成された既定のコンソール アプリケーション プロジェクトを使用しています。</span><span class="sxs-lookup"><span data-stu-id="e6973-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="e6973-119">CLI を使用して依存関係を追加する</span><span class="sxs-lookup"><span data-stu-id="e6973-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="e6973-120">依存関係を追加するには、次の例に示すように、[dotnet add package](dotnet-add-package.md) コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e6973-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="e6973-121">プロジェクト ファイルを編集して依存関係を削除する</span><span class="sxs-lookup"><span data-stu-id="e6973-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="e6973-122">依存関係を削除するには、プロジェクト ファイルから `<PackageReference>` 要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="e6973-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="e6973-123">CLI を使用して依存関係を削除する</span><span class="sxs-lookup"><span data-stu-id="e6973-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="e6973-124">依存関係を削除するには、次の例に示すように、[dotnet remove package](dotnet-remove-package.md) コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e6973-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="e6973-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6973-125">See also</span></span>

* [<span data-ttu-id="e6973-126">プロジェクト ファイルのパッケージ参照</span><span class="sxs-lookup"><span data-stu-id="e6973-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* [<span data-ttu-id="e6973-127">dotnet list package コマンド</span><span class="sxs-lookup"><span data-stu-id="e6973-127">dotnet list package command</span></span>](dotnet-list-package.md)
