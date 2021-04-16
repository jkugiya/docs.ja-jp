---
description: '詳細情報: <bindings>'
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 2cf5b42b8478e34a528cd36435023cac62bf0c1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639381"
---
# \<bindings>

<span data-ttu-id="85270-102">`bindings` 要素を使用すると、Windows Communication Foundation (WCF) の標準バインディングとカスタム バインディングのコレクションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="85270-102">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="85270-103">各エントリは、その一意の `binding` 属性で識別できる `name` 要素です。</span><span class="sxs-lookup"><span data-stu-id="85270-103">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="85270-104">サービスは、`name` を使用してバインディングをリンクすることにより、バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="85270-104">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="85270-105">.NET Framework 4 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="85270-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="85270-106">既定の構成と、名前のないバインディングと動作については、「[簡略化された構成](../../../wcf/simplified-configuration.md)」と「[WCF サービスの簡略化された構成](../../../wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85270-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="system-provided-bindings"></a><span data-ttu-id="85270-107">システム指定のバインド</span><span class="sxs-lookup"><span data-stu-id="85270-107">System-provided bindings</span></span>

<span data-ttu-id="85270-108">システム指定のバインディングは、WCF メッセージ スタックの複雑さを隠蔽します。</span><span class="sxs-lookup"><span data-stu-id="85270-108">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="85270-109">システム指定のバインディングを使用しているアプリケーションは、スタックを完全に制御する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="85270-109">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="85270-110">システム指定の各バインディングに公開される属性は、バインディングが処理する使用シナリオに最適な属性です。</span><span class="sxs-lookup"><span data-stu-id="85270-110">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>

<span data-ttu-id="85270-111">システム指定の各バインディングの構成セクションは、バインディングの構成に使用される複数の構成を定義できます。</span><span class="sxs-lookup"><span data-stu-id="85270-111">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="85270-112">各構成は、一意の名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="85270-112">Each configuration is identified by a unique name.</span></span>

<span data-ttu-id="85270-113">要素または属性をシステム指定のバインディングに追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="85270-113">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="85270-114">追加するには、「[カスタム バインド](#custom-bindings)」セクションで説明するように、カスタム バインドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85270-114">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="85270-115">システム指定のバインディングを完全に再現し、ユーザー アプリケーションで制御するいくつかの設定を追加するカスタム バインドを定義できます。</span><span class="sxs-lookup"><span data-stu-id="85270-115">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  

<span data-ttu-id="85270-116">システム指定のバインディングの一覧については、「[システム指定のバインディング](../../../wcf/system-provided-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85270-116">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="85270-117">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="85270-117">Custom bindings</span></span>

<span data-ttu-id="85270-118">カスタム バインディングを使用すると、WCF メッセージ スタックのフル コントロールが可能になります。</span><span class="sxs-lookup"><span data-stu-id="85270-118">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="85270-119">個別のバインディングは、メッセージ スタックを、スタック要素の構成要素をスタックに出現する順序で指定することにより定義します。</span><span class="sxs-lookup"><span data-stu-id="85270-119">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="85270-120">各要素は、スタック内の 1 つの要素を定義および構成します。</span><span class="sxs-lookup"><span data-stu-id="85270-120">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="85270-121">各カスタム バインディング内の `transport` 要素は 1 つだけにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="85270-121">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="85270-122">この要素がない場合、メッセージ スタックは不完全です。</span><span class="sxs-lookup"><span data-stu-id="85270-122">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="85270-123">要素がスタックに出現する順序は重要です。それは、その順序で操作がメッセージに適用されるためです。</span><span class="sxs-lookup"><span data-stu-id="85270-123">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="85270-124">スタック要素で必要な順序を次に示します。</span><span class="sxs-lookup"><span data-stu-id="85270-124">The required order of stack elements is the following:</span></span>  

1. <span data-ttu-id="85270-125">トランザクション (省略可能)</span><span class="sxs-lookup"><span data-stu-id="85270-125">Transactions (optional)</span></span>  

2. <span data-ttu-id="85270-126">リライアブル メッセージ機能 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="85270-126">Reliable messaging (optional)</span></span>  

3. <span data-ttu-id="85270-127">セキュリティ (省略可能)</span><span class="sxs-lookup"><span data-stu-id="85270-127">Security (optional)</span></span>  

4. <span data-ttu-id="85270-128">エンコーダー</span><span class="sxs-lookup"><span data-stu-id="85270-128">Encoder</span></span>  

5. <span data-ttu-id="85270-129">トランスポート</span><span class="sxs-lookup"><span data-stu-id="85270-129">Transport</span></span>  

 <span data-ttu-id="85270-130">カスタム バインドは、`name` 属性によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="85270-130">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="85270-131">カスタム バインディングの詳細については、「[カスタム バインディング](../../../wcf/extending/custom-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85270-131">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85270-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="85270-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [<span data-ttu-id="85270-133">バインド</span><span class="sxs-lookup"><span data-stu-id="85270-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="85270-134">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="85270-134">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
