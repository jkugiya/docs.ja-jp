---
description: '詳細情報: <disableCommitThreadStack> 要素'
title: <disableCommitThreadStack> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
ms.openlocfilehash: f80a23b12f67b9f3df1ddb010edb735225f6f7a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787098"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="f6bde-103">\<disableCommitThreadStack> 要素</span><span class="sxs-lookup"><span data-stu-id="f6bde-103">\<disableCommitThreadStack> Element</span></span>

<span data-ttu-id="f6bde-104">スレッドの起動時にスレッド スタック全体をコミットするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6bde-104">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="f6bde-105">構文</span><span class="sxs-lookup"><span data-stu-id="f6bde-105">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6bde-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f6bde-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f6bde-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6bde-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6bde-108">属性</span><span class="sxs-lookup"><span data-stu-id="f6bde-108">Attributes</span></span>  
  
|<span data-ttu-id="f6bde-109">属性</span><span class="sxs-lookup"><span data-stu-id="f6bde-109">Attribute</span></span>|<span data-ttu-id="f6bde-110">説明</span><span class="sxs-lookup"><span data-stu-id="f6bde-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6bde-111">enabled</span><span class="sxs-lookup"><span data-stu-id="f6bde-111">enabled</span></span>|<span data-ttu-id="f6bde-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="f6bde-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="f6bde-113">スレッド起動時にスレッド スタック全体をコミットすること (既定の動作) を無効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6bde-113">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f6bde-114">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="f6bde-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="f6bde-115">値</span><span class="sxs-lookup"><span data-stu-id="f6bde-115">Value</span></span>|<span data-ttu-id="f6bde-116">説明</span><span class="sxs-lookup"><span data-stu-id="f6bde-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f6bde-117">0</span><span class="sxs-lookup"><span data-stu-id="f6bde-117">0</span></span>|<span data-ttu-id="f6bde-118">共通言語ランタイムの既定の動作 (スレッドの起動時にスレッド スタック全体をコミット) を無効にしません。</span><span class="sxs-lookup"><span data-stu-id="f6bde-118">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="f6bde-119">1</span><span class="sxs-lookup"><span data-stu-id="f6bde-119">1</span></span>|<span data-ttu-id="f6bde-120">共通言語ランタイムの既定の動作 (スレッドの起動時にスレッド スタック全体をコミット) を無効にします。</span><span class="sxs-lookup"><span data-stu-id="f6bde-120">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6bde-121">子要素</span><span class="sxs-lookup"><span data-stu-id="f6bde-121">Child Elements</span></span>  

 <span data-ttu-id="f6bde-122">なし。</span><span class="sxs-lookup"><span data-stu-id="f6bde-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6bde-123">親要素</span><span class="sxs-lookup"><span data-stu-id="f6bde-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f6bde-124">要素</span><span class="sxs-lookup"><span data-stu-id="f6bde-124">Element</span></span>|<span data-ttu-id="f6bde-125">説明</span><span class="sxs-lookup"><span data-stu-id="f6bde-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f6bde-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="f6bde-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f6bde-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f6bde-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6bde-128">解説</span><span class="sxs-lookup"><span data-stu-id="f6bde-128">Remarks</span></span>  

 <span data-ttu-id="f6bde-129">共通言語ランタイムの既定の動作では、スレッドの起動時にスレッド スタック全体がコミットされます。</span><span class="sxs-lookup"><span data-stu-id="f6bde-129">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="f6bde-130">メモリが限られているサーバーで多数のスレッドが作成する必要があり、それらのスレッドのほとんどがごくわずかのスタック スペースしか使用しない場合は、スレッドの起動時に共通言語ランタイムが直ちにスレッド スタック全体をコミットしなければ、サーバーのパフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6bde-130">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6bde-131">アンマネージ ホストは、 `STARTUP_DISABLE_COMMITTHREADSTACK` STARTUP_FLAGS [列挙体の](../../../unmanaged-api/hosting/startup-flags-enumeration.md) 起動フラグを使用することにより、同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="f6bde-131">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6bde-132">例</span><span class="sxs-lookup"><span data-stu-id="f6bde-132">Example</span></span>  

 <span data-ttu-id="f6bde-133">次の例は、共通言語ランタイムの既定の動作 (スレッド起動時にスレッド スタック全体をコミット) を無効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f6bde-133">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6bde-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6bde-134">See also</span></span>

- [<span data-ttu-id="f6bde-135">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="f6bde-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f6bde-136">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="f6bde-136">Configuration File Schema</span></span>](../index.md)
