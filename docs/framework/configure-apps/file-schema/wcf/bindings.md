---
description: '詳細情報: <bindings>'
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 2cf5b42b8478e34a528cd36435023cac62bf0c1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639381"
---
# \<bindings>

`bindings` 要素を使用すると、Windows Communication Foundation (WCF) の標準バインディングとカスタム バインディングのコレクションを構成できます。 各エントリは、その一意の `binding` 属性で識別できる `name` 要素です。 サービスは、`name` を使用してバインディングをリンクすることにより、バインディングを使用します。 .NET Framework 4 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と、名前のないバインディングと動作については、「[簡略化された構成](../../../wcf/simplified-configuration.md)」と「[WCF サービスの簡略化された構成](../../../wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。

## <a name="system-provided-bindings"></a>システム指定のバインド

システム指定のバインディングは、WCF メッセージ スタックの複雑さを隠蔽します。 システム指定のバインディングを使用しているアプリケーションは、スタックを完全に制御する必要はありません。 システム指定の各バインディングに公開される属性は、バインディングが処理する使用シナリオに最適な属性です。

システム指定の各バインディングの構成セクションは、バインディングの構成に使用される複数の構成を定義できます。 各構成は、一意の名前によって識別されます。

要素または属性をシステム指定のバインディングに追加することはできません。 追加するには、「[カスタム バインド](#custom-bindings)」セクションで説明するように、カスタム バインドを実装する必要があります。 システム指定のバインディングを完全に再現し、ユーザー アプリケーションで制御するいくつかの設定を追加するカスタム バインドを定義できます。  

システム指定のバインディングの一覧については、「[システム指定のバインディング](../../../wcf/system-provided-bindings.md)」を参照してください。

## <a name="custom-bindings"></a>カスタム バインド

カスタム バインディングを使用すると、WCF メッセージ スタックのフル コントロールが可能になります。 個別のバインディングは、メッセージ スタックを、スタック要素の構成要素をスタックに出現する順序で指定することにより定義します。 各要素は、スタック内の 1 つの要素を定義および構成します。 各カスタム バインディング内の `transport` 要素は 1 つだけにする必要があります。 この要素がない場合、メッセージ スタックは不完全です。

要素がスタックに出現する順序は重要です。それは、その順序で操作がメッセージに適用されるためです。 スタック要素で必要な順序を次に示します。  

1. トランザクション (省略可能)  

2. リライアブル メッセージ機能 (省略可能)  

3. セキュリティ (省略可能)  

4. エンコーダー  

5. トランスポート  

 カスタム バインドは、`name` 属性によって識別されます。 カスタム バインディングの詳細については、「[カスタム バインディング](../../../wcf/extending/custom-bindings.md)」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [バインド](../../../wcf/bindings.md)
- [カスタム バインディング](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
