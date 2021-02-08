---
description: '詳細については、「方法: サービスエンドポイントからメタデータをエクスポートする」を参照してください。'
title: '方法: メタデータをサービス エンドポイントからエクスポートする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: f690d2dc0bd3ac0f89e527412a63ce0967daa8f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802880"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="4a81e-103">方法: メタデータをサービス エンドポイントからエクスポートする</span><span class="sxs-lookup"><span data-stu-id="4a81e-103">How to: Export Metadata from Service Endpoints</span></span>

<span data-ttu-id="4a81e-104">このトピックでは、メタデータをサービス エンドポイントからエクスポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4a81e-104">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="4a81e-105">メタデータをサービス エンドポイントからエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="4a81e-105">To export metadata from service endpoints</span></span>  
  
1. <span data-ttu-id="4a81e-106">新しい Visual Studio コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a81e-106">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="4a81e-107">以下の手順で示されているコードを、生成された Program.cs ファイルの main() メソッド内に追加します。</span><span class="sxs-lookup"><span data-stu-id="4a81e-107">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2. <span data-ttu-id="4a81e-108"><xref:System.ServiceModel.Description.WsdlExporter> を作成します。</span><span class="sxs-lookup"><span data-stu-id="4a81e-108">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. <span data-ttu-id="4a81e-109"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティを <xref:System.ServiceModel.Description.PolicyVersion> 列挙体のいずれかの値に設定します。</span><span class="sxs-lookup"><span data-stu-id="4a81e-109">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="4a81e-110">この例では、値を、WS-Policy 1.5 に対応する <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> に設定します。</span><span class="sxs-lookup"><span data-stu-id="4a81e-110">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. <span data-ttu-id="4a81e-111"><xref:System.ServiceModel.Description.ServiceEndpoint> オブジェクトの配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="4a81e-111">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. <span data-ttu-id="4a81e-112">サービス エンドポイントのメタデータをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="4a81e-112">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. <span data-ttu-id="4a81e-113">エクスポート プロセス中にエラーが発生していないことを確認し、メタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="4a81e-113">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. <span data-ttu-id="4a81e-114">これで、メタデータを使用できます。たとえば、<xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> メソッドを呼び出してメタデータをファイルに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="4a81e-114">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a81e-115">例</span><span class="sxs-lookup"><span data-stu-id="4a81e-115">Example</span></span>  

 <span data-ttu-id="4a81e-116">この例の完全なコードの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="4a81e-116">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4a81e-117">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="4a81e-117">Compiling the Code</span></span>  

 <span data-ttu-id="4a81e-118">Program.cs をコンパイルするときは、System.ServiceModel.dll への参照を追加してください。</span><span class="sxs-lookup"><span data-stu-id="4a81e-118">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a81e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a81e-119">See also</span></span>

- [<span data-ttu-id="4a81e-120">メタデータ アーキテクチャの概要</span><span class="sxs-lookup"><span data-stu-id="4a81e-120">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="4a81e-121">メタデータを使用する</span><span class="sxs-lookup"><span data-stu-id="4a81e-121">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="4a81e-122">エンドポイント:アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="4a81e-122">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
