---
description: 詳細については、「メタデータシステムの拡張」を参照してください。
title: メタデータ システムの拡張
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: e8409e29f9dc604ccc6bf399497f3d48f3bcd8f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685557"
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="09a0a-103">メタデータ システムの拡張</span><span class="sxs-lookup"><span data-stu-id="09a0a-103">Extending the Metadata System</span></span>

<span data-ttu-id="09a0a-104">Windows Communication Foundation (WCF) メタデータシステムは、サービスベースのアプリケーションを実装するために必要なメタデータを表すクラスとインターフェイスのグループです。</span><span class="sxs-lookup"><span data-stu-id="09a0a-104">The Windows Communication Foundation (WCF) metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="09a0a-105">クラスを変更または拡張するか、WSDL (Web サービス記述言語) の拡張子やカスタム WS-PolicyAttachments アサーションなどのカスタム メタデータをエクスポート/インポートするインターフェイスを実装して構成します。</span><span class="sxs-lookup"><span data-stu-id="09a0a-105">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09a0a-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="09a0a-106">In This Section</span></span>  

 [<span data-ttu-id="09a0a-107">WCF 拡張に対するカスタム メタデータのエクスポート</span><span class="sxs-lookup"><span data-stu-id="09a0a-107">Exporting Custom Metadata for a WCF Extension</span></span>](exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="09a0a-108"><xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> インターフェイスを実装および使用して、カスタム ポリシー アサーションを WSDL ドキュメントに埋め込む方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="09a0a-108">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="09a0a-109">WCF 拡張に対するカスタム メタデータのインポート</span><span class="sxs-lookup"><span data-stu-id="09a0a-109">Importing Custom Metadata for a WCF Extension</span></span>](importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="09a0a-110"><xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> インターフェイスを実装および使用して、WSDL ドキュメント内のカスタム ポリシー アサーションの読み取りや応答を行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="09a0a-110">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="09a0a-111">カスタム バインディングを介したメタデータの公開と取得</span><span class="sxs-lookup"><span data-stu-id="09a0a-111">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="09a0a-112">カスタム バインドを介してメタデータを交換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="09a0a-112">Describes how to exchange metadata over custom bindings.</span></span>
