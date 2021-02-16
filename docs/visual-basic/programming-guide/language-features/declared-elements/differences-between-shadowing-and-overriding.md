---
description: '詳細情報: シャドウとオーバーライドの違い (Visual Basic)'
title: シャドウとオーバーライドの違い
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 94e661c83b95448e7a78931b81c87b6e974059ed
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485199"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a><span data-ttu-id="f8525-103">シャドウとオーバーライドの違い (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8525-103">Differences Between Shadowing and Overriding (Visual Basic)</span></span>

<span data-ttu-id="f8525-104">基底クラスから継承するクラスを定義する場合、派生クラスの 1 つ以上の基底クラス要素を再定義する必要があることがあります。</span><span class="sxs-lookup"><span data-stu-id="f8525-104">When you define a class that inherits from a base class, you sometimes want to redefine one or more of the base class elements in the derived class.</span></span> <span data-ttu-id="f8525-105">この目的では、シャドウとオーバーライドの両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f8525-105">Shadowing and overriding are both available for this purpose.</span></span>  
  
## <a name="comparison"></a><span data-ttu-id="f8525-106">比較</span><span class="sxs-lookup"><span data-stu-id="f8525-106">Comparison</span></span>  

 <span data-ttu-id="f8525-107">シャドウとオーバーライドは、どちらも派生クラスが基底クラスから継承されるときに使用し、どちらも一方の宣言された要素を他方の要素で再定義します。</span><span class="sxs-lookup"><span data-stu-id="f8525-107">Shadowing and overriding are both used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="f8525-108">しかし、この 2 つには、大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="f8525-108">But there are significant differences between the two.</span></span>  
  
 <span data-ttu-id="f8525-109">次の表で、シャドウとオーバーライドを比較しています。</span><span class="sxs-lookup"><span data-stu-id="f8525-109">The following table compares shadowing with overriding.</span></span>  
  
