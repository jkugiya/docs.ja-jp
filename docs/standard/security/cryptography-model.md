---
title: .NET 暗号化モデル
description: .NET における通常の暗号アルゴリズムの実装を確認します。 オブジェクトの継承、ストリームのデザイン、構成の拡張可能な暗号化モデルについて説明します。
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106931"
---
# <a name="net-cryptography-model"></a>.NET 暗号化モデル

.NET には、多くの標準的な暗号アルゴリズムの実装が用意されており、.NET 暗号化モデルは拡張可能です。

## <a name="object-inheritance"></a>オブジェクトの継承

.NET 暗号化システムは、拡張可能な派生クラス継承のパターンを実装しています。 階層は次のとおりです。

- <xref:System.Security.Cryptography.SymmetricAlgorithm>、<xref:System.Security.Cryptography.AsymmetricAlgorithm>、<xref:System.Security.Cryptography.HashAlgorithm> などのアルゴリズム型クラス。 このレベルは抽象レベルです。

- <xref:System.Security.Cryptography.Aes>、<xref:System.Security.Cryptography.RSA>、または <xref:System.Security.Cryptography.ECDiffieHellman> など、アルゴリズム型クラスから継承されるアルゴリズム クラス。 このレベルは抽象レベルです。

- <xref:System.Security.Cryptography.AesManaged>、<xref:System.Security.Cryptography.RC2CryptoServiceProvider>、または <xref:System.Security.Cryptography.ECDiffieHellmanCng> など、アルゴリズム クラスから継承されるアルゴリズム クラスの実装。 このレベルは完全に実装されます。

派生クラスのこのパターンを使用すると、新しいアルゴリズムの追加、または既存アルゴリズムの新規実装の追加を行うことができます。 たとえば、新しい公開キー アルゴリズムを作成するには、<xref:System.Security.Cryptography.AsymmetricAlgorithm> クラスから継承します。 特定のアルゴリズムの実装を新しく作成するには、そのアルゴリズムの非抽象派生クラスを作成します。

## <a name="how-algorithms-are-implemented-in-net"></a>.NET でのアルゴリズムの実装方法

アルゴリズムに使用できるさまざまな実装例として、対称アルゴリズムを検討します。 すべての対称アルゴリズムの基本は <xref:System.Security.Cryptography.SymmetricAlgorithm> です。これは、<xref:System.Security.Cryptography.Aes>、<xref:System.Security.Cryptography.TripleDES>、および推奨されなくなったその他のものによって継承されます。

<xref:System.Security.Cryptography.Aes> は、<xref:System.Security.Cryptography.AesCryptoServiceProvider>、<xref:System.Security.Cryptography.AesCng>、<xref:System.Security.Cryptography.AesManaged> により継承されます。

Windows 上の .NET Framework の場合:

* `*CryptoServiceProvider` アルゴリズム クラス (<xref:System.Security.Cryptography.AesCryptoServiceProvider> など) は、アルゴリズムの Windows Cryptography API (CAPI) 実装のラッパーです。
* `*Cng` アルゴリズム クラス (<xref:System.Security.Cryptography.ECDiffieHellmanCng> など) は、Windows Cryptography Next Generation (CNG) 実装のラッパーです。
* クラス <xref:System.Security.Cryptography.AesManaged> (`*Managed` など) は、すべてマネージド コードで記述されています。 `*Managed` は連邦情報処理規格 (FIPS: Federal Information Processing Standards) によって認定されておらず、`*CryptoServiceProvider` と `*Cng` ラッパー クラスよりも低速である場合があります。

.NET Core と .NET 5 以降のバージョンでは、すべての実装クラス (`*CryptoServiceProvider`、`*Managed`、`*Cng`) は、オペレーティング システム (OS) アルゴリズムのラッパーです。 OS アルゴリズムが FIPS によって認定されている場合、.NET は FIPS によって認定されたアルゴリズムを使用します。 詳細については、[クロスプラットフォーム暗号化](cross-platform-cryptography.md)に関するページをご覧ください。

ほとんどの場合、`AesCryptoServiceProvider` などのアルゴリズム実装クラスを直接参照する必要はありません。 通常、必要とされるメソッドとプロパティは、`Aes` などの基本アルゴリズム クラスにあります。 基本アルゴリズム クラスのファクトリ メソッドを使用して既定の実装クラスのインスタンスを作成し、基本アルゴリズム クラスを参照します。 たとえば、次の例で強調表示されているコード行をご確認ください。

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="20":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="17":::

## <a name="cryptographic-configuration"></a>暗号化の構成

暗号化の構成によって、アルゴリズムの特定の実装をアルゴリズム名に解決できるようになり、.NET 暗号化クラスの機能を拡張できます。 アルゴリズムの独自のハードウェアまたはソフトウェア実装を追加して、実装を任意のアルゴリズム名にマップすることができます。 構成ファイルでアルゴリズムを指定しない場合は、既定の設定が使用されます。

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
- [ASP.NET Core データ保護](/aspnet/core/security/data-protection/introduction)
