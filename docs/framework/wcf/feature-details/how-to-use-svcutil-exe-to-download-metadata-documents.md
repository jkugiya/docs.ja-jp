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
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="34960-103">方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="34960-103">How to: Use Svcutil.exe to Download Metadata Documents</span></span>

<span data-ttu-id="34960-104">Svcutil.exe を使用すると、実行中のサービスからメタデータをダウンロードして、ローカル ファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="34960-104">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="34960-105">URL スキームが HTTP および HTTPS の場合は、Svcutil.exe により、メタデータの抽出に WS-MetadataExchange および [XML Web サービス検索](/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))の使用が試行されます。</span><span class="sxs-lookup"><span data-stu-id="34960-105">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="34960-106">その他の URL スキームの場合、Svcutil.exe は WS-MetadataExchange のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="34960-106">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="34960-107">既定で、Svcutil.exe は <xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスに定義されているバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="34960-107">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="34960-108">WS-MetadataExchange で使用するバインディングを構成するには、Svcutil.exe の構成ファイル (svcutil.exe.config) でクライアント エンドポイントを定義する必要があります。このとき、クライアント エンドポイントが `IMetadataExchange` コントラクトを使用し、メタデータ エンドポイントのアドレスの URI (Uniform Resource Identifier) スキームと同じ名前を持つように定義します。</span><span class="sxs-lookup"><span data-stu-id="34960-108">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="34960-109">Svcutil.exe を実行して、それぞれに同じ名前の操作が含まれている 2 つの異なるサービス コントラクトを公開するサービスのメタデータを取得すると、Svcutil.exe により、"... からメタデータを取得できません" というエラーが表示されます。たとえば、`Get(Car c)` 操作を含む `ICarService` という名前のサービス コントラクトを公開するサービスがあり、その同じサービスにより、`Get(Book b)` 操作を含む `IBookService` という名前のサービス コントラクトが公開される場合などです。</span><span class="sxs-lookup"><span data-stu-id="34960-109">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="34960-110">この問題を回避するには、次のいずれかのようにします。</span><span class="sxs-lookup"><span data-stu-id="34960-110">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="34960-111">操作の名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="34960-111">Rename one of the operations.</span></span>
> - <span data-ttu-id="34960-112"><xref:System.ServiceModel.OperationContractAttribute.Name%2A> を別の名前に設定する。</span><span class="sxs-lookup"><span data-stu-id="34960-112">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="34960-113"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティを使用して、操作の名前空間のいずれかを別の名前空間に設定する。</span><span class="sxs-lookup"><span data-stu-id="34960-113">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="34960-114">Svcutil.exe を使用してメタデータをダウンロードするには</span><span class="sxs-lookup"><span data-stu-id="34960-114">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="34960-115">次の場所で Svcutil.exe ツールを検索します。</span><span class="sxs-lookup"><span data-stu-id="34960-115">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="34960-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="34960-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="34960-117">コマンド プロンプトで、次の形式を使用してツールを起動します。</span><span class="sxs-lookup"><span data-stu-id="34960-117">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="34960-118">メタデータをダウンロードするには `/t:metadata` オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34960-118">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="34960-119">このオプションを指定しないと、クライアントのコードと構成が生成されます。</span><span class="sxs-lookup"><span data-stu-id="34960-119">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="34960-120"><`url`> 引数には、メタデータを提供するサービス エンドポイントまたはオンラインにホストされているメタデータ ドキュメントの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="34960-120">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="34960-121"><`epr`> 引数には、WS-MetadataExchange をサポートするサービス エンドポイント用の WS-Addressing `EndpointAddress` が含まれる XML ファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="34960-121">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="34960-122">メタデータのダウンロードにこのツールを使用する方法の詳細については、「[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34960-122">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34960-123">例</span><span class="sxs-lookup"><span data-stu-id="34960-123">Example</span></span>  

 <span data-ttu-id="34960-124">次のコマンドにより、実行中のサービスからメタデータ ドキュメントがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="34960-124">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="34960-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="34960-125">See also</span></span>

- [<span data-ttu-id="34960-126">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="34960-126">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
