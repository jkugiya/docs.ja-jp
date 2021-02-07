---
description: '詳細情報: 例: 動的プログラミングのトラブルシューティング'
title: 例:動的プログラミングのトラブルシューティング
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: 7ad3fde9c81800123abe899e2f696c3833fed5bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747856"
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="b9e22-103">例:動的プログラミングのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b9e22-103">Example: Troubleshooting Dynamic Programming</span></span>

> [!NOTE]
> <span data-ttu-id="b9e22-104">このトピックでは、プレリリース ソフトウェアである .NET Native Developer Preview について述べています。</span><span class="sxs-lookup"><span data-stu-id="b9e22-104">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="b9e22-105">プレビュー版は、[Microsoft Connect Web サイト](https://go.microsoft.com/fwlink/?LinkId=394611)からダウンロードできます (登録が必要です)。</span><span class="sxs-lookup"><span data-stu-id="b9e22-105">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="b9e22-106">.NET Native ツールチェーンを使用して開発されたアプリでのメタデータ参照の失敗によっては、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="b9e22-106">Not all metadata lookup failures in apps developed using the .NET Native tool chain result in an exception.</span></span>  <span data-ttu-id="b9e22-107">予測できない方法でアプリに出現するものもあります。</span><span class="sxs-lookup"><span data-stu-id="b9e22-107">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="b9e22-108">次の例は、null オブジェクトの参照により生じるアクセス違反を示しています。</span><span class="sxs-lookup"><span data-stu-id="b9e22-108">The following example shows an access violation caused by referencing a null object:</span></span>  
  
```output
Access violation - code c0000005 (first chance)  
App!$3_App::Core::Util::NavigationArgs.Setup  
App!$3_App::Core::Util::NavigationArgs..ctor  
App!$0_App::Gibbon::Util::DesktopNavigationArgs..ctor  
App!$0_App::ViewModels::DesktopAppVM.NavigateToPage  
App!$3_App::Core::ViewModels::AppViewModel.NavigateToFirstPage  
App!$3_App::Core::ViewModels::AppViewModel::<HandleLaunch>d__a.MoveNext  
App!$43_System::Runtime::CompilerServices::AsyncMethodBuilderCore.CallMoveNext  
App!System::Action.InvokeClosedStaticThunk  
App!System::Action.Invoke  
App!$43_System::Threading::Tasks::AwaitTaskContinuation.InvokeAction  
App!$43_System::Threading::SendOrPostCallback.InvokeOpenStaticThunk  
[snip]  
```  
  
 <span data-ttu-id="b9e22-109">「[Getting Started](getting-started-with-net-native.md)」(はじめに) の「メタデータの欠落を手動で解決する」セクションで説明されている 3 つの手順からなるアプローチを使用して、この例外をトラブルシューティングしてみましょう。</span><span class="sxs-lookup"><span data-stu-id="b9e22-109">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="b9e22-110">アプリは何をしていたのか?</span><span class="sxs-lookup"><span data-stu-id="b9e22-110">What was the app doing?</span></span>  

 <span data-ttu-id="b9e22-111">最初に注目するのは、スタックの最下位にある `async` キーワード メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="b9e22-111">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="b9e22-112">スタックでは元の呼び出しのコンテキストが失われており、別のスレッドで `async` コードを実行しているため、アプリが `async` メソッドで実際に何を行っていたかを決定するのは困難です。</span><span class="sxs-lookup"><span data-stu-id="b9e22-112">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="b9e22-113">ただし、アプリが最初のページをロードしようとしていたことは推測できます。</span><span class="sxs-lookup"><span data-stu-id="b9e22-113">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="b9e22-114">`NavigationArgs.Setup` の実装で、次のコードによってアクセス違反が発生しました。</span><span class="sxs-lookup"><span data-stu-id="b9e22-114">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 <span data-ttu-id="b9e22-115">この例では、`AppViewModel.Current` の `LayoutVM` プロパティは **null** でした。</span><span class="sxs-lookup"><span data-stu-id="b9e22-115">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="b9e22-116">メタデータの一部が欠落しているため、わずかな動作の違いが生じ、その結果プロパティはアプリで予期されているように設定されるのではなく、初期化されないままになります。</span><span class="sxs-lookup"><span data-stu-id="b9e22-116">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="b9e22-117">コードの `LayoutVM` が初期化される必要がある位置にブレークポイントを設定すると、状況の把握に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b9e22-117">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="b9e22-118">ただし、`LayoutVM` の型は `App.Core.ViewModels.Layout.LayoutApplicationVM` であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b9e22-118">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="b9e22-119">この時点で rd.xml ファイル内に存在するメタデータ ディレクティブは、次のもののみです。</span><span class="sxs-lookup"><span data-stu-id="b9e22-119">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="b9e22-120">失敗の原因として考えられるのは、`App.Core.ViewModels.Layout.LayoutApplicationVM` が別の名前空間にあるために、メタデータが欠落していることです。</span><span class="sxs-lookup"><span data-stu-id="b9e22-120">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="b9e22-121">この場合、`App.Core.ViewModels` のランタイム ディレクティブを追加すると、問題が解決します。</span><span class="sxs-lookup"><span data-stu-id="b9e22-121">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="b9e22-122">根本原因は、**null** を返した <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> メソッドへの API 呼び出しで、アプリではクラッシュが発生するまでエラーを出さずにこの問題を無視していました。</span><span class="sxs-lookup"><span data-stu-id="b9e22-122">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="b9e22-123">動的プログラミングでは、.NET Native でリフレクション Api を使用する場合は、 <xref:System.Type.GetType%2A?displayProperty=nameWithType> エラー発生時に例外をスローするオーバーロードを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b9e22-123">In dynamic programming, a good practice when using reflection APIs under .NET Native is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="b9e22-124">特殊なケースかどうか</span><span class="sxs-lookup"><span data-stu-id="b9e22-124">Is this an isolated case?</span></span>  

 <span data-ttu-id="b9e22-125">`App.Core.ViewModels` を使用する際に、その他の問題が発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="b9e22-125">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="b9e22-126">メタデータの欠落例外すべてを特定して修正する意味があるかどうか、または大きい型のクラスにディレクティブを追加して時間を節約するかを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9e22-126">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="b9e22-127">この場合は、出力バイナリのサイズ増大が問題になるのでなければ、`dynamic` の `App.Core.ViewModels` メタデータを追加するのが最適な方法でしょう。</span><span class="sxs-lookup"><span data-stu-id="b9e22-127">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="b9e22-128">コードを書き換えることができるか</span><span class="sxs-lookup"><span data-stu-id="b9e22-128">Could the code be rewritten?</span></span>  

 <span data-ttu-id="b9e22-129">アプリで `typeof(LayoutApplicationVM)` ではなく `Type.GetType("LayoutApplicationVM")` を使用している場合、ツール チェーンに `browse` メタデータが保存されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9e22-129">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="b9e22-130">ただし、それでも `invoke` メタデータは作成されておらず、そのため型をインスタンス化するときに [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9e22-130">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="b9e22-131">この例外を回避するには、名前空間または `dynamic` ポリシーを指定する型のランタイム ディレクティブを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9e22-131">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="b9e22-132">ランタイム ディレクティブの詳細については、「[ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](runtime-directives-rd-xml-configuration-file-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9e22-132">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e22-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9e22-133">See also</span></span>

- [<span data-ttu-id="b9e22-134">はじめに</span><span class="sxs-lookup"><span data-stu-id="b9e22-134">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="b9e22-135">例:データ バインド時の例外の処理</span><span class="sxs-lookup"><span data-stu-id="b9e22-135">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)