||||  
|---|---|---|  
|<span data-ttu-id="f8525-110">比較のポイント</span><span class="sxs-lookup"><span data-stu-id="f8525-110">Point of comparison</span></span>|<span data-ttu-id="f8525-111">シャドウ</span><span class="sxs-lookup"><span data-stu-id="f8525-111">Shadowing</span></span>|<span data-ttu-id="f8525-112">オーバーライド</span><span class="sxs-lookup"><span data-stu-id="f8525-112">Overriding</span></span>|  
|<span data-ttu-id="f8525-113">目的</span><span class="sxs-lookup"><span data-stu-id="f8525-113">Purpose</span></span>|<span data-ttu-id="f8525-114">既に派生クラスに定義しているメンバーを取り込む、基底クラスの後続の変更から保護します</span><span class="sxs-lookup"><span data-stu-id="f8525-114">Protects against a subsequent base-class modification that introduces a member you have already defined in your derived class</span></span>|<span data-ttu-id="f8525-115">同じ呼び出しシーケンス<sup>1</sup>で、プロシージャまたはプロパティの異なる実装を定義することによって、ポリモーフィズムを実現します</span><span class="sxs-lookup"><span data-stu-id="f8525-115">Achieves polymorphism by defining a different implementation of a procedure or property with the same calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="f8525-116">再定義された要素</span><span class="sxs-lookup"><span data-stu-id="f8525-116">Redefined element</span></span>|<span data-ttu-id="f8525-117">任意の宣言された要素型</span><span class="sxs-lookup"><span data-stu-id="f8525-117">Any declared element type</span></span>|<span data-ttu-id="f8525-118">プロシージャ (`Function`、`Sub`、または `Operator`) またはプロパティのみ</span><span class="sxs-lookup"><span data-stu-id="f8525-118">Only a procedure (`Function`, `Sub`, or `Operator`) or property</span></span>|  
|<span data-ttu-id="f8525-119">再定義する要素</span><span class="sxs-lookup"><span data-stu-id="f8525-119">Redefining element</span></span>|<span data-ttu-id="f8525-120">任意の宣言された要素型</span><span class="sxs-lookup"><span data-stu-id="f8525-120">Any declared element type</span></span>|<span data-ttu-id="f8525-121">同じ呼び出しシーケンス<sup>1</sup> のプロシージャまたはプロパティのみ</span><span class="sxs-lookup"><span data-stu-id="f8525-121">Only a procedure or property with the identical calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="f8525-122">再定義する要素のアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="f8525-122">Access level of redefining element</span></span>|<span data-ttu-id="f8525-123">任意のアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="f8525-123">Any access level</span></span>|<span data-ttu-id="f8525-124">オーバーライドされた要素のアクセス レベルは変更できません</span><span class="sxs-lookup"><span data-stu-id="f8525-124">Cannot change access level of overridden element</span></span>|  
|<span data-ttu-id="f8525-125">再定義する要素の読みやすさと記述のしやすさ</span><span class="sxs-lookup"><span data-stu-id="f8525-125">Readability and writability of redefining element</span></span>|<span data-ttu-id="f8525-126">任意の組み合わせ</span><span class="sxs-lookup"><span data-stu-id="f8525-126">Any combination</span></span>|<span data-ttu-id="f8525-127">オーバーライドされたプロパティの読みやすさと記述のしやすさを変更することはできません</span><span class="sxs-lookup"><span data-stu-id="f8525-127">Cannot change readability or writability of overridden property</span></span>|  
|<span data-ttu-id="f8525-128">再定義の制御</span><span class="sxs-lookup"><span data-stu-id="f8525-128">Control over redefining</span></span>|<span data-ttu-id="f8525-129">基底クラス要素ではシャドウを強制または禁止できません</span><span class="sxs-lookup"><span data-stu-id="f8525-129">Base class element cannot enforce or prohibit shadowing</span></span>|<span data-ttu-id="f8525-130">基底クラス要素では、`MustOverride`、`NotOverridable`、または `Overridable` を指定できます</span><span class="sxs-lookup"><span data-stu-id="f8525-130">Base class element can specify `MustOverride`, `NotOverridable`, or `Overridable`</span></span>|  
|<span data-ttu-id="f8525-131">キーワードの使用方法</span><span class="sxs-lookup"><span data-stu-id="f8525-131">Keyword usage</span></span>|<span data-ttu-id="f8525-132">派生クラスでは `Shadows` が推奨されます。`Shadows` も `Overrides` も指定されていない場合<sup>2</sup>、`Shadows` と見なされます</span><span class="sxs-lookup"><span data-stu-id="f8525-132">`Shadows` recommended in derived class; `Shadows` assumed if neither `Shadows` nor `Overrides` specified<sup>2</sup></span></span>|<span data-ttu-id="f8525-133">基底クラスでは `Overridable` または `MustOverride` が必要です。派生クラスでは `Overrides` が必要です</span><span class="sxs-lookup"><span data-stu-id="f8525-133">`Overridable` or `MustOverride` required in base class; `Overrides` required in derived class</span></span>|  
|<span data-ttu-id="f8525-134">派生クラスから派生するクラスによる再定義する要素の継承</span><span class="sxs-lookup"><span data-stu-id="f8525-134">Inheritance of redefining element by classes deriving from your derived class</span></span>|<span data-ttu-id="f8525-135">さらに派生したクラスによって継承された要素のシャドウ。シャドウされた要素は引き続き非表示になります<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f8525-135">Shadowing element inherited by further derived classes; shadowed element still hidden<sup>3</sup></span></span>|<span data-ttu-id="f8525-136">さらに派生したクラスによって継承された要素のオーバーライド。オーバーライドされた要素は引き続きオーバーライドされます</span><span class="sxs-lookup"><span data-stu-id="f8525-136">Overriding element inherited by further derived classes; overridden element still overridden</span></span>|  
  
 <span data-ttu-id="f8525-137"><sup>1</sup> *呼び出しシーケンス* は、要素の型 (`Function`、`Sub`、`Operator`、または `Property`)、名前、パラメーター リスト、および戻り値の型から構成されます。</span><span class="sxs-lookup"><span data-stu-id="f8525-137"><sup>1</sup> The *calling sequence* consists of the element type (`Function`, `Sub`, `Operator`, or `Property`), name, parameter list, and return type.</span></span> <span data-ttu-id="f8525-138">プロパティでプロシージャをオーバーライドすることはできません。また、その逆もできません。</span><span class="sxs-lookup"><span data-stu-id="f8525-138">You cannot override a procedure with a property, or the other way around.</span></span> <span data-ttu-id="f8525-139">ある種類のプロシージャ (`Function`、`Sub`、または `Operator`) を別の種類でオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f8525-139">You cannot override one kind of procedure (`Function`, `Sub`, or `Operator`) with another kind.</span></span>  
  
 <span data-ttu-id="f8525-140"><sup>2</sup> `Shadows` または `Overrides` を指定しない場合、使用する再定義の種類を確認できるように、コンパイラによって警告メッセージが発行されます。</span><span class="sxs-lookup"><span data-stu-id="f8525-140"><sup>2</sup> If you do not specify either `Shadows` or `Overrides`, the compiler issues a warning message to help you be sure which kind of redefinition you want to use.</span></span> <span data-ttu-id="f8525-141">警告を無視すると、シャドウ メカニズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f8525-141">If you ignore the warning, the shadowing mechanism is used.</span></span>  
  
 <span data-ttu-id="f8525-142"><sup>3</sup> さらに派生したクラスから、シャドウする要素にアクセスできない場合、シャドウは継承されません。</span><span class="sxs-lookup"><span data-stu-id="f8525-142"><sup>3</sup> If the shadowing element is inaccessible in a further derived class, shadowing is not inherited.</span></span> <span data-ttu-id="f8525-143">たとえば、シャドウする要素を `Private` として宣言した場合、派生クラスから派生したクラスでは、シャドウする要素ではなく元の要素が継承されます。</span><span class="sxs-lookup"><span data-stu-id="f8525-143">For example, if you declare the shadowing element as `Private`, a class deriving from your derived class inherits the original element instead of the shadowing element.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="f8525-144">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="f8525-144">Guidelines</span></span>  

 <span data-ttu-id="f8525-145">通常、オーバーライドは次の場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="f8525-145">You normally use overriding in the following cases:</span></span>  
  
