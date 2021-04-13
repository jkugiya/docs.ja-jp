---
title: サーバー側 UI オートメーション プロバイダーの公開
description: System.Windows.Forms.Control ウィンドウでホストされているサーバー側 UI オートメーション プロバイダーを公開する方法を示す例を確認します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expose a server-side UI Automation provider
- UI Automation, server-side provider, exposing
- server-side UI Automation provider, exposing
ms.assetid: 55d419c0-2201-4101-90c9-2888df4dbb47
ms.openlocfilehash: be39130c7a91fc081256bf14a87f503d27f45129
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276530"
---
# <a name="expose-a-server-side-ui-automation-provider"></a><span data-ttu-id="2ffd6-103">サーバー側 UI オートメーション プロバイダーの公開</span><span class="sxs-lookup"><span data-stu-id="2ffd6-103">Expose a Server-side UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="2ffd6-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="2ffd6-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2ffd6-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2ffd6-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2ffd6-106">このトピックには、 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> ウィンドウにホストされているサーバー側 UI オートメーション プロバイダーを公開する方法を示すコード例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ffd6-106">This topic contains example code that shows how to expose a server-side UI Automation provider that is hosted in a <xref:System.Windows.Forms.Control?displayProperty=nameWithType> window.</span></span>  
  
 <span data-ttu-id="2ffd6-107">この例は、WM_GETOBJECT (クライアント アプリケーションがウィンドウに関する情報を要求したときに、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コア サービスによって送信されるメッセージ) をトラップするためのウィンドウ プロシージャをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="2ffd6-107">The example overrides the window procedure to trap WM_GETOBJECT, which is the message sent by the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core service when a client application requests information about the window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ffd6-108">例</span><span class="sxs-lookup"><span data-stu-id="2ffd6-108">Example</span></span>  

 [!code-csharp[UIAFragmentProvider_snip#116](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#116)]
 [!code-vb[UIAFragmentProvider_snip#116](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#116)]  
  
## <a name="see-also"></a><span data-ttu-id="2ffd6-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ffd6-109">See also</span></span>

- [<span data-ttu-id="2ffd6-110">UI オートメーション プロバイダーの概要</span><span class="sxs-lookup"><span data-stu-id="2ffd6-110">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="2ffd6-111">サーバー側 UI オートメーション プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="2ffd6-111">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
