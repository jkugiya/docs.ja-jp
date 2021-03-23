---
title: 破壊的変更と .NET ライブラリ
description: .NET ライブラリを作成するとき、破壊的変更を進行させるためのベストプラクティス推奨事項。
ms.date: 10/02/2018
ms.openlocfilehash: 673a14e69b166fff81e8af9e9c5bf477fdb36871
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873979"
---
# <a name="breaking-changes"></a><span data-ttu-id="5c96a-103">重大な変更</span><span class="sxs-lookup"><span data-stu-id="5c96a-103">Breaking changes</span></span>

<span data-ttu-id="5c96a-104">.NET ライブラリでは既存のユーザーに向けた安定性と将来に向けたイノベーションとの間でバランスを取ることが重要です。</span><span class="sxs-lookup"><span data-stu-id="5c96a-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="5c96a-105">ライブラリ作成者にはコードが完璧になるまでコードを再構成し、再考する傾向がありますが、既存のユーザーを壊すと、特に低レベルのライブラリに対して、マイナスの影響が出ます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="5c96a-106">プロジェクトの種類と破壊的変更</span><span class="sxs-lookup"><span data-stu-id="5c96a-106">Project types and breaking changes</span></span>

<span data-ttu-id="5c96a-107">.NET コミュニティによるライブラリの使用方法によって、破壊的変更がエンドユーザー開発者に与える影響が変わります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

- <span data-ttu-id="5c96a-108">シリアライザー、HTML パーサー、データベース オブジェクトリレーショナル マッパー、Web フレームワークなど、**低レベル/中レベルのライブラリ** が破壊的変更の影響を最も大きく受けます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="5c96a-109">ビルディング ブロック パッケージは、アプリケーションを構築する目的でエンドユーザー開発者が使用します。また、NuGet 依存関係として他のライブラリによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="5c96a-110">たとえば、アプリケーションを構築しているとき、オープン ソースのクライアントを使用して Web サービスを呼び出すとします。</span><span class="sxs-lookup"><span data-stu-id="5c96a-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="5c96a-111">クライアントで使用される依存関係に対する破壊的更新は自分で修正できるものではありません。</span><span class="sxs-lookup"><span data-stu-id="5c96a-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="5c96a-112">変更しなければならないのはオープンソースのクライアントであり、それに対しては何の権限もありません。</span><span class="sxs-lookup"><span data-stu-id="5c96a-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="5c96a-113">互換性のあるライブラリ バージョンを探すか、クライアント ライブラリの修正案を提出し、新しいバージョンが出るのを待つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="5c96a-114">最悪なケースは、使用する 2 つのライブラリが依存する 3 つ目のライブラリのバージョン間で互換性がない場合です。</span><span class="sxs-lookup"><span data-stu-id="5c96a-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

- <span data-ttu-id="5c96a-115">UI コントロール スイートなど、**高レベルのライブラリ** の場合、破壊的変更の影響が小さくなります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="5c96a-116">エンドユーザー アプリケーションでは、高レベルのライブラリは直接参照されます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="5c96a-117">破壊的変更が行われた場合、開発者は最新版への更新を選択するか、破壊的変更に合わせてアプリケーションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="5c96a-118">✔️ ライブラリがどのように使用されるかについてよく考えてください。</span><span class="sxs-lookup"><span data-stu-id="5c96a-118">✔️ DO think about how your library will be used.</span></span> <span data-ttu-id="5c96a-119">破壊的変更はそれを使用するアプリケーションやライブラリにどのような影響を及ぼしますか。</span><span class="sxs-lookup"><span data-stu-id="5c96a-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="5c96a-120">✔️ 低レベルの .NET ライブラリを開発するときは、破壊的変更を最小限に抑えてください。</span><span class="sxs-lookup"><span data-stu-id="5c96a-120">✔️ DO minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="5c96a-121">✔️ ライブラリを大幅に書き直した場合は、新しい NuGet パッケージとして公開することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5c96a-121">✔️ CONSIDER publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="5c96a-122">破壊的変更の種類</span><span class="sxs-lookup"><span data-stu-id="5c96a-122">Types of breaking changes</span></span>

<span data-ttu-id="5c96a-123">破壊的変更はさまざまなカテゴリに属し、その影響力は一様ではありません。</span><span class="sxs-lookup"><span data-stu-id="5c96a-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="5c96a-124">ソースの破壊的変更</span><span class="sxs-lookup"><span data-stu-id="5c96a-124">Source breaking change</span></span>

<span data-ttu-id="5c96a-125">ソースの破壊的変更はプログラム実行に影響を与えませんが、次回、アプリケーションを再コンパイルしたとき、コンパイル エラーを引き起こします。</span><span class="sxs-lookup"><span data-stu-id="5c96a-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="5c96a-126">たとえば、新しいオーバーロードによって、以前はあいまいではなかったメソッド呼び出しに多義性が与えられることがあります。あるいは、パラメーターの名前が変更されると、名前付きパラメーターを使用する呼び出し元が壊れます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="5c96a-127">ソースの破壊的変更は開発者がアプリケーションを再コンパイルするときにのみ害があります。そのため、破壊的変更の中では破壊性が最も少なくなります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="5c96a-128">開発者は壊れた自分のソース コードを簡単に修正できます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="5c96a-129">動作の破壊的変更</span><span class="sxs-lookup"><span data-stu-id="5c96a-129">Behavior breaking change</span></span>

