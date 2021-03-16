---
title: '破壊的変更: TripleDES.Create で作成されるインスタンスの既定の FeedbackSize 値の変更'
description: .NET 5 での破壊的変更について学習します。この変更により、TripleDES.Create() から返される TripleDES インスタンス上の FeedbackSize プロパティの既定値は、64 から 8 に変更されました。
ms.date: 10/16/2020
ms.openlocfilehash: 9d3259da30cce84e83a3f13c610dad5884b445b8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256765"
---
# <a name="default-feedbacksize-value-for-instances-created-by-tripledescreate-changed"></a>TripleDES.Create で作成されるインスタンスの既定の FeedbackSize 値の変更

<xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> から返される <xref:System.Security.Cryptography.TripleDES> インスタンスの <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> プロパティの既定値が 64 から 8 に変更され、.NET Framework からの移行がより簡単になりました。 このプロパティは、呼び出し元のコードで直接使用されていない限り、<xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> プロパティが <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>場合にのみ使用されます。

<xref:System.Security.Cryptography.CipherMode.CFB> モードのサポートは最初に 5.0 RC1 リリース用の .NET に追加されたため、この変更の影響を受けるのは .NET 5 RC1 および .NET 5 RC2 アプリケーションのみであるはずです。

## <a name="change-description"></a>変更内容

.Net Core と以前のプレリリース バージョンの .NET 5 では、`TripleDES.Create().FeedbackSize` の既定値は 64 です。 RTM バージョンの .NET 5 以降では、`TripleDES.Create().FeedbackSize` の既定値は 8 です。

## <a name="reason-for-change"></a>変更理由

.NET Framework によって、<xref:System.Security.Cryptography.TripleDES> 基底クラスの <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> の値は既定で 64 に設定されますが、<xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> クラスの既定値は 8 に上書きされます。 バージョン 2.0 で <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> プロパティが .NET Core に導入されたときに、同じ動作が維持されました。 しかし、.NET Framework では、<xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> から <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> のインスタンスが返されるため、アルゴリズム ファクトリの既定値は 8 となります。 .NET Core および .NET 5 以降の場合、アルゴリズム ファクトリからパブリックではない実装が返されます。これまで、その既定値は 64 でした。

<xref:System.Security.Cryptography.TripleDES> 実装クラスの <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> の値を 8 に変更すると、暗号モードを <xref:System.Security.Cryptography.CipherMode.CFB> として指定していても、<xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> プロパティを明示的に代入していない .NET Framework 用に作成されたアプリケーションは、引き続き .NET 5 で機能できます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

RC1 または RC2 バージョンの .NET 5 でデータの暗号化またはその解除を行うアプリケーションにより、次の条件が満たされたときに CFB64 を使用して操作が行われます。

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> の <xref:System.Security.Cryptography.TripleDES> インスタンスを使用する。
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> に既定値を使用する。
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> プロパティが <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> に設定されている。

この動作を維持するには、<xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> プロパティを `64` に代入します。

すべての `TripleDES` 実装で、<xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> に同じ既定値が使用されるわけではありません。 <xref:System.Security.Cryptography.TripleDES> インスタンスで <xref:System.Security.Cryptography.CipherMode.CFB> 暗号モードを使用する場合は、常に <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> プロパティ値を明示的に代入することをお勧めします。

```csharp
TripleDES cipher = TripleDES.Create();
cipher.Mode = CipherMode.CFB;
// Explicitly set the FeedbackSize for CFB to control between CFB8 and CFB64.
cipher.FeedbackSize = 8;
```

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Security.Cryptography.TripleDES.Create`
- `P:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize`

### Category

- Cryptography

-->