- <span data-ttu-id="f8525-146">ポリモーフィックな派生クラスを定義している。</span><span class="sxs-lookup"><span data-stu-id="f8525-146">You are defining polymorphic derived classes.</span></span>  
  
- <span data-ttu-id="f8525-147">コンパイラに同一の要素型と呼び出しシーケンスを適用させる安全性が必要である。</span><span class="sxs-lookup"><span data-stu-id="f8525-147">You want the safety of having the compiler enforce the identical element type and calling sequence.</span></span>  
  
 <span data-ttu-id="f8525-148">通常、シャドウは次の場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="f8525-148">You normally use shadowing in the following cases:</span></span>  
  
- <span data-ttu-id="f8525-149">基底クラスが変更される可能性があると予想し、自分の要素と同じ名前を使用して要素を定義する。</span><span class="sxs-lookup"><span data-stu-id="f8525-149">You anticipate that your base class might be modified and define an element using the same name as yours.</span></span>  
  
- <span data-ttu-id="f8525-150">要素の型や呼び出しシーケンスを自由に変更したいと考えている。</span><span class="sxs-lookup"><span data-stu-id="f8525-150">You want the freedom of changing the element type or calling sequence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8525-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8525-151">See also</span></span>

- [<span data-ttu-id="f8525-152">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="f8525-152">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="f8525-153">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="f8525-153">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="f8525-154">方法: 自分で宣言した変数と同じ名前の変数を隠す</span><span class="sxs-lookup"><span data-stu-id="f8525-154">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="f8525-155">方法: 継承された変数を隠す</span><span class="sxs-lookup"><span data-stu-id="f8525-155">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="f8525-156">方法: 派生クラスによって非表示になっている変数にアクセスする</span><span class="sxs-lookup"><span data-stu-id="f8525-156">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="f8525-157">Shadows</span><span class="sxs-lookup"><span data-stu-id="f8525-157">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="f8525-158">Overrides</span><span class="sxs-lookup"><span data-stu-id="f8525-158">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
