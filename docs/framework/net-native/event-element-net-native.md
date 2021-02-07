---
description: '詳細情報: <Event> 要素 (.NET Native)'
title: <Event> 要素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 16ef4376e5953da514598bd7cdcbe0c196ee4da5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747882"
---
# <a name="event-element-net-native"></a><span data-ttu-id="4b08f-103">\<Event> 要素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="4b08f-103">\<Event> Element (.NET Native)</span></span>

<span data-ttu-id="4b08f-104">イベントにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="4b08f-104">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b08f-105">構文</span><span class="sxs-lookup"><span data-stu-id="4b08f-105">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b08f-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4b08f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4b08f-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b08f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b08f-108">属性</span><span class="sxs-lookup"><span data-stu-id="4b08f-108">Attributes</span></span>  
  
|<span data-ttu-id="4b08f-109">属性</span><span class="sxs-lookup"><span data-stu-id="4b08f-109">Attribute</span></span>|<span data-ttu-id="4b08f-110">属性の型</span><span class="sxs-lookup"><span data-stu-id="4b08f-110">Attribute type</span></span>|<span data-ttu-id="4b08f-111">[説明]</span><span class="sxs-lookup"><span data-stu-id="4b08f-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="4b08f-112">全般</span><span class="sxs-lookup"><span data-stu-id="4b08f-112">General</span></span>|<span data-ttu-id="4b08f-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="4b08f-113">Required attribute.</span></span> <span data-ttu-id="4b08f-114">イベントの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b08f-114">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="4b08f-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="4b08f-115">Reflection</span></span>|<span data-ttu-id="4b08f-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="4b08f-116">Optional attribute.</span></span> <span data-ttu-id="4b08f-117">イベントに関する情報の照会やイベントの列挙を制御しますが、実行時の動的アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="4b08f-117">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="4b08f-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="4b08f-118">Reflection</span></span>|<span data-ttu-id="4b08f-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="4b08f-119">Optional attribute.</span></span> <span data-ttu-id="4b08f-120">イベントへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="4b08f-120">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="4b08f-121">このポリシーにより、実行時にイベントを動的に処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4b08f-121">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="4b08f-122">Name 属性</span><span class="sxs-lookup"><span data-stu-id="4b08f-122">Name attribute</span></span>  
  
|<span data-ttu-id="4b08f-123">値</span><span class="sxs-lookup"><span data-stu-id="4b08f-123">Value</span></span>|<span data-ttu-id="4b08f-124">説明</span><span class="sxs-lookup"><span data-stu-id="4b08f-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b08f-125">*method_name*</span><span class="sxs-lookup"><span data-stu-id="4b08f-125">*method_name*</span></span>|<span data-ttu-id="4b08f-126">イベントの名前です。</span><span class="sxs-lookup"><span data-stu-id="4b08f-126">The event name.</span></span> <span data-ttu-id="4b08f-127">イベントの型は、親要素または要素によって定義され [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="4b08f-127">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="4b08f-128">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="4b08f-128">All other attributes</span></span>  
  
|<span data-ttu-id="4b08f-129">値</span><span class="sxs-lookup"><span data-stu-id="4b08f-129">Value</span></span>|<span data-ttu-id="4b08f-130">説明</span><span class="sxs-lookup"><span data-stu-id="4b08f-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b08f-131">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="4b08f-131">*policy_setting*</span></span>|<span data-ttu-id="4b08f-132">イベントのこのポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="4b08f-132">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="4b08f-133">指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。</span><span class="sxs-lookup"><span data-stu-id="4b08f-133">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="4b08f-134">詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b08f-134">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b08f-135">子要素</span><span class="sxs-lookup"><span data-stu-id="4b08f-135">Child Elements</span></span>  

 <span data-ttu-id="4b08f-136">なし。</span><span class="sxs-lookup"><span data-stu-id="4b08f-136">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b08f-137">親要素</span><span class="sxs-lookup"><span data-stu-id="4b08f-137">Parent Elements</span></span>  
  
|<span data-ttu-id="4b08f-138">要素</span><span class="sxs-lookup"><span data-stu-id="4b08f-138">Element</span></span>|<span data-ttu-id="4b08f-139">説明</span><span class="sxs-lookup"><span data-stu-id="4b08f-139">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="4b08f-140">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="4b08f-140">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="4b08f-141">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="4b08f-141">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b08f-142">解説</span><span class="sxs-lookup"><span data-stu-id="4b08f-142">Remarks</span></span>  

 <span data-ttu-id="4b08f-143">イベントのポリシーが明示的に定義されていない場合は、その親要素の実行時ポリシーを継承します。</span><span class="sxs-lookup"><span data-stu-id="4b08f-143">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b08f-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b08f-144">See also</span></span>

- [<span data-ttu-id="4b08f-145">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4b08f-145">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="4b08f-146">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="4b08f-146">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="4b08f-147">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="4b08f-147">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
