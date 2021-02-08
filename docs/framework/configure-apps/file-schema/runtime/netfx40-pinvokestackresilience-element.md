---
description: '詳細については、次を参照してください: <NetFx40_PInvokeStackResilience> 要素'
title: <NetFx40_PInvokeStackResilience> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 59e2a5845868ebfa186344c9a731871739a29c47
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782300"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="875d1-103">\<NetFx40_PInvokeStackResilience> 要素</span><span class="sxs-lookup"><span data-stu-id="875d1-103">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="875d1-104">ランタイムが実行時の不適切なプラットフォーム呼び出し宣言を自動的に修正するかどうかを指定します。これにより、マネージド コードとアンマネージド コード間の遷移が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="875d1-104">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**  

## <a name="syntax"></a><span data-ttu-id="875d1-105">構文</span><span class="sxs-lookup"><span data-stu-id="875d1-105">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="875d1-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="875d1-106">Attributes and Elements</span></span>

<span data-ttu-id="875d1-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="875d1-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="875d1-108">属性</span><span class="sxs-lookup"><span data-stu-id="875d1-108">Attributes</span></span>

|<span data-ttu-id="875d1-109">属性</span><span class="sxs-lookup"><span data-stu-id="875d1-109">Attribute</span></span>|<span data-ttu-id="875d1-110">説明</span><span class="sxs-lookup"><span data-stu-id="875d1-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="875d1-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="875d1-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="875d1-112">ランタイムが無効なプラットフォーム呼び出し宣言を検出し、実行時に32ビットプラットフォームで自動的にスタックを修正するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="875d1-112">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="875d1-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="875d1-113">enabled Attribute</span></span>

|<span data-ttu-id="875d1-114">値</span><span class="sxs-lookup"><span data-stu-id="875d1-114">Value</span></span>|<span data-ttu-id="875d1-115">説明</span><span class="sxs-lookup"><span data-stu-id="875d1-115">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="875d1-116">ランタイムは、.NET Framework 4 で導入された高速な相互運用マーシャリングアーキテクチャを使用します。これは、不適切なプラットフォーム呼び出し宣言を検出して修正するものではありません。</span><span class="sxs-lookup"><span data-stu-id="875d1-116">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="875d1-117">既定値です。</span><span class="sxs-lookup"><span data-stu-id="875d1-117">This is the default.</span></span>|
|`1`|<span data-ttu-id="875d1-118">ランタイムは、不適切なプラットフォーム呼び出し宣言を検出して修正する低速の遷移を使用します。</span><span class="sxs-lookup"><span data-stu-id="875d1-118">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="875d1-119">子要素</span><span class="sxs-lookup"><span data-stu-id="875d1-119">Child Elements</span></span>

<span data-ttu-id="875d1-120">なし。</span><span class="sxs-lookup"><span data-stu-id="875d1-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="875d1-121">親要素</span><span class="sxs-lookup"><span data-stu-id="875d1-121">Parent Elements</span></span>

|<span data-ttu-id="875d1-122">要素</span><span class="sxs-lookup"><span data-stu-id="875d1-122">Element</span></span>|<span data-ttu-id="875d1-123">説明</span><span class="sxs-lookup"><span data-stu-id="875d1-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="875d1-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="875d1-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="875d1-125">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="875d1-125">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="875d1-126">解説</span><span class="sxs-lookup"><span data-stu-id="875d1-126">Remarks</span></span>

<span data-ttu-id="875d1-127">この要素を使用すると、不適切なプラットフォーム呼び出し宣言に対して実行時の回復性を高めるために、高速な相互運用マーシャリングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="875d1-127">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="875d1-128">.NET Framework 4 以降では、合理化された相互運用マーシャリングアーキテクチャにより、マネージコードからアンマネージコードへの遷移で大幅なパフォーマンスが向上しています。</span><span class="sxs-lookup"><span data-stu-id="875d1-128">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="875d1-129">以前のバージョンの .NET Framework では、マーシャリング層が32ビットプラットフォームで正しくないプラットフォーム呼び出し宣言を検出し、自動的にスタックを修正しました。</span><span class="sxs-lookup"><span data-stu-id="875d1-129">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="875d1-130">新しいマーシャリングアーキテクチャでは、この手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="875d1-130">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="875d1-131">その結果、遷移は非常に高速になりますが、不適切なプラットフォーム呼び出しの宣言によってプログラムエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="875d1-131">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="875d1-132">開発中に不適切な宣言を簡単に検出できるように、Visual Studio のデバッグエクスペリエンスが改善されました。</span><span class="sxs-lookup"><span data-stu-id="875d1-132">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="875d1-133">デバッガーがアタッチされた状態でアプリケーションを実行すると、 [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed デバッグアシスタント (MDA) によって、不適切なプラットフォーム呼び出し宣言が通知されます。</span><span class="sxs-lookup"><span data-stu-id="875d1-133">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="875d1-134">再コンパイルできないコンポーネントをアプリケーションで使用していて、無効なプラットフォーム呼び出し宣言を持つシナリオに対処するには、要素を使用でき `NetFx40_PInvokeStackResilience` ます。</span><span class="sxs-lookup"><span data-stu-id="875d1-134">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="875d1-135">この要素をアプリケーション構成ファイルに追加するには、 `enabled="1"` 以前のバージョンの .NET Framework の動作で互換性モードを使用します。これにより、移行速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="875d1-135">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="875d1-136">以前のバージョンの .NET Framework に対してコンパイルされたアセンブリは、自動的にこの互換モードに設定され、この要素は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="875d1-136">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="875d1-137">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="875d1-137">Configuration File</span></span>

<span data-ttu-id="875d1-138">この要素は、アプリケーション構成ファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="875d1-138">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="875d1-139">例</span><span class="sxs-lookup"><span data-stu-id="875d1-139">Example</span></span>

<span data-ttu-id="875d1-140">次の例では、マネージコードとアンマネージコードの間の遷移が低速であるため、アプリケーションの不適切なプラットフォーム呼び出し宣言に対して高度な復元を選択する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="875d1-140">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="875d1-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="875d1-141">See also</span></span>

- [<span data-ttu-id="875d1-142">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="875d1-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="875d1-143">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="875d1-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="875d1-144">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="875d1-144">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
