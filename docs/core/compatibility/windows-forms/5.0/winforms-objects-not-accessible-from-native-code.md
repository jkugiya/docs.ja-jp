---
title: 破壊的変更:ネイティブ コードから WinForms オブジェクトにアクセスできない
description: ネイティブ コードから Windows フォーム オブジェクトにアクセスできなくなった .NET 5.0 の破壊的変更について説明します。
ms.date: 01/29/2021
ms.openlocfilehash: 53343f3f07817f735fa3b0ee77a352dcc80d4b6c
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506477"
---
# <a name="native-code-cant-access-windows-forms-objects"></a><span data-ttu-id="8f680-103">ネイティブ コードが Windows フォーム オブジェクトにアクセスできない</span><span class="sxs-lookup"><span data-stu-id="8f680-103">Native code can't access Windows Forms objects</span></span>

<span data-ttu-id="8f680-104">.NET 5.0 以降、ネイティブ コードから Windows フォーム オブジェクトにアクセスできなくなりました。</span><span class="sxs-lookup"><span data-stu-id="8f680-104">Starting in .NET 5.0, you can no longer access Windows Forms objects from native code.</span></span>

## <a name="change-description"></a><span data-ttu-id="8f680-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="8f680-105">Change description</span></span>

<span data-ttu-id="8f680-106">以前の .NET バージョンでは、一部の Windows フォームの種類は、COM 相互運用機能から参照できるように修飾されていたため、ネイティブ コードからアクセスできました。</span><span class="sxs-lookup"><span data-stu-id="8f680-106">In previous .NET versions, some Windows Forms types were decorated as visible to COM interop, and thus were accessible to native code.</span></span> <span data-ttu-id="8f680-107">.NET 5.0 以降、Windows フォーム API は、COM 相互運用機能から参照できなくなり、ネイティブ コードにアクセスできなくなりました。</span><span class="sxs-lookup"><span data-stu-id="8f680-107">Starting in .NET 5.0, no Windows Forms API are visible to COM interop or accessible to native code.</span></span> <span data-ttu-id="8f680-108">.NET ランタイムでは、すぐに使用できるカスタム タイプ ライブラリの作成がサポートされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="8f680-108">The .NET runtime no longer supports creating custom type libraries out of the box.</span></span> <span data-ttu-id="8f680-109">さらに、.NET ランタイムは .NET Framework のタイプ ライブラリに依存できなくなりました (.NET Framework の場合と同じようにクラスの構造を維持する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="8f680-109">In addition, the .NET runtime can't depend on the type library for .NET Framework (which would require maintaining the shape of classes as they were in .NET Framework).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="8f680-110">変更理由</span><span class="sxs-lookup"><span data-stu-id="8f680-110">Reason for change</span></span>

- <span data-ttu-id="8f680-111">タイプ ライブラリ (TLB ファイル) の生成と検索に使用された列挙からの `ComVisible(true)` の削除: .NET Core には WinForms TLB が用意されていないため、この属性を保持しても意味がありません。</span><span class="sxs-lookup"><span data-stu-id="8f680-111">Removal of `ComVisible(true)` from enumerations that were used for type library (TLB file) generation and lookup: Since there is no WinForms TLB provided by .NET Core, there's no value in keeping this attribute.</span></span>
- <span data-ttu-id="8f680-112">`AccessibleObject` クラスからの `ComVisible(true)` の削除: クラスは CoCreateable ではなく (パラメーターなしのコンストラクターはありません)、既存のインスタンスを COM に公開するためにその属性は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8f680-112">Removal of `ComVisible(true)` from `AccessibleObject` classes: The classes are not CoCreateable (they have no parameterless constructor), and exposing an already existing instance to COM does not require that attribute.</span></span>
- <span data-ttu-id="8f680-113">`Control` および `Component` クラスからの `ComVisible(true)` の削除: これは、たとえば VB6 や MFC で、OLE または ActiveX を介して WinForms コントロールをホストできるようにするために使用されていました。</span><span class="sxs-lookup"><span data-stu-id="8f680-113">Removal of `ComVisible(true)` from `Control` and `Component` classes: This was used to allow hosting of WinForms controls via OLE/ActiveX, for example in VB6 or MFC.</span></span> <span data-ttu-id="8f680-114">ただし、これには、提供されなくなった WinForms の TLB と、レジストリベースのアクティブ化が必要です。これもそのままでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="8f680-114">However, this requires a TLB for WinForms, which is no longer provided, as well as registry-based activation, which also would not work out of the box.</span></span> <span data-ttu-id="8f680-115">一般に、WinForms コントロールの COM ベースのホスティングは保守されていなかったため、サポートされていない状態のままにするのではなく、サポートが削除されました。</span><span class="sxs-lookup"><span data-stu-id="8f680-115">Generally, there was no maintenance of COM-based hosting of WinForms controls, so support was removed instead of leaving it in an unsupported state.</span></span>
- <span data-ttu-id="8f680-116">コントロールからの `ClassInterface` 属性の削除: OLE または ActiveX を介したホスティングがサポートされていない場合、これらの属性は不要です。</span><span class="sxs-lookup"><span data-stu-id="8f680-116">Removal of `ClassInterface` attributes from controls: If hosting via OLE/ActiveX is not supported, these attributes aren't needed anymore.</span></span> <span data-ttu-id="8f680-117">これらは、オブジェクトがまだ COM に公開されていて、属性が関連している可能性がある他の場所では保持されています。</span><span class="sxs-lookup"><span data-stu-id="8f680-117">They are kept in other places where objects are still exposed to COM and the attribute may be relevant.</span></span>
- <span data-ttu-id="8f680-118">`EventArgs` からの `ComVisible(true)` の削除: これらは、サポートされなくなった OLE または ActiveX ホスティングで使用されていた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8f680-118">Removal of `ComVisible(true)` from `EventArgs`: They were most likely used with OLE/ActiveX hosting, which is no longer supported.</span></span> <span data-ttu-id="8f680-119">これらも CoCreateable ではないため、属性には目的がありません。</span><span class="sxs-lookup"><span data-stu-id="8f680-119">They are not CoCreateable either, so the attribute has no purpose.</span></span> <span data-ttu-id="8f680-120">また、TLB を指定せずに既存のインスタンスを公開しても意味がありません。</span><span class="sxs-lookup"><span data-stu-id="8f680-120">Also, exposing existing instances without providing a TLB makes no sense.</span></span>
- <span data-ttu-id="8f680-121">デリゲートからの `ComVisible(true)` の削除: 目的は不明ですが、WinForms コントロールの ActiveX ホスティングはサポートされなくなったため、実用性がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8f680-121">Removal of `ComVisible(true)` from delegates: Purpose is unknown, but since ActiveX hosting of WinForms Controls is no longer supported, it's unlikely to have any usefulness.</span></span>
- <span data-ttu-id="8f680-122">一部の非公開コードからの `ComVisible(true)` の削除: 考えられる唯一のコンシューマーは新しい Visual Studio デザイナーですが、GUID が指定されていない場合、それがまだ必要である可能性はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="8f680-122">Removal of `ComVisible(true)` from some non-public code: The only potential consumer would be the new Visual Studio designer, but without a GUID specified, it's unlikely that it's still needed.</span></span>
- <span data-ttu-id="8f680-123">一部の任意のパブリック デザイナー クラスからの `ComVisible(true)` の削除: 以前の Visual Studio デザイナーでは、COM 相互運用を使用してこれらのクラスと通信していた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8f680-123">Removal of `ComVisible(true)` from some arbitrary public designer classes: The old Visual Studio designer may have been using COM interop to talk to these classes.</span></span> <span data-ttu-id="8f680-124">ただし、以前のデザイナーでは .NET Core がサポートされていないため、`ComVisible` としてこれらが必要な場合はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="8f680-124">However, the old designer doesn't support .NET Core, so few people would need these as `ComVisible`.</span></span>
- <span data-ttu-id="8f680-125">`IWin32Window` により、.NET Framework で定義されたものと同じ GUID が定義されましたが、これによって危険な結果が生じます。</span><span class="sxs-lookup"><span data-stu-id="8f680-125">`IWin32Window` defined the same GUID that was defined in .NET Framework, which has dangerous consequences.</span></span> <span data-ttu-id="8f680-126">.NET Framework との相互運用が必要な場合は、`ComImport` を使用します。</span><span class="sxs-lookup"><span data-stu-id="8f680-126">If you require interop with .NET Framework, use `ComImport`.</span></span>
- <span data-ttu-id="8f680-127">WinForms マネージド `IDataObject` は `ComVisible` になりました。</span><span class="sxs-lookup"><span data-stu-id="8f680-127">The WinForms managed `IDataObject` was made `ComVisible`.</span></span> <span data-ttu-id="8f680-128">これは必須ではありません。`IDataObject` COM 相互運用には別の `ComImport` インターフェイス宣言があります。</span><span class="sxs-lookup"><span data-stu-id="8f680-128">This is not required, there is a separate `ComImport` interface declaration for `IDataObject` COM interop.</span></span> <span data-ttu-id="8f680-129">TLB が指定されておらず、マーシャリングは常に失敗するため、マネージド `IDataObject` を `ComVisible` にするのは逆効果です。</span><span class="sxs-lookup"><span data-stu-id="8f680-129">It's counterproductive to have the managed `IDataObject` be `ComVisible`, since no TLB is provided and marshaling will always fail.</span></span> <span data-ttu-id="8f680-130">また、GUID が指定されておらず、.NET Framework とは異なっていたため、文書化されていない IID を削除しても顧客に悪影響が及ぶ可能性はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="8f680-130">Also, the GUID was not specified and differed from .NET Framework, so its unlikely that removing an undocumented IID will affect customers negatively.</span></span>
- <span data-ttu-id="8f680-131">`ComVisible(false)` の削除: 一見したところ、これらは任意の場所に配置されており、既定でクラスを COM 相互運用に公開しない場合は冗長になります。</span><span class="sxs-lookup"><span data-stu-id="8f680-131">Removal of `ComVisible(false)`: Those are placed in seemingly arbitrary places and are redundant when the default is to not expose classes to COM interop.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8f680-132">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="8f680-132">Version introduced</span></span>

<span data-ttu-id="8f680-133">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="8f680-133">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8f680-134">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="8f680-134">Recommended action</span></span>

<span data-ttu-id="8f680-135">次の例は、.NET Framework および .NET Core 3.1 で機能します。</span><span class="sxs-lookup"><span data-stu-id="8f680-135">The following example works on .NET Framework and .NET Core 3.1.</span></span> <span data-ttu-id="8f680-136">この例は、.NET Framework タイプ ライブラリに依存しています。これにより、JavaScript からリフレクションを介してフォーム サブクラスにコールバックすることができます。</span><span class="sxs-lookup"><span data-stu-id="8f680-136">This example relies on the .NET Framework type library, which allows the JavaScript to call back into the form subclass via reflection.</span></span>

```cs
[PermissionSet(SecurityAction.Demand, Name="FullTrust")]
[System.Runtime.InteropServices.ComVisibleAttribute(true)]
public class Form1 : Form
{
    private WebBrowser webBrowser1 = new WebBrowser();

    protected override void OnLoad(EventArgs e)
    {
        webBrowser1.AllowWebBrowserDrop = false;
        webBrowser1.IsWebBrowserContextMenuEnabled = false;
        webBrowser1.WebBrowserShortcutsEnabled = false;
        webBrowser1.ObjectForScripting = this;

        webBrowser1.DocumentText =
            "<html><body><button " +
            "onclick=\"window.external.Test('called from script code')\">" +
            "call client code from script code</button>" +
            "</body></html>";
    }

    public void Test(String message)
    {
        MessageBox.Show(message, "client code");
    }
}
```

<span data-ttu-id="8f680-137">.NET 5.0 以降のバージョンでこのサンプルを動作させるには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="8f680-137">There are two possible ways to make the example work on .NET 5.0 and later versions:</span></span>

- <span data-ttu-id="8f680-138">`IDispatch` をサポートするユーザー宣言の `ObjectForScripting` オブジェクトを導入します (プロジェクト レベルで明示的に変更されない限り、既定で適用されます)。</span><span class="sxs-lookup"><span data-stu-id="8f680-138">Introduce a user-declared `ObjectForScripting` object that supports `IDispatch` (which is applied by default, unless changed explicitly at the project level).</span></span>

  ```cs
  public class MyScriptObject
  {
      private Form1 _form;

      public MyScriptObject(Form1 form)
      {
          _form = form;
      }

      public void Test(string message)
      {
          MessageBox.Show(message, "client code");
      }
  }

  public partial class Form1 : Form
  {
      protected override void OnLoad(EventArgs e)
      {
          ...

          // Works correctly.
          webBrowser1.ObjectForScripting = new MyScriptObject(this);

          ...
      }
  }
  ```

- <span data-ttu-id="8f680-139">公開するメソッドを使用してインターフェイスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="8f680-139">Declare an interface with the methods to expose.</span></span>

  ```cs
  public interface IForm1
  {
      void Test(string message);
  }

  [ComDefaultInterface(typeof(IForm1))]
  public partial class Form1 : Form, IForm1
  {
      protected override void OnLoad(EventArgs e)
      {
          ...

          // Works correctly.
          webBrowser1.ObjectForScripting = this;

          ...
      }
  }
  ```

## <a name="affected-apis"></a><span data-ttu-id="8f680-140">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="8f680-140">Affected APIs</span></span>

<span data-ttu-id="8f680-141">すべての Windows フォーム API。</span><span class="sxs-lookup"><span data-stu-id="8f680-141">All Windows Forms APIs.</span></span>

<!--

### Category

- Windows Forms

-->
