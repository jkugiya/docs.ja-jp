---
title: クライアント アプリケーションに UI オートメーション プロバイダーを実装する
description: アプリケーションでクライアント側 UI オートメーション プロバイダーを実装する方法の例を確認します。 これは、一般的ではないシナリオであることに注意してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: 486e05f9080b686c48454dfcfceaaa666fa57f67
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269588"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="e596a-104">クライアント アプリケーションに UI オートメーション プロバイダーを実装する</span><span class="sxs-lookup"><span data-stu-id="e596a-104">Implement UI Automation Providers in a Client Application</span></span>

> [!NOTE]
> <span data-ttu-id="e596a-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="e596a-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e596a-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e596a-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e596a-107">このトピックのコード例では、アプリケーション内のクライアント側 UI オートメーション プロバイダーを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e596a-107">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="e596a-108">これは、一般的ではないシナリオです。</span><span class="sxs-lookup"><span data-stu-id="e596a-108">This is an uncommon scenario.</span></span> <span data-ttu-id="e596a-109">通常は、UI オートメーション クライアント アプリケーションは、サーバー側プロバイダーを使用するか、または DLL 内に存在するクライアント側プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="e596a-109">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e596a-110">例</span><span class="sxs-lookup"><span data-stu-id="e596a-110">Example</span></span>  

 <span data-ttu-id="e596a-111">次のコード例では、コンソール ウィンドウ用の簡単なプロバイダーを実装します。</span><span class="sxs-lookup"><span data-stu-id="e596a-111">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="e596a-112">このコードは、有用な機能は備えていませんが、クライアント コード内でプロバイダーを設定し、 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>を使用して登録する際の基本的な手順を示すために用意されています。</span><span class="sxs-lookup"><span data-stu-id="e596a-112">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="e596a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e596a-113">See also</span></span>

- [<span data-ttu-id="e596a-114">UI オートメーション プロバイダーの概要</span><span class="sxs-lookup"><span data-stu-id="e596a-114">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="e596a-115">クライアント側プロバイダー アセンブリの登録</span><span class="sxs-lookup"><span data-stu-id="e596a-115">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="e596a-116">クライアント側 UI オートメーション プロバイダーの作成</span><span class="sxs-lookup"><span data-stu-id="e596a-116">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="e596a-117">クライアント側 UI オートメーション プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="e596a-117">Client-Side UI Automation Provider Implementation</span></span>](client-side-ui-automation-provider-implementation.md)
