---
title: '方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする'
description: Svcutil.exe を使用して、実行中のサービスからメタデータをダウンロードし、メタデータをローカル ファイルに保存する方法について説明します。
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 449dd3023b5d688ed0de22e3651cccf16bee0c52
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280677"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする

Svcutil.exe を使用すると、実行中のサービスからメタデータをダウンロードして、ローカル ファイルに保存できます。 URL スキームが HTTP および HTTPS の場合は、Svcutil.exe により、メタデータの抽出に WS-MetadataExchange および [XML Web サービス検索](/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))の使用が試行されます。 その他の URL スキームの場合、Svcutil.exe は WS-MetadataExchange のみを使用します。  
  
 既定で、Svcutil.exe は <xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスに定義されているバインディングを使用します。 WS-MetadataExchange で使用するバインディングを構成するには、Svcutil.exe の構成ファイル (svcutil.exe.config) でクライアント エンドポイントを定義する必要があります。このとき、クライアント エンドポイントが `IMetadataExchange` コントラクトを使用し、メタデータ エンドポイントのアドレスの URI (Uniform Resource Identifier) スキームと同じ名前を持つように定義します。  
  
> [!CAUTION]
> Svcutil.exe を実行して、それぞれに同じ名前の操作が含まれている 2 つの異なるサービス コントラクトを公開するサービスのメタデータを取得すると、Svcutil.exe により、"... からメタデータを取得できません" というエラーが表示されます。たとえば、`Get(Car c)` 操作を含む `ICarService` という名前のサービス コントラクトを公開するサービスがあり、その同じサービスにより、`Get(Book b)` 操作を含む `IBookService` という名前のサービス コントラクトが公開される場合などです。 この問題を回避するには、次のいずれかのようにします。
>
> - 操作の名前を変更する。
> - <xref:System.ServiceModel.OperationContractAttribute.Name%2A> を別の名前に設定する。
> - <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティを使用して、操作の名前空間のいずれかを別の名前空間に設定する。
  
## <a name="to-download-metadata-using-svcutilexe"></a>Svcutil.exe を使用してメタデータをダウンロードするには  
  
1. 次の場所で Svcutil.exe ツールを検索します。  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2. コマンド プロンプトで、次の形式を使用してツールを起動します。  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     メタデータをダウンロードするには `/t:metadata` オプションを指定する必要があります。 このオプションを指定しないと、クライアントのコードと構成が生成されます。  
  
3. <`url`> 引数には、メタデータを提供するサービス エンドポイントまたはオンラインにホストされているメタデータ ドキュメントの URL を指定します。 <`epr`> 引数には、WS-MetadataExchange をサポートするサービス エンドポイント用の WS-Addressing `EndpointAddress` が含まれる XML ファイルへのパスを指定します。  
  
 メタデータのダウンロードにこのツールを使用する方法の詳細については、「[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)」を参照してください。  
  
## <a name="example"></a>例  

 次のコマンドにより、実行中のサービスからメタデータ ドキュメントがダウンロードされます。  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>関連項目

- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
