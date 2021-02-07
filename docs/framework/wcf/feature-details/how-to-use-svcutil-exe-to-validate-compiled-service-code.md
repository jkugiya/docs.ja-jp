---
description: '詳細については、「方法: Svcutil.exe を使用してコンパイル済みサービスコードを検証する」を参照してください。'
title: '方法: Svcutil.exe を使用してコンパイル済みサービス コードを検証する'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: b68cdeb61ac1f42cacdcf7d1468623acb8542abe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734166"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="3fbbc-103">方法: Svcutil.exe を使用してコンパイル済みサービス コードを検証する</span><span class="sxs-lookup"><span data-stu-id="3fbbc-103">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>

<span data-ttu-id="3fbbc-104">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、サービスをホストせずにサービスの実装と構成のエラーを検出することができます。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-104">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="3fbbc-105">サービスを検証するには</span><span class="sxs-lookup"><span data-stu-id="3fbbc-105">To validate a service</span></span>  
  
1. <span data-ttu-id="3fbbc-106">サービスを実行可能ファイルおよび 1 つ以上の依存アセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-106">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2. <span data-ttu-id="3fbbc-107">SDK コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-107">Open an SDK command prompt</span></span>  
  
3. <span data-ttu-id="3fbbc-108">コマンド プロンプトで、次の形式を使用して Svcutil.exe ツールを起動します。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-108">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="3fbbc-109">さまざまなパラメーターの詳細については、「 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 」の「サービスの検証」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-109">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```console
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="3fbbc-110">`/serviceName` オプションを使用して、検証するサービスの構成名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-110">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="3fbbc-111">`assemblyPath` 引数には、検証対象のサービスの実行可能ファイルへのパス、およびサービス型を格納している 1 つ以上のアセンブリへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-111">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="3fbbc-112">実行可能アセンブリに、サービス構成を提供する関連構成ファイルが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-112">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="3fbbc-113">標準のコマンドライン ワイルドカードを使用して、複数のアセンブリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-113">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fbbc-114">例</span><span class="sxs-lookup"><span data-stu-id="3fbbc-114">Example</span></span>  

 <span data-ttu-id="3fbbc-115">次のコマンドでは、myServiceHost.exe 実行可能ファイルに実装されたサービス myServiceName を検証します。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-115">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="3fbbc-116">サービスの構成ファイル (myServiceHost.exe.config) は自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-116">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```console  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fbbc-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fbbc-117">See also</span></span>

- [<span data-ttu-id="3fbbc-118">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="3fbbc-118">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
