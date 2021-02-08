---
description: 詳細については、「ランタイムディレクティブ (rd.xml) 構成ファイルリファレンス」を参照してください。
title: ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: 9c995bd831f01e47c651d015895398e1ad42633d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801996"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="9fbc8-103">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="9fbc8-103">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="9fbc8-104">ランタイム ディレクティブ (.rd.xml) ファイルは、指定されたプログラム要素をリフレクションに使用できるかどうかを示す XML 構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-104">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="9fbc8-105">ランタイム ディレクティブ ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-105">Here’s an example of a runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />
    <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />
    <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />
    <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />

    <Namespace Name="System.Collections.ObjectModel" >
      <TypeInstantiation Name="ObservableCollection"
            Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />
      <TypeInstantiation Name="ReadOnlyObservableCollection"
            Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />
    </Namespace>
  </Application>
</Directives>
```

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="9fbc8-106">ランタイム ディレクティブ ファイルの構造</span><span class="sxs-lookup"><span data-stu-id="9fbc8-106">The structure of a runtime directives file</span></span>

<span data-ttu-id="9fbc8-107">ランタイム ディレクティブ ファイルは `http://schemas.microsoft.com/netfx/2013/01/metadata` 名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-107">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="9fbc8-108">ルート要素は [Directives](directives-element-net-native.md) 要素です。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-108">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="9fbc8-109">これには、次の構造に示すように、0 個以上の [Library](library-element-net-native.md) 要素と 0 または 1 個の [Application](application-element-net-native.md) 要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-109">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="9fbc8-110">[Application](application-element-net-native.md) 要素の属性は、アプリケーション全体のランタイム リフレクション ポリシーを定義できるか、子要素のコンテナーとして機能できます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-110">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="9fbc8-111">一方、[Library](library-element-net-native.md) 要素は単にコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-111">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="9fbc8-112">[Application](application-element-net-native.md) 要素と [Library](library-element-net-native.md) 要素の子は、リフレクションで使用できる型、メソッド、フィールド、プロパティ、およびイベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-112">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="9fbc8-113">参照情報については、次の構造から要素を選択するか、「[ランタイム ディレクティブ要素](runtime-directive-elements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-113">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="9fbc8-114">次の階層で、省略記号は再帰構造を示します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-114">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="9fbc8-115">角かっこ内の情報は、その要素が省略可能または必須のいずれであるか、および使用される場合に許可されるインスタンスの数 (1 つまたは複数) を示します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-115">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

