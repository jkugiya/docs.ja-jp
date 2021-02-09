---
description: '詳細情報: データ サービス クライアント ライブラリの生成 (WCF Data Services)'
title: データ サービス クライアント ライブラリの生成 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 3bac2459044ff910c8085ff56e60d9da6e0ba877
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765933"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="e906e-103">データ サービス クライアント ライブラリの生成 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="e906e-103">Generating the Data Service Client Library (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="e906e-104">Open Data Protocol (OData) が実装されているデータ サービスでは、OData フィードによって公開されているデータ モデルが記述されたサービス メタデータ ドキュメントが返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="e906e-104">A data service that implements the Open Data Protocol (OData) can return a service metadata document that describes the data model exposed by the OData feed.</span></span> <span data-ttu-id="e906e-105">詳細については、「サービス メタデータ ドキュメント」セクション ([OData の概要](https://www.odata.org/documentation/odata-version-2-0/overview/)に関する記事) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e906e-105">For more information, see the Service Metadata Document section in the [OData: Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) article.</span></span> <span data-ttu-id="e906e-106">Visual Studio の **[サービス参照の追加]** ダイアログを使用して、参照を OData ベースのサービスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="e906e-106">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an OData-based service.</span></span> <span data-ttu-id="e906e-107">このツールを使用してクライアント プロジェクト内の OData によって返されるメタデータに参照を追加すると、次のアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="e906e-107">When you use this tool to add a reference to the metadata returned by an OData feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="e906e-108">データ サービスからのサービス メタデータ ドキュメントが要求され、返されたメタデータが解釈されます。</span><span class="sxs-lookup"><span data-stu-id="e906e-108">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e906e-109">返されたメタデータは、クライアント プロジェクトに .edmx ファイルとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="e906e-109">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="e906e-110">.edmx ファイルは、Entity Framework で使用される .edmx ファイルと形式が異なるので、Entity Data Model デザイナーを使用して開くことができません。</span><span class="sxs-lookup"><span data-stu-id="e906e-110">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="e906e-111">このメタデータ ファイルは、XML エディターまたは任意のテキスト エディターを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="e906e-111">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="e906e-112">詳細については、「[\[MC-EDMX\]: データ サービス パッケージング形式の Entity Data Model](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e906e-112">For more information, see [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16).</span></span>
  
- <span data-ttu-id="e906e-113"><xref:System.Data.Services.Client.DataServiceContext> から継承するエンティティ コンテナー クラスとしてサービスの表現が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e906e-113">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="e906e-114">この生成されたエンティティ コンテナー クラスは、Entity Data Model ツールが生成するエンティティ コンテナーに似ています。</span><span class="sxs-lookup"><span data-stu-id="e906e-114">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="e906e-115">詳細は、[Object Services の概要 (Entity Framework)](/previous-versions/bb386871(v=vs.100)) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e906e-115">For more information, see [Object Services Overview (Entity Framework)](/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="e906e-116">サービス メタデータ内で見つかったデータ モデル型のデータ クラスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="e906e-116">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="e906e-117">`System.Data.Services.Client` アセンブリへの参照がプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e906e-117">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="e906e-118">詳細については、[データ サービス参照を追加する](how-to-add-a-data-service-reference-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e906e-118">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="e906e-119">クライアント データ サービス クラスは、コマンド プロンプトで [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) ツールを使用して生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e906e-119">The client data service classes can also be generated by using the [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="e906e-120">詳細については、[クライアント データ サービス クラスを手動で生成する](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e906e-120">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="e906e-121">クライアント データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="e906e-121">Client Data Type Mapping</span></span>  

 <span data-ttu-id="e906e-122">Visual Studio の **[サービス参照の追加]** ダイアログまたは `DataSvcUtil.exe` ツールを使用して、OData フィードに基づいてクライアント データ クラスを生成する場合、次のように .NET Framework データ型がデータ モデルのプリミティブ型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="e906e-122">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an OData feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="e906e-123">データ モデル型</span><span class="sxs-lookup"><span data-stu-id="e906e-123">Data model type</span></span>|<span data-ttu-id="e906e-124">.NET Framework データ型</span><span class="sxs-lookup"><span data-stu-id="e906e-124">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="e906e-125"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="e906e-125"><xref:System.Byte> `[]`</span></span>|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 <span data-ttu-id="e906e-126">詳細については、「プリミティブ データ型」セクション ([OData の概要](https://www.odata.org/documentation/odata-version-2-0/overview/)に関する記事) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e906e-126">For more information, see the Primitive Data Types section in the [OData: Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) article.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e906e-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="e906e-127">See also</span></span>

- [<span data-ttu-id="e906e-128">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e906e-128">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="e906e-129">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="e906e-129">Quickstart</span></span>](quickstart-wcf-data-services.md)
