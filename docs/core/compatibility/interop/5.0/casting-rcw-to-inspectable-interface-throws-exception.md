---
title: 破壊的変更:RCW を `InterfaceIsIInspectable` にキャストすると例外がスローされる
description: .NET 5 での相互運用に関する破壊的変更について学習します。RCW を `InterfaceIsIInspectable` インターフェイスにキャストすると、PlatformNotSupportedException がスローされます。
ms.date: 09/13/2020
ms.openlocfilehash: 9f777ee9396f7822c9ff6bf5209021c07b8b618a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256635"
---
# <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a>RCW を `InterfaceIsIInspectable` インターフェイスにキャストすると、PlatformNotSupportedException がスローされる

ランタイム呼び出し可能ラッパー (RCW) を <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> とマークされたインターフェイスにキャストすると、<xref:System.PlatformNotSupportedException> がスローされるようになりました。 この変更は、[WinRT のサポートが .NET から削除された](built-in-support-for-winrt-removed.md)ことのフォローアップです。

## <a name="version-introduced"></a>導入されたバージョン

5.0 RC2

## <a name="change-description"></a>変更内容

.NET 5 Preview 6 以前の .NET バージョンでは、RCW を <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> とマークされたインターフェイスにキャストすると想定どおりに動作します。 .NET 5 Preview 6-8 および RC1 では、RCW を <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> インターフェイスに正常にキャストできます。 ただし、ランタイムの基になるサポートが [.NET 5 Preview 6 で削除された](built-in-support-for-winrt-removed.md)ため、インターフェイスでメソッドを実行するとアクセス違反が発生する場合があります。

.NET 5 RC2 以降のバージョンでは、RCW を <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> とマークされたインターフェイスにキャストすると、キャスト時に <xref:System.PlatformNotSupportedException> がスローされます。

## <a name="reason-for-change"></a>変更理由

<xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> のサポートが、[前の .NET 5 Preview で削除されました](built-in-support-for-winrt-removed.md)。 しかし、<xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> インターフェイスへのキャストが誤って見落とされました。 ランタイムの基になるサポートが存在しなくなったため、<xref:System.PlatformNotSupportedException> をスローすると、正常なエラー パスが有効になります。 また、例外をスローすることで、この機能がサポートされなくなったことが見つけやすくなります。

## <a name="recommended-action"></a>推奨アクション

- Windows ランタイムメタデータ (WinMD) ファイルでインターフェイスを定義できる場合は、代わりに C#/WinRT ツールを使用します。

- それ以外の場合は、<xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> ではなく <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> としてインターフェイスをマークし、<xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> メソッドのインターフェイスの先頭に 3 つのダミー エントリを追加します。 次のコード スニペットに例を示します。

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

### Category

Interop

-->