- <span data-ttu-id="9fbc8-116">[Directives](directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-116">[Directives](directives-element-net-native.md) [1:1]</span></span>
  - <span data-ttu-id="9fbc8-117">[Application](application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-117">[Application](application-element-net-native.md) [0:1]</span></span>
    - <span data-ttu-id="9fbc8-118">[Assembly](assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-118">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-119">[名前空間](namespace-element-net-native.md) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-119">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-120">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-120">.</span></span> <span data-ttu-id="9fbc8-121">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-121">.</span></span>
      - <span data-ttu-id="9fbc8-122">[「](type-element-net-native.md) [0: M]」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-122">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-123">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-123">.</span></span> <span data-ttu-id="9fbc8-124">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-124">.</span></span>
      - <span data-ttu-id="9fbc8-125">[Typeinstantiation インスタンス化](typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-125">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="9fbc8-126">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-126">.</span></span> <span data-ttu-id="9fbc8-127">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-127">.</span></span>
    - <span data-ttu-id="9fbc8-128">[Namespace](namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-128">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-129">[名前空間](namespace-element-net-native.md) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-129">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-130">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-130">.</span></span> <span data-ttu-id="9fbc8-131">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-131">.</span></span>
      - <span data-ttu-id="9fbc8-132">[「](type-element-net-native.md) [0: M]」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-132">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-133">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-133">.</span></span> <span data-ttu-id="9fbc8-134">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-134">.</span></span>
      - <span data-ttu-id="9fbc8-135">[Typeinstantiation インスタンス化](typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-135">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="9fbc8-136">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-136">.</span></span> <span data-ttu-id="9fbc8-137">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-137">.</span></span>
    - <span data-ttu-id="9fbc8-138">[Type](type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-138">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-139">[Subtypes](subtypes-element-net-native.md) (それを含む型のサブクラス) [O:1]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-139">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="9fbc8-140">[「](type-element-net-native.md) [0: M]」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-140">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-141">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-141">.</span></span> <span data-ttu-id="9fbc8-142">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-142">.</span></span>
      - <span data-ttu-id="9fbc8-143">[Typeinstantiation インスタンス化](typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-143">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="9fbc8-144">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-144">.</span></span> <span data-ttu-id="9fbc8-145">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-145">.</span></span>
      - <span data-ttu-id="9fbc8-146">[AttributeImplies](attributeimplies-element-net-native.md) (それを含む型が属性) [O:1]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-146">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="9fbc8-147">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-147">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-148">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-148">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="9fbc8-149">[Parameter](parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-149">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="9fbc8-150">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-150">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="9fbc8-151">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-151">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-152">[MethodInstantiation](methodinstantiation-element-net-native.md) (構築されたジェネリック メソッド) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-152">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-153">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-153">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-154">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-154">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-155">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-155">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="9fbc8-156">[TypeInstantiation](typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-156">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-157">[「](type-element-net-native.md) [0: M]」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-157">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-158">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-158">.</span></span> <span data-ttu-id="9fbc8-159">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-159">.</span></span>
      - <span data-ttu-id="9fbc8-160">[Typeinstantiation インスタンス化](typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="9fbc8-161">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-161">.</span></span> <span data-ttu-id="9fbc8-162">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-162">.</span></span>
      - <span data-ttu-id="9fbc8-163">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-163">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="9fbc8-164">[Parameter](parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-164">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="9fbc8-165">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-165">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="9fbc8-166">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-166">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-167">[MethodInstantiation](methodinstantiation-element-net-native.md) (構築されたジェネリック メソッド) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-167">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-168">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-168">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-169">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-169">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-170">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-170">[Event](event-element-net-native.md) [0:M]</span></span>
  - <span data-ttu-id="9fbc8-171">[Library](library-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-171">[Library](library-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="9fbc8-172">[Assembly](assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-172">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-173">[名前空間](namespace-element-net-native.md) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-173">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-174">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-174">.</span></span> <span data-ttu-id="9fbc8-175">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-175">.</span></span>
      - <span data-ttu-id="9fbc8-176">[「](type-element-net-native.md) [0: M]」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-176">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-177">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-177">.</span></span> <span data-ttu-id="9fbc8-178">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-178">.</span></span>
      - <span data-ttu-id="9fbc8-179">[Typeinstantiation インスタンス化](typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-179">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="9fbc8-180">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-180">.</span></span> <span data-ttu-id="9fbc8-181">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-181">.</span></span>
    - <span data-ttu-id="9fbc8-182">[Namespace](namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-182">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-183">[名前空間](namespace-element-net-native.md) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-183">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-184">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-184">.</span></span> <span data-ttu-id="9fbc8-185">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-185">.</span></span>
      - <span data-ttu-id="9fbc8-186">[「](type-element-net-native.md) [0: M]」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-186">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-187">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-187">.</span></span> <span data-ttu-id="9fbc8-188">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-188">.</span></span>
      - <span data-ttu-id="9fbc8-189">[Typeinstantiation インスタンス化](typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-189">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="9fbc8-190">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-190">.</span></span> <span data-ttu-id="9fbc8-191">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-191">.</span></span>
    - <span data-ttu-id="9fbc8-192">[Type](type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-192">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-193">[Subtypes](subtypes-element-net-native.md) (それを含む型のサブクラス) [O:1]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-193">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="9fbc8-194">[「](type-element-net-native.md) [0: M]」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-194">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-195">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-195">.</span></span> <span data-ttu-id="9fbc8-196">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-196">.</span></span>
      - <span data-ttu-id="9fbc8-197">[Typeinstantiation インスタンス化](typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-197">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="9fbc8-198">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-198">.</span></span> <span data-ttu-id="9fbc8-199">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-199">.</span></span>
      - <span data-ttu-id="9fbc8-200">[AttributeImplies](attributeimplies-element-net-native.md) (それを含む型が属性) [O:1]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-200">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="9fbc8-201">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-201">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-202">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-202">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-203">[MethodInstantiation](methodinstantiation-element-net-native.md) (構築されたジェネリック メソッド) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-203">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-204">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-204">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-205">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-205">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-206">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-206">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="9fbc8-207">[TypeInstantiation](typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-207">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-208">[「](type-element-net-native.md) [0: M]」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-208">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="9fbc8-209">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-209">.</span></span> <span data-ttu-id="9fbc8-210">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-210">.</span></span>
      - <span data-ttu-id="9fbc8-211">[Typeinstantiation インスタンス化](typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0: M]。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-211">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="9fbc8-212">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-212">.</span></span> <span data-ttu-id="9fbc8-213">.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-213">.</span></span>
      - <span data-ttu-id="9fbc8-214">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-214">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-215">[MethodInstantiation](methodinstantiation-element-net-native.md) (構築されたジェネリック メソッド) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-215">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-216">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-216">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-217">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-217">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="9fbc8-218">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="9fbc8-218">[Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="9fbc8-219">[Application](application-element-net-native.md) 要素は属性を持たないか、「[ランタイム ディレクティブとポリシー](#Directives)」セクションで説明しているポリシー属性を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-219">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="9fbc8-220">[Library](library-element-net-native.md) 要素は、ライブラリまたはアセンブリの名前をファイル拡張子なしで指定する、`Name` 属性 1 つを持ちます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-220">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="9fbc8-221">たとえば、次の [Library](library-element-net-native.md) 要素は、Extensions.dll という名前のアセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-221">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <!-- Child elements go here -->
  </Application>
  <Library Name="Extensions">
     <!-- Child elements go here -->
  </Library>
</Directives>
```

<a name="Directives"></a>

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="9fbc8-222">ランタイム ディレクティブとポリシー</span><span class="sxs-lookup"><span data-stu-id="9fbc8-222">Runtime directives and policy</span></span>

<span data-ttu-id="9fbc8-223">[Application](application-element-net-native.md) 要素自体と [Library](library-element-net-native.md) 要素と [Application](application-element-net-native.md) 要素の子要素はポリシーを表します。つまり、アプリがプログラム要素にリフレクションを適用できる方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-223">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="9fbc8-224">ポリシーの種類は要素の属性 (たとえば、`Serialize`) により定義されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-224">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="9fbc8-225">ポリシーの値は属性の値 (たとえば、`Serialize="Required"`) により定義されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-225">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="9fbc8-226">要素の属性により指定されるすべてのポリシーは、そのポリシーの値を指定しないすべての子要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-226">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="9fbc8-227">たとえば、[Type](type-element-net-native.md) 要素で指定されたポリシーは、ポリシーが明示的に指定されていない、その要素に含まれる型とメンバーすべてに適用されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-227">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="9fbc8-228">[Application](application-element-net-native.md)、[Assembly](assembly-element-net-native.md)、[AttributeImplies](attributeimplies-element-net-native.md)、[Namespace](namespace-element-net-native.md)、[Subtypes](subtypes-element-net-native.md)、および [Type](type-element-net-native.md) 要素で表すことができるポリシーは、個々のメンバーについて ([Method](method-element-net-native.md)、[Property](property-element-net-native.md)、[Field](field-element-net-native.md)、および [Event](event-element-net-native.md) 要素で) 表すことができるポリシーとは異なります。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-228">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="9fbc8-229">アセンブリ、名前空間、型に対するポリシーの指定</span><span class="sxs-lookup"><span data-stu-id="9fbc8-229">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="9fbc8-230">[Application](application-element-net-native.md)、[Assembly](assembly-element-net-native.md)、[AttributeImplies](attributeimplies-element-net-native.md)、[Namespace](namespace-element-net-native.md)、[Subtypes](subtypes-element-net-native.md)、および [Type](type-element-net-native.md) 要素は、次のポリシーの種類をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-230">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="9fbc8-231">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-231">`Activate`.</span></span> <span data-ttu-id="9fbc8-232">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-232">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="9fbc8-233">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-233">`Browse`.</span></span> <span data-ttu-id="9fbc8-234">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-234">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="9fbc8-235">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-235">`Dynamic`.</span></span> <span data-ttu-id="9fbc8-236">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-236">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="9fbc8-237">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-237">`Serialize`.</span></span> <span data-ttu-id="9fbc8-238">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのサードパーティ ライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-238">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="9fbc8-239">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-239">`DataContractSerializer`.</span></span> <span data-ttu-id="9fbc8-240"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-240">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="9fbc8-241">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-241">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="9fbc8-242"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-242">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="9fbc8-243">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-243">`XmlSerializer`.</span></span> <span data-ttu-id="9fbc8-244"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-244">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="9fbc8-245">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-245">`MarshalObject`.</span></span> <span data-ttu-id="9fbc8-246">WinRT と COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-246">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="9fbc8-247">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-247">`MarshalDelegate`.</span></span> <span data-ttu-id="9fbc8-248">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-248">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="9fbc8-249">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="9fbc8-249">`MarshalStructure` .</span></span> <span data-ttu-id="9fbc8-250">ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-250">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="9fbc8-251">これらのポリシーの種類に関連付けられている設定を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-251">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="9fbc8-252">`All`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-252">`All`.</span></span> <span data-ttu-id="9fbc8-253">ツール チェーンが削除しないすべての型とメンバーに対するポリシーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-253">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="9fbc8-254">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-254">`Auto`.</span></span> <span data-ttu-id="9fbc8-255">既定の動作を使用します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-255">Use the default behavior.</span></span> <span data-ttu-id="9fbc8-256">(親要素などによってポリシーがオーバーライドされない限り、ポリシーを指定しないことは、そのポリシーを `Auto` に設定することと同じです。)</span><span class="sxs-lookup"><span data-stu-id="9fbc8-256">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="9fbc8-257">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-257">`Excluded`.</span></span> <span data-ttu-id="9fbc8-258">プログラム要素のポリシーを無効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-258">Disable the policy for the program element.</span></span>

- <span data-ttu-id="9fbc8-259">`Public`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-259">`Public`.</span></span> <span data-ttu-id="9fbc8-260">ツール チェーンがメンバーが不要なために削除すると判断した場合を除き、パブリック型またはメンバーのポリシーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-260">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="9fbc8-261">(後者の場合は、`Required Public` を使用して、メンバーが保持されており、リフレクション機能があることを確認する必要があります。)</span><span class="sxs-lookup"><span data-stu-id="9fbc8-261">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="9fbc8-262">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-262">`PublicAndInternal`.</span></span> <span data-ttu-id="9fbc8-263">パブリックおよび内部型またはメンバーがツール チェーンによって削除されていない場合、それらのポリシーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-263">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="9fbc8-264">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-264">`Required Public`.</span></span> <span data-ttu-id="9fbc8-265">使用されているかどうかに関係なく、パブリック型とメンバーを保持し、それらのポリシーを有効にするためにツール チェーンを要求します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-265">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="9fbc8-266">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-266">`Required PublicAndInternal`.</span></span> <span data-ttu-id="9fbc8-267">使用されているかどうかに関係なく、パブリックおよび内部両方の型とメンバーを保持し、それらのポリシーを有効にするためにツール チェーンを要求します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-267">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="9fbc8-268">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="9fbc8-268">`Required All`.</span></span> <span data-ttu-id="9fbc8-269">使用されているかどうかに関係なく、すべての型とメンバーを保持し、それらのポリシーを有効にするために、ツール チェーンを要求します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-269">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="9fbc8-270">たとえば、次のランタイム ディレクティブ ファイルは、DataClasses.dll アセンブリ内のすべての型とメンバーのポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-270">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="9fbc8-271">これは、すべてのパブリック プロパティのシリアル化のリフレクションを有効にし、すべての型と型のメンバーの参照を有効にし、すべての型のアクティブ化を (`Dynamic` 属性により) 有効にして、すべてのパブリック型とメンバーのリフレクションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-271">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"
                Browse="All" Activate="PublicAndInternal"
                Dynamic="Public"  />
   </Application>
   <Library Name="UtilityLibrary">
     <!-- Child elements go here -->
   </Library>
</Directives>
```

### <a name="specifying-policy-for-members"></a><span data-ttu-id="9fbc8-272">メンバーのポリシーの指定</span><span class="sxs-lookup"><span data-stu-id="9fbc8-272">Specifying policy for members</span></span>

<span data-ttu-id="9fbc8-273">[Property](property-element-net-native.md) 要素と [Field](field-element-net-native.md) 要素は次のポリシーの種類をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-273">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="9fbc8-274">`Browse`: このメンバーに関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-274">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="9fbc8-275">`Dynamic`: コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-275">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="9fbc8-276">また、それを含む型に関する情報の照会も制御します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-276">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="9fbc8-277">`Serialize`: メンバーへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-277">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="9fbc8-278">このポリシーは、コンストラクター、フィールド、およびプロパティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-278">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="9fbc8-279">[Method](method-element-net-native.md) 要素と [Event](event-element-net-native.md) 要素は次のポリシーの種類をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-279">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="9fbc8-280">`Browse`: このメンバーに関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-280">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="9fbc8-281">`Dynamic`: コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-281">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="9fbc8-282">また、それを含む型に関する情報の照会も制御します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-282">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="9fbc8-283">これらのポリシーの種類に関連付けられている設定を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-283">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="9fbc8-284">`Auto`: 既定の動作を使用します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-284">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="9fbc8-285">(何かにオーバーライドされない限り、ポリシーを指定しないことは、そのポリシーを `Auto` に設定することと同じです。)</span><span class="sxs-lookup"><span data-stu-id="9fbc8-285">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="9fbc8-286">`Excluded`: メンバーのメタデータを含めません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-286">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="9fbc8-287">`Included`: 親型が出力に存在する場合、ポリシーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-287">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="9fbc8-288">`Required`: このメンバーが未使用と見なされる場合でもこれを保持し、そのメンバーのポリシーを有効にするためにツール チェーンを要求します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-288">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="9fbc8-289">ランタイム ディレクティブ ファイルのセマンティクス</span><span class="sxs-lookup"><span data-stu-id="9fbc8-289">Runtime directives file semantics</span></span>

<span data-ttu-id="9fbc8-290">ポリシーは、上位レベルと下位レベルの要素両方に同時に定義できます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-290">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="9fbc8-291">たとえば、アセンブリと、そのアセンブリに含まれる型の一部にポリシーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-291">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="9fbc8-292">特定の下位レベル要素が表されていない場合、その親のポリシーを継承します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-292">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="9fbc8-293">たとえば、`Assembly` 要素は存在するが `Type` 要素は存在しない場合、`Assembly` 要素で指定されるポリシーはアセンブリ内のすべての型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-293">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="9fbc8-294">複数の要素が同じプログラム要素にポリシーを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-294">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="9fbc8-295">たとえば、個別の [Assembly](assembly-element-net-native.md) 要素が、同じアセンブリの同じポリシー要素を別々に定義するとします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-295">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="9fbc8-296">次のセクションで、このような場合に特定の型のポリシーがどのように解決されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-296">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="9fbc8-297">ジェネリック型またはメソッドの [Type](type-element-net-native.md) 要素または [Method](method-element-net-native.md) 要素は、独自のポリシーを持たないすべてのインスタンス化にそのポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-297">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="9fbc8-298">たとえば、`Type` のポリシーを指定する <xref:System.Collections.Generic.List%601> 要素は、構築された特定のジェネリック型 (`List<Int32>` など) について `TypeInstantiation` 要素によってオーバーライドされない限り、そのジェネリック型のすべての構築されたインスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-298">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="9fbc8-299">そうでない場合、要素は指定されたプログラム要素のポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-299">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="9fbc8-300">要素があいまいな場合、エンジンが一致を検索し、完全一致が見つかるとそれを使用します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-300">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="9fbc8-301">複数の一致が見つかった場合は警告またはエラーになります。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-301">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="9fbc8-302">2 つのディレクティブが同じプログラム要素にポリシーを適用する場合</span><span class="sxs-lookup"><span data-stu-id="9fbc8-302">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="9fbc8-303">別のランタイム ディレクティブ ファイルにある 2 つの要素が同じプログラム要素 (アセンブリや型など) の同じポリシーの種類を異なる値に設定しようとした場合、次のように競合が解決されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-303">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="9fbc8-304">`Excluded` 要素が存在する場合はこれが優先されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-304">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="9fbc8-305">`Required` は `Required` 以外より優先されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-305">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="9fbc8-306">`All` は `PublicAndInternal` (`Public` より優先) より優先されされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-306">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="9fbc8-307">明示的な設定はいずれも `Auto` より優先されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-307">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="9fbc8-308">たとえば、1 つのプロジェクトに次の 2 つのランタイム ディレクティブ ファイルが含まれている場合、DataClasses.dll のシリアル化ポリシーは `Required Public` と `All` の両方に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-308">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="9fbc8-309">この場合、シリアル化ポリシーは `Required All` として解決されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-309">In this case, the serialization policy would be resolved as `Required All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"/>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="All" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

<span data-ttu-id="9fbc8-310">ただし、1 つのランタイム ディレクティブ ファイル内の 2 つのディレクティブが同じプログラム要素に同じポリシーの種類を設定しようとした場合、XML スキーマ定義ツールからエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-310">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="9fbc8-311">子要素と親要素が同じポリシーの種類を適用する場合</span><span class="sxs-lookup"><span data-stu-id="9fbc8-311">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="9fbc8-312">`Excluded` 設定を含め、子要素はその親要素をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-312">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="9fbc8-313">オーバーライドは、`Auto` を指定する必要がある主な理由です。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-313">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="9fbc8-314">次の例では、`DataClasses` にはあるが `DataClasses.ViewModels` にはないものすべてのシリアル化ポリシー設定が `Required Public` になり、`DataClasses` と `DataClasses.ViewModels` の両方にあるものすべてのシリアル化ポリシー設定は `All` になります。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-314">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="9fbc8-315">オープン ジェネリックとインスタンス化された要素が同じポリシーの種類を適用する場合</span><span class="sxs-lookup"><span data-stu-id="9fbc8-315">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="9fbc8-316">次の例では、`Dictionary<int,int>` には、特に `Browse` ポリシーを割り当てる理由がエンジンにある場合にのみ、`Browse` ポリシーが割り当てられます (通常は、これが既定の動作です)。それ以外の <xref:System.Collections.Generic.Dictionary%602> のすべてのインスタンス化では、そのメンバーのすべてが参照可能になります。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-316">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
      <Namespace Name="DataClasses.Generics" />
      <Type Name="Dictionary" Browse="All" />
      <TypeInstantiation Name="Dictionary"
                         Arguments="System.Int32,System.Int32" Browse="Auto" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="how-policy-is-inferred"></a><span data-ttu-id="9fbc8-317">ポリシーの推論方法</span><span class="sxs-lookup"><span data-stu-id="9fbc8-317">How policy is inferred</span></span>

<span data-ttu-id="9fbc8-318">ポリシーの種類ごとに、そのポリシーの種類の存在が他の構造体にどう影響するかを決定する一連のルールが異なります。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-318">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="9fbc8-319">Browse ポリシーの効果</span><span class="sxs-lookup"><span data-stu-id="9fbc8-319">The effect of Browse policy</span></span>

<span data-ttu-id="9fbc8-320">`Browse` ポリシーを型に適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-320">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="9fbc8-321">型の基本型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-321">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-322">型がインスタンス化されたジェネリックである場合、インスタンス化されていないその型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-322">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-323">型がデリゲートの場合、型の `Invoke` メソッドが `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-323">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="9fbc8-324">型の各インターフェイスが `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-324">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-325">型に適用されている各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-325">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-326">型がジェネリックの場合、各制約型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-326">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-327">型がジェネリックの場合、その型のインスタンス化対象である型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-327">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="9fbc8-328">メソッドに `Browse` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-328">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="9fbc8-329">メソッドの各パラメーター型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-329">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-330">メソッドの戻り型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-330">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-331">メソッドを含む型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-331">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-332">メソッドがインスタンス化されたジェネリック メソッドである場合、インスタンス化されていないジェネリック メソッドが `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-332">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-333">メソッドに適用される各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-333">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-334">メソッドがジェネリックの場合、各制約型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-334">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-335">メソッドがジェネリックの場合、そのメソッドのインスタンス化対象である型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-335">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="9fbc8-336">フィールドに `Browse` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-336">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="9fbc8-337">フィールドに適用される各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-337">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-338">フィールドの型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-338">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-339">フィールドが属する型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-339">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="9fbc8-340">Dynamic ポリシーの効果</span><span class="sxs-lookup"><span data-stu-id="9fbc8-340">The effect of Dynamic policy</span></span>

<span data-ttu-id="9fbc8-341">`Dynamic` ポリシーを型に適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-341">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="9fbc8-342">型の基本型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-342">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="9fbc8-343">型がインスタンス化されたジェネリックである場合、インスタンス化されていないその型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-343">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="9fbc8-344">型がデリゲート型の場合、型の `Invoke` メソッドが `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-344">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="9fbc8-345">型の各インターフェイスが `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-345">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-346">型に適用されている各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-346">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-347">型がジェネリックの場合、各制約型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-347">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-348">型がジェネリックの場合、その型のインスタンス化対象である型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-348">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="9fbc8-349">メソッドに `Dynamic` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-349">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="9fbc8-350">メソッドの各パラメーター型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-350">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-351">メソッドの戻り型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-351">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="9fbc8-352">メソッドを含む型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-352">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="9fbc8-353">メソッドがインスタンス化されたジェネリック メソッドである場合、インスタンス化されていないジェネリック メソッドが `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-353">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-354">メソッドに適用される各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-354">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-355">メソッドがジェネリックの場合、各制約型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-355">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-356">メソッドがジェネリックの場合、そのメソッドのインスタンス化対象である型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-356">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-357">メソッドを `MethodInfo.Invoke` により呼び出すことができ、<xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> によりデリゲートの作成が可能になります。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-357">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="9fbc8-358">フィールドに `Dynamic` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-358">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="9fbc8-359">フィールドに適用される各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-359">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-360">フィールドの型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-360">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="9fbc8-361">フィールドが属する型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-361">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="9fbc8-362">Activation ポリシーの効果</span><span class="sxs-lookup"><span data-stu-id="9fbc8-362">The effect of Activation policy</span></span>

<span data-ttu-id="9fbc8-363">型に Activation ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-363">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="9fbc8-364">型がインスタンス化されたジェネリックである場合、インスタンス化されていないその型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-364">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-365">型がデリゲート型の場合、型の `Invoke` メソッドが `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-365">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="9fbc8-366">型のコンストラクターが `Activation` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-366">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="9fbc8-367">メソッドに `Activation` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-367">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="9fbc8-368">コンストラクターを <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> メソッドと <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> メソッドにより呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-368">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="9fbc8-369">メソッドに関しては、`Activation` ポリシーはコンストラクターにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-369">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="9fbc8-370">フィールドに `Activation` ポリシーを適用しても効果はありません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-370">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="9fbc8-371">Serialize ポリシーの効果</span><span class="sxs-lookup"><span data-stu-id="9fbc8-371">The effect of Serialize policy</span></span>

<span data-ttu-id="9fbc8-372">`Serialize` ポリシーにより、一般的なリフレクション ベースのシリアライザーを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-372">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="9fbc8-373">ただし、Microsoft では、Microsoft 以外のシリアライザーの正確なリフレクション アクセス パターンを認識していないため、このポリシーが常に効果的であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-373">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="9fbc8-374">`Serialize` ポリシーを型に適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-374">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="9fbc8-375">型の基本型が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-375">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="9fbc8-376">型がインスタンス化されたジェネリックである場合、インスタンス化されていないその型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-376">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="9fbc8-377">型がデリゲート型の場合、型の `Invoke` メソッドが `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-377">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="9fbc8-378">型が列挙の場合、型の配列が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-378">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="9fbc8-379">型が <xref:System.Collections.Generic.IEnumerable%601> を実装する場合、`T` が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-379">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="9fbc8-380">型が <xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.Generic.IList%601>、<xref:System.Collections.Generic.ICollection%601>、<xref:System.Collections.Generic.IReadOnlyCollection%601>、または <xref:System.Collections.Generic.IReadOnlyList%601> の場合、`T[]` と <xref:System.Collections.Generic.List%601> が `Serialize` ポリシーでマークされますが、インターフェイス型のメンバーは `Serialize` ポリシーでマークされません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-380">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="9fbc8-381">型が <xref:System.Collections.Generic.List%601> の場合、型のどのメンバーも `Serialize` ポリシーでマークされません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-381">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="9fbc8-382">型が <xref:System.Collections.Generic.IDictionary%602> の場合、<xref:System.Collections.Generic.Dictionary%602> が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-382">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="9fbc8-383">ただし、型のどのメンバーも `Serialize` ポリシーでマークされません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-383">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="9fbc8-384">型が <xref:System.Collections.Generic.Dictionary%602> の場合、型のどのメンバーも `Serialize` ポリシーでマークされません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-384">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="9fbc8-385">型が <xref:System.Collections.Generic.IDictionary%602> を実装している場合、`TKey` と `TValue` が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-385">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="9fbc8-386">各コンストラクター、各プロパティ アクセサー、および各フィールドが `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-386">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="9fbc8-387">メソッドに `Serialize` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-387">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="9fbc8-388">それを含む型が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-388">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="9fbc8-389">メソッドの戻り型が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-389">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="9fbc8-390">フィールドに `Serialize` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-390">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="9fbc8-391">それを含む型が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-391">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="9fbc8-392">フィールドの型が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-392">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="9fbc8-393">XmlSerializer、DataContractSerializer、DataContractJsonSerializer の各ポリシーの影響</span><span class="sxs-lookup"><span data-stu-id="9fbc8-393">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="9fbc8-394">`Serialize`リフレクションベースのシリアライザーを対象とするポリシーとは異なり、、、およびの各ポリシーを使用して、 <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .NET Native ツールチェーンで認識されているシリアライザーのセットを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-394">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="9fbc8-395">これらのシリアライザーはリフレクションを使用して実装されるのではなく、実行時にシリアル化可能な型のセットが、リフレクション可能な型と同様の方法で決定されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-395">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="9fbc8-396">これらのポリシーのいずれかを型に適用すると、対応するシリアライザーで型をシリアル化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-396">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="9fbc8-397">また、シリアル化が必要であることをシリアル化エンジンが静的に決定できる、すべての型もシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-397">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="9fbc8-398">これらのポリシーは、メソッドとフィールドには影響しません。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-398">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="9fbc8-399">詳細については、「[Windows ストア アプリの .NET ネイティブへの移行](migrating-your-windows-store-app-to-net-native.md)」の「シリアライザーの違い」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fbc8-399">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9fbc8-400">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fbc8-400">See also</span></span>

- [<span data-ttu-id="9fbc8-401">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="9fbc8-401">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="9fbc8-402">リフレクションおよび .NET ネイティブ</span><span class="sxs-lookup"><span data-stu-id="9fbc8-402">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
