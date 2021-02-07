---
description: '詳細については、「方法: MetadataResolver を使用してバインディングメタデータを動的に取得する」を参照してください。'
title: '方法: MetadataResolver を使用してバインディング メタデータを動的に取得する'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 00f33b31504ede6868113040ba83b6f9462ee808
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734283"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="b388d-103">方法: MetadataResolver を使用してバインディング メタデータを動的に取得する</span><span class="sxs-lookup"><span data-stu-id="b388d-103">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>

<span data-ttu-id="b388d-104">ここでは、<xref:System.ServiceModel.Description.MetadataResolver> クラスを使用してバインディング メタデータを動的に取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b388d-104">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="b388d-105">バインディング メタデータを動的に取得するには</span><span class="sxs-lookup"><span data-stu-id="b388d-105">To dynamically obtain binding metadata</span></span>  
  
1. <span data-ttu-id="b388d-106">メタデータ エンドポイントのアドレスを持つ <xref:System.ServiceModel.EndpointAddress> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b388d-106">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. <span data-ttu-id="b388d-107">サービス型とメタデータ エンドポイント アドレスを渡して、<xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b388d-107">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="b388d-108">これにより、指定したコントラクトを実装したエンドポイントのコレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="b388d-108">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="b388d-109">メタデータからはバインディング情報のみがインポートされます。コントラクト情報はインポートされません。</span><span class="sxs-lookup"><span data-stu-id="b388d-109">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="b388d-110">提供されたコントラクトが代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="b388d-110">The supplied contract is used instead.</span></span>  
  
    ```csharp  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. <span data-ttu-id="b388d-111">これで、サービス エンドポイントのコレクションを反復処理して必要なバインディング情報を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="b388d-111">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="b388d-112">次のコードは、エンドポイントを反復処理し、現在のエンドポイントに関連付けられたバインディングとアドレスを渡すサービス クライアント オブジェクトを作成し、そのサービスでメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b388d-112">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
    ```csharp  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b388d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b388d-113">See also</span></span>

- [<span data-ttu-id="b388d-114">Metadata</span><span class="sxs-lookup"><span data-stu-id="b388d-114">Metadata</span></span>](metadata.md)
