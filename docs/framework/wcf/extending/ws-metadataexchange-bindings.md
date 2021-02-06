---
description: 詳細については、「WS-MetadataExchange バインド」を参照してください。
title: WS-MetadataExchange のバインディング
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 3bcea573ad436a85285fab5657e58defa9113d9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643944"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="f8adf-103">WS-MetadataExchange のバインディング</span><span class="sxs-lookup"><span data-stu-id="f8adf-103">WS-MetadataExchange Bindings</span></span>

<span data-ttu-id="f8adf-104">ここでは、既定のメタデータ交換バインディングを各種のトランスポート用に構築する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f8adf-104">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="f8adf-105">既定のバインディング</span><span class="sxs-lookup"><span data-stu-id="f8adf-105">The Default Bindings</span></span>  
  
|<span data-ttu-id="f8adf-106">既定のバインディング名</span><span class="sxs-lookup"><span data-stu-id="f8adf-106">Default Binding Name</span></span>|<span data-ttu-id="f8adf-107">バインディングを構築する方法</span><span class="sxs-lookup"><span data-stu-id="f8adf-107">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="f8adf-108">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f8adf-108">mexHttpBinding</span></span>|<span data-ttu-id="f8adf-109">トランスポート レベルのセキュリティが無効な <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="f8adf-109">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="f8adf-110">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="f8adf-110">mexHttpsBinding</span></span>|<span data-ttu-id="f8adf-111">トランスポート レベルのセキュリティをサポートする <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="f8adf-111">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="f8adf-112">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="f8adf-112">mexNamedPipeBinding</span></span>|<span data-ttu-id="f8adf-113"><xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="f8adf-113">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="f8adf-114">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="f8adf-114">mexTcpBinding</span></span>|<span data-ttu-id="f8adf-115"><xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="f8adf-115">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
