---
description: 詳細については、「ランタイムディレクティブ要素」を参照してください。
title: ランタイム ディレクティブ要素
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: 74ff6c7d782f48106e37b99187770d8e82926be4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738430"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="8bcd4-103">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="8bcd4-103">Runtime Directive Elements</span></span>

<span data-ttu-id="8bcd4-104">ランタイム ディレクティブ (rd.xml) ファイル形式は、次のランタイム ディレクティブ要素をサポートします。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-104">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="8bcd4-105">階層表現については、「[ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](runtime-directives-rd-xml-configuration-file-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-105">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [\<Application>](application-element-net-native.md)  
 <span data-ttu-id="8bcd4-106">アプリで使用されるすべての型にランタイム リフレクション ポリシーを適用し、実行時にリフレクションに使用できるメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="8bcd4-107">これは要素の子です [\<Directives>](directives-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [\<Assembly>](assembly-element-net-native.md)  
 <span data-ttu-id="8bcd4-108">アセンブリ内のすべての型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-108">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="8bcd4-109">これは、 [\<Application>](application-element-net-native.md) 要素と要素の子です [\<Library>](library-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-109">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="8bcd4-110">それを含む [\<Type>](type-element-net-native.md) ディレクティブが属性の場合、は、その属性が適用されるコード要素に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-110">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [\<Directives>](directives-element-net-native.md)  
 <span data-ttu-id="8bcd4-111">.NET Native のすべてのランタイムディレクティブファイルのルート要素。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-111">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="8bcd4-112">その子要素は [\<Application>](application-element-net-native.md) と [\<Library>](library-element-net-native.md) です。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-112">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [\<Event>](event-element-net-native.md)  
 <span data-ttu-id="8bcd4-113">イベントに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-113">Applies runtime policy to an event.</span></span> <span data-ttu-id="8bcd4-114">これは、 [\<Type>](type-element-net-native.md) 要素と要素の子です [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-114">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Field>](field-element-net-native.md)  
 <span data-ttu-id="8bcd4-115">フィールドに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-115">Applies runtime policy to a field.</span></span> <span data-ttu-id="8bcd4-116">これは、 [\<Type>](type-element-net-native.md) 要素と要素の子です [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-116">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 <span data-ttu-id="8bcd4-117">ジェネリック型またはメソッドのパラメーター型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-117">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 <span data-ttu-id="8bcd4-118">型に実行時ポリシーを適用します (それを含んでいる型またはメソッドにそのポリシーが適用されている場合)。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-118">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [\<Library>](library-element-net-native.md)  
 <span data-ttu-id="8bcd4-119">アセンブリ内のすべての型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-119">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="8bcd4-120">これは、 [\<Application>](application-element-net-native.md) 要素と要素の子です [\<Library>](library-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-120">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<Method>](method-element-net-native.md)  
 <span data-ttu-id="8bcd4-121">メソッドに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-121">Applies runtime policy to a method.</span></span> <span data-ttu-id="8bcd4-122">これは、 [\<Type>](type-element-net-native.md) 要素と要素の子です [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-122">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="8bcd4-123">構築されたジェネリック メソッドに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-123">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="8bcd4-124">これは、 [\<Type>](type-element-net-native.md) 要素と要素の子です [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-124">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Namespace>](namespace-element-net-native.md)  
 <span data-ttu-id="8bcd4-125">名前空間内のすべての型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-125">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [\<Parameter>](parameter-element-net-native.md)  
 <span data-ttu-id="8bcd4-126">メソッドに渡された引数の型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-126">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [\<Property>](property-element-net-native.md)  
 <span data-ttu-id="8bcd4-127">プロパティに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-127">Applies runtime policy to a property.</span></span> <span data-ttu-id="8bcd4-128">これは、 [\<Type>](type-element-net-native.md) 要素と要素の子です [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-128">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 <span data-ttu-id="8bcd4-129">それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-129">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [\<Type>](type-element-net-native.md)  
 <span data-ttu-id="8bcd4-130">型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-130">Applies runtime policy to a type.</span></span>  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="8bcd4-131">構築されたジェネリック型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-131">Applies runtime policy to a constructed generic type.</span></span>  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 <span data-ttu-id="8bcd4-132">メソッドに渡された <xref:System.Type> 引数によって表される型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="8bcd4-132">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bcd4-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bcd4-133">See also</span></span>

- [<span data-ttu-id="8bcd4-134">rd.xml 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="8bcd4-134">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
