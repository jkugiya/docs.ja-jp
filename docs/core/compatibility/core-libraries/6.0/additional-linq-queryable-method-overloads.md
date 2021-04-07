---
title: '.NET 6 の破壊的変更: LINQ Queryable メソッドの追加のオーバーロード'
description: System.Linq.Queryable 型にメソッド オーバーロードが追加されたコア .NET ライブラリにおける .NET 6 の破壊的変更について説明します。
ms.date: 03/31/2021
ms.openlocfilehash: 15a4e480f7d1b4e110084e736fc920a522439e69
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106123560"
---
# <a name="new-systemlinqqueryable-method-overloads"></a><span data-ttu-id="7172d-103">新しい System.Linq.Queryable メソッドのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="7172d-103">New System.Linq.Queryable method overloads</span></span>

<span data-ttu-id="7172d-104"><https://github.com/dotnet/runtime/pull/47231> に実装されている新機能の一部として、追加のパブリック メソッド オーバーロードが <xref:System.Linq.Queryable?displayProperty=fullName> に追加されました。</span><span class="sxs-lookup"><span data-stu-id="7172d-104">Additional public method overloads have been added to <xref:System.Linq.Queryable?displayProperty=fullName> as part of the new features implemented in <https://github.com/dotnet/runtime/pull/47231>.</span></span> <span data-ttu-id="7172d-105">メソッドの検索時にリフレクション コードの堅牢性が不足していると、これらの追加機能によってクエリ プロバイダーの実装が破損するおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="7172d-105">If your reflection code isn't sufficiently robust when looking up methods, these additions can break your query provider implementations.</span></span>

## <a name="change-description"></a><span data-ttu-id="7172d-106">変更の説明</span><span class="sxs-lookup"><span data-stu-id="7172d-106">Change description</span></span>

<span data-ttu-id="7172d-107">.NET 6 では、新しいオーバーロードが「[影響を受ける API](#affected-apis)」セクションに記載されているメソッドに追加されました。</span><span class="sxs-lookup"><span data-stu-id="7172d-107">In .NET 6, new overloads were added to the methods listed in the [Affected APIs](#affected-apis) section.</span></span> <span data-ttu-id="7172d-108">これらの追加の結果として、次の例に示すようなリフレクション コードが破損するおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="7172d-108">Reflection code, such as that shown in the following example, may break as a result of these additions:</span></span>

```csharp
typeof(System.Linq.Queryable)
    .GetMethods(BindingFlags.Public | BindingFlags.Static)
    .Where(m => m.Name == "ElementAt")
    .Single();
```

<span data-ttu-id="7172d-109">このリフレクション コードは、"**シーケンスに複数の要素が含まれています**" といったメッセージと共に <xref:System.InvalidOperationException> をスローするようになりました。</span><span class="sxs-lookup"><span data-stu-id="7172d-109">This reflection code will now throw an <xref:System.InvalidOperationException> with a message similar to: **Sequence contains more than one element**.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7172d-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="7172d-110">Version introduced</span></span>

<span data-ttu-id="7172d-111">6.0 Preview 3 と Preview 4</span><span class="sxs-lookup"><span data-stu-id="7172d-111">6.0 Preview 3 and Preview 4</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7172d-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="7172d-112">Reason for change</span></span>

<span data-ttu-id="7172d-113">LINQ `Queryable` API を拡張するために新しいオーバーロードが追加されました。</span><span class="sxs-lookup"><span data-stu-id="7172d-113">The new overloads were added to extend the LINQ `Queryable` API.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7172d-114">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="7172d-114">Recommended action</span></span>

<span data-ttu-id="7172d-115">クエリプロバイダー ライブラリの作成者は、リフレクション コードをメソッド オーバーロードの追加に確実に耐えられるようにします。</span><span class="sxs-lookup"><span data-stu-id="7172d-115">If you're a query-provider library author, ensure that your reflection code is tolerant of method overload additions.</span></span> <span data-ttu-id="7172d-116">たとえば、メソッドのパラメーターの型を明示的に受け入れる <xref:System.Type.GetMethod%2A?displayProperty=nameWithType> オーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="7172d-116">For example, use a <xref:System.Type.GetMethod%2A?displayProperty=nameWithType> overload that explicitly accepts the method's parameter types.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7172d-117">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="7172d-117">Affected APIs</span></span>

<span data-ttu-id="7172d-118">次の <xref:System.Linq.Queryable> 拡張メソッドに新しいオーバーロードが追加されました。</span><span class="sxs-lookup"><span data-stu-id="7172d-118">New overloads were added for the following <xref:System.Linq.Queryable> extension methods:</span></span>

- <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Zip%2A?displayProperty=fullName>

<!--

### Category

- Core .NET libraries
- LINQ

### Affected APIs

- `Overload:System.Linq.Queryable.ElementAt`
- `Overload:System.Linq.Queryable.ElementAtOrDefault`
- `Overload:System.Linq.Queryable.Take`
- `Overload:System.Linq.Queryable.Min`
- `Overload:System.Linq.Queryable.Max`
- `Overload:System.Linq.Queryable.FirstOrDefault`
- `Overload:System.Linq.Queryable.LastOrDefault`
- `Overload:System.Linq.Queryable.SingleOrDefault`
- `Overload:System.Linq.Queryable.Zip`

-->
