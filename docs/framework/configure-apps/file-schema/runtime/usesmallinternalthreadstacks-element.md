---
description: '詳細情報: <UseSmallInternalThreadStacks> 要素'
title: <UseSmallInternalThreadStacks> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: eeb253025b32f862926c7315004b1854b8eef928
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639966"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="078a8-103">\<UseSmallInternalThreadStacks> 要素</span><span class="sxs-lookup"><span data-stu-id="078a8-103">\<UseSmallInternalThreadStacks> Element</span></span>

<span data-ttu-id="078a8-104">共通言語ランタイム (CLR) が、内部で使用する特定のスレッドを作成するときに明示的なスタックサイズを指定することによって、メモリの使用量を削減するように要求します。これらのスレッドの既定のスタックサイズは使用されません。</span><span class="sxs-lookup"><span data-stu-id="078a8-104">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a><span data-ttu-id="078a8-105">構文</span><span class="sxs-lookup"><span data-stu-id="078a8-105">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="078a8-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="078a8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="078a8-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="078a8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="078a8-108">属性</span><span class="sxs-lookup"><span data-stu-id="078a8-108">Attributes</span></span>  
  
|<span data-ttu-id="078a8-109">属性</span><span class="sxs-lookup"><span data-stu-id="078a8-109">Attribute</span></span>|<span data-ttu-id="078a8-110">説明</span><span class="sxs-lookup"><span data-stu-id="078a8-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="078a8-111">enabled</span><span class="sxs-lookup"><span data-stu-id="078a8-111">enabled</span></span>|<span data-ttu-id="078a8-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="078a8-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="078a8-113">内部で使用する特定のスレッドを作成するときに、CLR が既定のスタックサイズではなく明示的なスタックサイズを使用するように要求するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="078a8-113">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="078a8-114">明示的なスタックサイズは、既定のスタックサイズの 1 MB よりも小さくなっています。</span><span class="sxs-lookup"><span data-stu-id="078a8-114">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="078a8-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="078a8-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="078a8-116">値</span><span class="sxs-lookup"><span data-stu-id="078a8-116">Value</span></span>|<span data-ttu-id="078a8-117">説明</span><span class="sxs-lookup"><span data-stu-id="078a8-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="078a8-118">true</span><span class="sxs-lookup"><span data-stu-id="078a8-118">true</span></span>|<span data-ttu-id="078a8-119">明示的なスタックサイズを要求します。</span><span class="sxs-lookup"><span data-stu-id="078a8-119">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="078a8-120">false</span><span class="sxs-lookup"><span data-stu-id="078a8-120">false</span></span>|<span data-ttu-id="078a8-121">既定のスタックサイズを使用します。</span><span class="sxs-lookup"><span data-stu-id="078a8-121">Use the default stack size.</span></span> <span data-ttu-id="078a8-122">これは .NET Framework 4 の既定値です。</span><span class="sxs-lookup"><span data-stu-id="078a8-122">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="078a8-123">子要素</span><span class="sxs-lookup"><span data-stu-id="078a8-123">Child Elements</span></span>  

 <span data-ttu-id="078a8-124">なし。</span><span class="sxs-lookup"><span data-stu-id="078a8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="078a8-125">親要素</span><span class="sxs-lookup"><span data-stu-id="078a8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="078a8-126">要素</span><span class="sxs-lookup"><span data-stu-id="078a8-126">Element</span></span>|<span data-ttu-id="078a8-127">説明</span><span class="sxs-lookup"><span data-stu-id="078a8-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="078a8-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="078a8-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="078a8-129">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="078a8-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="078a8-130">解説</span><span class="sxs-lookup"><span data-stu-id="078a8-130">Remarks</span></span>  

 <span data-ttu-id="078a8-131">この構成要素は、プロセスでの仮想メモリの使用量の削減を要求するために使用されます。これは、CLR が内部スレッドに使用する明示的なスレッドサイズ (要求が受け入れられた場合) が既定のサイズよりも小さいためです。</span><span class="sxs-lookup"><span data-stu-id="078a8-131">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="078a8-132">この構成要素は、絶対的な要件ではなく、CLR への要求です。</span><span class="sxs-lookup"><span data-stu-id="078a8-132">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="078a8-133">.NET Framework 4 では、要求は x86 アーキテクチャに対してのみ受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="078a8-133">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="078a8-134">この要素は、CLR の将来のバージョンでは完全に無視される場合もあれば、選択した内部スレッドで常に使用される明示的なスタックサイズに置き換えられる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="078a8-134">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="078a8-135">この構成要素を指定すると、CLR が要求を受け入れた場合に、より小さなスタックサイズによってスタックオーバーフローが発生する可能性があるため、仮想メモリの使用量が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="078a8-135">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="078a8-136">例</span><span class="sxs-lookup"><span data-stu-id="078a8-136">Example</span></span>  

 <span data-ttu-id="078a8-137">次の例は、CLR が内部で使用する特定のスレッドに対して明示的なスタックサイズを使用するように要求する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="078a8-137">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="078a8-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="078a8-138">See also</span></span>

- [<span data-ttu-id="078a8-139">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="078a8-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="078a8-140">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="078a8-140">Configuration File Schema</span></span>](../index.md)