<span data-ttu-id="5c96a-130">動作変更は破壊的変更の中で最も一般的な種類です。動作の場合、何を変更してもたいていは誰かにとって破壊性があります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="5c96a-131">メソッド シグネチャ、スローされた例外、入力/出力データ形式など、ライブラリの変更はすべて、ライブラリの利用者にマイナスの影響の与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="5c96a-132">以前の壊れていた動作にユーザーが依存していた場合、バグの修正が破壊的変更になることがあります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="5c96a-133">機能の追加や不適切動作の改善は良いことですが、慎重に行わない場合、既存ユーザーにとってアップグレードが非常に難しくなります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="5c96a-134">動作の破壊的変更の前に "設定" を置くことが、変更に対処する開発者を助ける 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="5c96a-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="5c96a-135">この "設定" で開発者はライブラリの最新版に更新し、同時に破壊的変更の採用を選択できます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="5c96a-136">このような方法をとることで、開発者は最新の状態を維持しながら、時間をかけてコードを調整できます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="5c96a-137">たとえば、ASP.NET Core MVC には、`MvcOptions` で有効/無効になっている機能を変更する[互換性バージョン](/aspnet/core/mvc/compatibility-version)という概念があります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="5c96a-138">✔️ 新しい機能が既存のユーザーに影響を与える場合は、新しい機能を既定でオフにし、開発者が設定によってその機能を選択できるようにすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5c96a-138">✔️ CONSIDER leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="5c96a-139">バイナリの破壊的変更</span><span class="sxs-lookup"><span data-stu-id="5c96a-139">Binary breaking change</span></span>

<span data-ttu-id="5c96a-140">バイナリの破壊的変更は、ライブラリのパブリック API を変更するときに発生します。そのため、旧バージョンのライブラリに対してコンパイルされたアセンブリはその API を呼び出せなくなります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="5c96a-141">たとえば、新しいパラメーターを追加してメソッドのシグネチャを変更すると、旧バージョンのライブラリに対してコンパイルされたアセンブリから <xref:System.MissingMethodException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="5c96a-142">バイナリの破壊的変更は **アセンブリ全体** を壊すこともあります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="5c96a-143">`AssemblyName` でアセンブリの名前を変更すると、アセンブリの ID が変更されます。アセンブリの厳密な名前付けキーを追加、削除、変更した場合も同様に ID が変更されます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="5c96a-144">アセンブリの ID を変更すると、それを使用するすべてのコンパイル済みコードが壊れます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="5c96a-145">❌ アセンブリ名を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="5c96a-145">❌ DO NOT change an assembly name.</span></span>

<span data-ttu-id="5c96a-146">❌ 厳密な名前付けキーを追加、削除、または変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="5c96a-146">❌ DO NOT add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="5c96a-147">✔️ インターフェイスではなく、抽象基本クラスを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5c96a-147">✔️ CONSIDER using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="5c96a-148">インターフェイスに何かを追加すると、そのインターフェイスを実装する既定の型でエラーが出ます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="5c96a-149">抽象基本クラスを使用すると、既定の仮想実装を追加できます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="5c96a-150">✔️ 削除する予定の型とメンバーに <xref:System.ObsoleteAttribute> を付けることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5c96a-150">✔️ CONSIDER placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="5c96a-151">この属性によって、無効になった API を使用しないようにコードを更新するための指示が与えられます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="5c96a-152"><xref:System.ObsoleteAttribute> が与えられた型やメソッドをコードが呼び出すと、ビルドの警告が出され、属性にメッセージが与えられます。</span><span class="sxs-lookup"><span data-stu-id="5c96a-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="5c96a-153">この警告によって、無効になった API を使用している人に十分な移行時間が与えられます。無効になった API が削除されたとき、ほとんどの人がそれを使用しなくなっています。</span><span class="sxs-lookup"><span data-stu-id="5c96a-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

<span data-ttu-id="5c96a-154">✔️ 低レベルおよび中レベルのライブラリでは、<xref:System.ObsoleteAttribute> が指定された型やメソッドを無期限に保持することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5c96a-154">✔️ CONSIDER keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="5c96a-155">API を削除することはバイナリの破壊的変更です。</span><span class="sxs-lookup"><span data-stu-id="5c96a-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="5c96a-156">保守管理コストが低く、ライブラリに与える技術的な負荷が大きくなければ、無効になった型とメソッドを保持することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5c96a-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="5c96a-157">型やメソッドを削除しなければ、前述の最悪なケースを回避できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5c96a-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c96a-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c96a-158">See also</span></span>

- [<span data-ttu-id="5c96a-159">C# 開発者向けのバージョンと更新に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="5c96a-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- [<span data-ttu-id="5c96a-160">API の決定版ガイド - .NET の破壊的変更</span><span class="sxs-lookup"><span data-stu-id="5c96a-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [<span data-ttu-id="5c96a-161">.NET 破壊的変更ルール</span><span class="sxs-lookup"><span data-stu-id="5c96a-161">.NET breaking change rules</span></span>](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
><span data-ttu-id="5c96a-162">[[戻る]](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="5c96a-162">[Previous](versioning.md)</span></span>
