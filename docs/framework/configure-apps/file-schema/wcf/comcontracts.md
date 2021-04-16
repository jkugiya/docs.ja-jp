---
description: '詳細情報: <comContracts>'
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 263210b4499274fe009a6b1b1e46c1f09dd007ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638653"
---
# \<comContracts>

`comContracts` 構成セクションには、COM+ 統合サービス コントラクトのさまざまなプロパティを指定できる要素が含まれます。  
  
## <a name="specifying-namespace-and-contract"></a>名前空間およびコントラクトの指定  

 COM+ 統合サービス コントラクトは、現在 `http://tempuri.org` 名前空間に制限されており、コントラクト名はサポートする COM インターフェイスから派生します。 ただし、構成ファイルの `comContracts` セクションを使用して候補を指定することができます。  
  
 たとえば、次の構成を使用して、サービス コントラクトの名前空間とコントラクト名、およびセッションの多いバインディングで使用させるオプションを指定できます。  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 サービスが初期化される場合、指定した名前空間およびコントラクト名が、生成されるサービスの説明に適用されます。  
  
 このセクションが空の場合、サービスの初期化によって、サポートしている COM インターフェイス ID から取得された既定の名前空間およびコントラクト名が適用されます。  
  
 また、[\<exposedMethod>](exposedmethod.md) 要素を使用して、COM+ コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM+ メソッドを指定できます。 さらに、[\<persistableTypes>](persistabletypes.md) を使用して、統合で使用される永続型も指定できます。 最後に、[\<userDefinedType>](userdefinedtype.md) 要素を使用して、サービス コントラクトに組み込まれるユーザー定義型 (UDT) を含めることができます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [COM+ アプリケーションとの統合](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [方法: COM+ サービス設定を構成する](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
