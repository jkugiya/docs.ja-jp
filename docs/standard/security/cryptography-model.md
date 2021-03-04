---
title: .NET 暗号化モデル
description: .NET での通常の暗号化アルゴリズムの実装を確認します。 オブジェクトの継承、ストリームのデザイン、& 構成の拡張可能な暗号化モデルについて説明します。
ms.date: 02/26/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], model
- encryption [.NET], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: 2208e36ac4521f43cfd2960d92588c8349a119ca
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106931"
---
# <a name="net-cryptography-model"></a>.NET 暗号化モデル

.NET には、多くの標準的な暗号化アルゴリズムの実装が用意されており、.NET 暗号化モデルは拡張可能です。

## <a name="object-inheritance"></a>オブジェクトの継承

.NET 暗号化システムは、派生クラスの継承の拡張可能なパターンを実装します。 階層は次のとおりです。

- アルゴリズムの種類クラス (、、など) <xref:System.Security.Cryptography.SymmetricAlgorithm>  <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.HashAlgorithm> 。 このレベルは抽象レベルです。

- <xref:System.Security.Cryptography.Aes>、<xref:System.Security.Cryptography.RSA>、または <xref:System.Security.Cryptography.ECDiffieHellman> など、アルゴリズム型クラスから継承されるアルゴリズム クラス。 このレベルは抽象レベルです。

- <xref:System.Security.Cryptography.AesManaged>、<xref:System.Security.Cryptography.RC2CryptoServiceProvider>、または <xref:System.Security.Cryptography.ECDiffieHellmanCng> など、アルゴリズム クラスから継承されるアルゴリズム クラスの実装。 このレベルは完全に実装されます。

この派生クラスのパターンを使用すると、新しいアルゴリズムを追加したり、既存のアルゴリズムの新しい実装を追加したりできます。 たとえば、新しい公開キー アルゴリズムを作成するには、<xref:System.Security.Cryptography.AsymmetricAlgorithm> クラスから継承します。 特定のアルゴリズムの実装を新しく作成するには、そのアルゴリズムの非抽象派生クラスを作成します。

## <a name="how-algorithms-are-implemented-in-net"></a>.NET でのアルゴリズムの実装方法

アルゴリズムに使用できるさまざまな実装例として、対称アルゴリズムを検討します。 すべての対称アルゴリズムの基本は、、 <xref:System.Security.Cryptography.SymmetricAlgorithm> <xref:System.Security.Cryptography.Aes> <xref:System.Security.Cryptography.TripleDES> 、および推奨されなくなった他のすべての対称アルゴリズムによって継承されます。

<xref:System.Security.Cryptography.Aes> は、、、およびによって継承され <xref:System.Security.Cryptography.AesCryptoServiceProvider> <xref:System.Security.Cryptography.AesCng> <xref:System.Security.Cryptography.AesManaged> ます。

Windows の .NET Framework:

* `*CryptoServiceProvider` アルゴリズムクラス (など) <xref:System.Security.Cryptography.AesCryptoServiceProvider> は、アルゴリズムの Windows CRYPTOGRAPHY API (CAPI) 実装のラッパーです。
* `*Cng` などのアルゴリズムクラス <xref:System.Security.Cryptography.ECDiffieHellmanCng> は、Windows Cryptography Next Generation (CNG) 実装のラッパーです。
* `*Managed` などのクラス <xref:System.Security.Cryptography.AesManaged> は、完全にマネージコードで記述されます。 `*Managed` 実装は、連邦情報処理規格 (FIPS) によって認定されていないため、およびラッパークラスよりも低速になる可能性があり `*CryptoServiceProvider` `*Cng` ます。

.NET Core と .NET 5 以降のバージョンでは、すべての実装クラス ( `*CryptoServiceProvider` 、 `*Managed` 、および `*Cng` ) は、オペレーティングシステム (os) アルゴリズムのラッパーです。 OS アルゴリズムが FIPS 認定の場合、.NET は FIPS 認定アルゴリズムを使用します。 詳細については、「 [クロスプラットフォーム暗号化](cross-platform-cryptography.md)」を参照してください。

ほとんどの場合、などのアルゴリズム実装クラスを直接参照する必要はありません `AesCryptoServiceProvider` 。 通常必要なメソッドとプロパティは、のような基本アルゴリズムクラスにあり `Aes` ます。 基本アルゴリズムクラスのファクトリメソッドを使用して、既定の実装クラスのインスタンスを作成し、基本アルゴリズムクラスを参照します。 たとえば、次の例で強調表示されているコード行を確認します。

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="20":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="17":::

## <a name="cryptographic-configuration"></a>暗号化の構成

暗号化の構成を使用すると、アルゴリズムの特定の実装をアルゴリズム名に解決して、.NET 暗号化クラスの機能拡張を可能にすることができます。 アルゴリズムの独自のハードウェアまたはソフトウェア実装を追加して、実装を任意のアルゴリズム名にマップすることができます。 構成ファイルでアルゴリズムを指定しない場合は、既定の設定が使用されます。

## <a name="choose-an-algorithm"></a>アルゴリズムの選択

データの整合性、データのプライバシー保護、またはキー生成など、さまざまな理由のためにアルゴリズムを選択することができます。 対称アルゴリズムおよびハッシュ アルゴリズムは、整合性の理由 (変更の防止) またはプライバシー上の理由 (表示の防止) のいずれかのためにデータを保護することを意図しています。 ハッシュ アルゴリズムは、主にデータの整合性用に使用されます。

アプリケーションで推奨されるアルゴリズムの一覧を示します。

- データのプライバシー : 
  - <xref:System.Security.Cryptography.Aes>
- データの整合性 : 
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- デジタル署名 : 
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- キー交換 : 
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- 乱数生成 : 
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- パスワードからのキー生成 :  
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>関連項目

- [Cryptographic Services](cryptographic-services.md)
- [クロスプラットフォーム暗号化](cross-platform-cryptography.md)
- [データ保護の ASP.NET Core](/aspnet/core/security/data-protection/introduction)
