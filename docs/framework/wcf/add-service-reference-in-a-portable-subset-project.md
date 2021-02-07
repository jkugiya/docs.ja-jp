---
description: 詳細については、「ポータブルサブセットプロジェクトでのサービス参照の追加」を参照してください。
title: ポータブル サブセット プロジェクトでサービス参照を追加する
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: 85c7c38c26481487b02c39917986c916ac31282f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677484"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="d9cfe-103">ポータブル サブセット プロジェクトでサービス参照を追加する</span><span class="sxs-lookup"><span data-stu-id="d9cfe-103">Add Service Reference in a Portable Subset Project</span></span>

<span data-ttu-id="d9cfe-104">ポータブルサブセットプロジェクトを使用すると、.NET アセンブリプログラマは、1つのソースツリーとビルドシステムを維持しながら、複数の .NET 実装 (デスクトップ、Silverlight、Windows Phone、Xbox) を引き続きサポートできます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-104">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and Xbox).</span></span> <span data-ttu-id="d9cfe-105">ポータブルサブセットプロジェクトは、任意の .NET 実装で使用できる .NET アセンブリであるポータブルライブラリのみを参照します。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-105">Portable subset projects only reference portable libraries that are .NET assemblies that can be used on any .NET implementation.</span></span>
  
## <a name="add-service-reference-details"></a><span data-ttu-id="d9cfe-106">サービス参照の追加の詳細</span><span class="sxs-lookup"><span data-stu-id="d9cfe-106">Add Service Reference Details</span></span>  

 <span data-ttu-id="d9cfe-107">ポータブル サブセット プロジェクトでサービス参照を追加する場合は、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-107">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1. <span data-ttu-id="d9cfe-108"><xref:System.Xml.Serialization.XmlSerializer> では、文字エンコーディングのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-108">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="d9cfe-109">SOAP エンコーディングを使用すると、インポート中にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-109">SOAP encodings generate an error during import.</span></span>  
  
2. <span data-ttu-id="d9cfe-110"><xref:System.Runtime.Serialization.DataContractSerializer> シナリオを使用するサービスの場合、再利用された型をポータブル サブセットからのみ受け取ることを確認するために、データ コントラクト サロゲートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-110">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3. <span data-ttu-id="d9cfe-111">ポータブル ライブラリでサポートされていないバインド (<xref:System.ServiceModel.BasicHttpBinding>、トランザクション フロー、信頼できるセッション、または MTOM エンコーディングがない <xref:System.ServiceModel.WSHttpBinding>、および等価のカスタム バインドを除くすべてのバインド) に依存するエンドポイントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-111">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4. <span data-ttu-id="d9cfe-112">メッセージ ヘッダーは、インポート前にすべての操作におけるすべてのメッセージの説明から削除されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-112">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5. <span data-ttu-id="d9cfe-113">非ポータブル属性 (<xref:System.ComponentModel.DesignerCategoryAttribute>、<xref:System.SerializableAttribute>、および <xref:System.ServiceModel.TransactionFlowAttribute>) は、生成されたクライアント プロキシ コードから削除されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-113">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6. <span data-ttu-id="d9cfe-114">非ポータブル プロパティ (ProtectionLevel、SessionMode、IsInitiating、IsTerminating) は、<xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.OperationContractAttribute>、および <xref:System.ServiceModel.FaultContractAttribute> から削除されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-114">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7. <span data-ttu-id="d9cfe-115">すべてのサービス操作は、クライアント プロキシ上で非同期操作として生成されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-115">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8. <span data-ttu-id="d9cfe-116">非ポータブル型を使用する生成済みのクライアント コンストラクターは削除されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-116">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="d9cfe-117"><xref:System.Net.CookieContainer> インスタンスは、生成されたクライアントで公開されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-117">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="d9cfe-118">コード ジェネレーターのアセンブリとバージョンを示すコメント "`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`" がファイルの先頭に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-118">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="d9cfe-119"><xref:System.Runtime.Serialization.ISerializable> インターフェイスはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-119">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="d9cfe-120">Net.Tcp および PollingDuplex バインドはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-120">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="d9cfe-121"><xref:System.Runtime.Serialization.DataContractSerializer> は常にエラーに対して使用されます。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-121">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="d9cfe-122">ポータブル サブセット プロジェクトでは <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d9cfe-122"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9cfe-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9cfe-123">See also</span></span>

- [<span data-ttu-id="d9cfe-124">WCF クライアントを使用したサービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="d9cfe-124">Accessing Services Using a WCF Client</span></span>](accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="d9cfe-125">ポータブル クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d9cfe-125">Portable Class Library</span></span>](../cross-platform/portable-class-library.md)
