---
title: 破壊的変更:ネイティブ コードから WinForms オブジェクトにアクセスできない
description: ネイティブ コードから Windows フォーム オブジェクトにアクセスできなくなった .NET 5 の破壊的変更について説明します。
ms.date: 01/29/2021
ms.openlocfilehash: 823d37cb8115b8669b254878325a350809393e79
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256094"
---
# <a name="native-code-cant-access-windows-forms-objects"></a>ネイティブ コードが Windows フォーム オブジェクトにアクセスできない

.NET 5 以降、ネイティブ コードから Windows フォーム オブジェクトにアクセスできなくなりました。

## <a name="change-description"></a>変更内容

以前の .NET バージョンでは、一部の Windows フォームの種類は、COM 相互運用機能から参照できるように修飾されていたため、ネイティブ コードからアクセスできました。 .NET 5 以降、Windows フォーム API は、COM 相互運用機能から参照できなくなり、ネイティブ コードにアクセスできなくなりました。 .NET ランタイムでは、すぐに使用できるカスタム タイプ ライブラリの作成がサポートされなくなりました。 さらに、.NET ランタイムは .NET Framework のタイプ ライブラリに依存できなくなりました (.NET Framework の場合と同じようにクラスの構造を維持する必要があります)。

## <a name="reason-for-change"></a>変更理由

- タイプ ライブラリ (TLB ファイル) の生成と検索に使用された列挙からの `ComVisible(true)` の削除: .NET Core には WinForms TLB が用意されていないため、この属性を保持しても意味がありません。
- `AccessibleObject` クラスからの `ComVisible(true)` の削除: クラスは CoCreateable ではなく (パラメーターなしのコンストラクターはありません)、既存のインスタンスを COM に公開するためにその属性は必要ありません。
- `Control` および `Component` クラスからの `ComVisible(true)` の削除: これは、たとえば VB6 や MFC で、OLE または ActiveX を介して WinForms コントロールをホストできるようにするために使用されていました。 ただし、これには、提供されなくなった WinForms の TLB と、レジストリベースのアクティブ化が必要です。これもそのままでは機能しません。 一般に、WinForms コントロールの COM ベースのホスティングは保守されていなかったため、サポートされていない状態のままにするのではなく、サポートが削除されました。
- コントロールからの `ClassInterface` 属性の削除: OLE または ActiveX を介したホスティングがサポートされていない場合、これらの属性は不要です。 これらは、オブジェクトがまだ COM に公開されていて、属性が関連している可能性がある他の場所では保持されています。
- `EventArgs` からの `ComVisible(true)` の削除: これらは、サポートされなくなった OLE または ActiveX ホスティングで使用されていた可能性があります。 これらも CoCreateable ではないため、属性には目的がありません。 また、TLB を指定せずに既存のインスタンスを公開しても意味がありません。
- デリゲートからの `ComVisible(true)` の削除: 目的は不明ですが、WinForms コントロールの ActiveX ホスティングはサポートされなくなったため、実用性がない可能性があります。
- 一部の非公開コードからの `ComVisible(true)` の削除: 考えられる唯一のコンシューマーは新しい Visual Studio デザイナーですが、GUID が指定されていない場合、それがまだ必要である可能性はほとんどありません。
- 一部の任意のパブリック デザイナー クラスからの `ComVisible(true)` の削除: 以前の Visual Studio デザイナーでは、COM 相互運用を使用してこれらのクラスと通信していた可能性があります。 ただし、以前のデザイナーでは .NET Core がサポートされていないため、`ComVisible` としてこれらが必要な場合はほとんどありません。
- `IWin32Window` により、.NET Framework で定義されたものと同じ GUID が定義されましたが、これによって危険な結果が生じます。 .NET Framework との相互運用が必要な場合は、`ComImport` を使用します。
- WinForms マネージド `IDataObject` は `ComVisible` になりました。 これは必須ではありません。`IDataObject` COM 相互運用には別の `ComImport` インターフェイス宣言があります。 TLB が指定されておらず、マーシャリングは常に失敗するため、マネージド `IDataObject` を `ComVisible` にするのは逆効果です。 また、GUID が指定されておらず、.NET Framework とは異なっていたため、文書化されていない IID を削除しても顧客に悪影響が及ぶ可能性はほとんどありません。
- `ComVisible(false)` の削除: 一見したところ、これらは任意の場所に配置されており、既定でクラスを COM 相互運用に公開しない場合は冗長になります。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0

## <a name="recommended-action"></a>推奨される操作

次の例は、.NET Framework および .NET Core 3.1 で機能します。 この例は、.NET Framework タイプ ライブラリに依存しています。これにより、JavaScript からリフレクションを介してフォーム サブクラスにコールバックすることができます。

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

.NET 5 以降のバージョンでこのサンプルを動作させるには、2 つの方法があります。

- `IDispatch` をサポートするユーザー宣言の `ObjectForScripting` オブジェクトを導入します (プロジェクト レベルで明示的に変更されない限り、既定で適用されます)。

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

- 公開するメソッドを使用してインターフェイスを宣言します。

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

## <a name="affected-apis"></a>影響を受ける API

すべての Windows フォーム API。

<!--

### Category

- Windows Forms

-->
