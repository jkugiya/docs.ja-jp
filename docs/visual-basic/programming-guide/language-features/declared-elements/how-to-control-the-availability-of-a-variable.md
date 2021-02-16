---
description: '詳細情報: 方法:変数の可用性を制御する (Visual Basic)'
title: '方法: 変数の可用性を制御する'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 3fa21a804008f31da9003aa847752f749154d602
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429885"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="c1da7-103">方法: 変数の可用性を制御する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1da7-103">How to: Control the Availability of a Variable (Visual Basic)</span></span>

<span data-ttu-id="c1da7-104">変数の可用性を制御するには、その *アクセス レベル* を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1da7-104">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="c1da7-105">アクセス レベルによって、変数への読み取りまたは書き込みのアクセス許可を持つコードが決まります。</span><span class="sxs-lookup"><span data-stu-id="c1da7-105">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="c1da7-106">*メンバー変数* (モジュール レベルのプロシージャの外部で定義される) は、既定でパブリック アクセスになります。これは、それらを参照できるすべてのコードで、それらにアクセスできることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c1da7-106">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="c1da7-107">これを変更するには、アクセス修飾子を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1da7-107">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="c1da7-108">*ローカル変数* (プロシージャ内に定義) は、名目上パブリック アクセス権を持ちますが、それらのプロシージャ内のコードだけがそれらにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c1da7-108">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="c1da7-109">ローカル変数のアクセス レベルを変更することはできませんが、それを含むプロシージャのアクセス レベルを変更することはできます。</span><span class="sxs-lookup"><span data-stu-id="c1da7-109">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="c1da7-110">詳しくは、「[Visual Basic でのアクセス レベル](access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1da7-110">For more information, see [Access levels in Visual Basic](access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="c1da7-111">プライベート アクセスとパブリック アクセス</span><span class="sxs-lookup"><span data-stu-id="c1da7-111">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="c1da7-112">変数をそのモジュール、クラス、または構造体内からのみアクセスできるようにするには</span><span class="sxs-lookup"><span data-stu-id="c1da7-112">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="c1da7-113">モジュール、クラス、または構造体の内部で、ただしプロシージャの外部に、変数の [Dim ステートメント](../../../language-reference/statements/dim-statement.md)を配置します。</span><span class="sxs-lookup"><span data-stu-id="c1da7-113">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="c1da7-114">`Dim` ステートメントに [Private](../../../language-reference/modifiers/private.md) キーワードを含めます。</span><span class="sxs-lookup"><span data-stu-id="c1da7-114">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="c1da7-115">変数の読み取りや書き込みは、モジュール、クラス、または構造体内のどこからでも行うことができますが、その外部から行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="c1da7-115">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="c1da7-116">変数を参照できるすべてのコードから変数にアクセスできるようにするには</span><span class="sxs-lookup"><span data-stu-id="c1da7-116">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="c1da7-117">メンバー変数の場合、変数の `Dim` ステートメントをモジュール、クラス、または構造体の内部で、ただしプロシージャの外部に配置します。</span><span class="sxs-lookup"><span data-stu-id="c1da7-117">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="c1da7-118">`Dim` ステートメントに [Public](../../../language-reference/modifiers/public.md) キーワードを含めます。</span><span class="sxs-lookup"><span data-stu-id="c1da7-118">Include the [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="c1da7-119">アセンブリと相互運用するすべてのコードから変数の読み取りや書き込みができます。</span><span class="sxs-lookup"><span data-stu-id="c1da7-119">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="c1da7-120">\- または -</span><span class="sxs-lookup"><span data-stu-id="c1da7-120">-or-</span></span>  
  
1. <span data-ttu-id="c1da7-121">ローカル変数の場合は、プロシージャ内に変数の `Dim` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="c1da7-121">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="c1da7-122">`Dim` ステートメントには `Public` キーワードを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="c1da7-122">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="c1da7-123">変数の読み取りや書き込みは、プロシージャ内のどこからでも行うことができますが、その外部から行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="c1da7-123">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="c1da7-124">Protected アクセスと Friend アクセス</span><span class="sxs-lookup"><span data-stu-id="c1da7-124">Protected and Friend Access</span></span>  

 <span data-ttu-id="c1da7-125">変数のアクセス レベルは、そのクラス、任意の派生クラス、またはそのアセンブリに制限できます。</span><span class="sxs-lookup"><span data-stu-id="c1da7-125">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="c1da7-126">また、これらの制限の和集合を指定することもできます。これにより、任意の派生クラスまたは同じアセンブリ内の他の任意の場所のコードからアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="c1da7-126">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="c1da7-127">この和集合を指定するには、同じ宣言で `Protected` キーワードと `Friend` キーワードを組み合わせます。</span><span class="sxs-lookup"><span data-stu-id="c1da7-127">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="c1da7-128">そのクラスと任意の派生クラス内からのみ変数にアクセスできるようにするには</span><span class="sxs-lookup"><span data-stu-id="c1da7-128">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="c1da7-129">変数の `Dim` ステートメントをクラス内、ただしプロシージャの外部に配置します。</span><span class="sxs-lookup"><span data-stu-id="c1da7-129">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="c1da7-130">`Dim` ステートメントに [Protected](../../../language-reference/modifiers/protected.md) キーワードを含めます。</span><span class="sxs-lookup"><span data-stu-id="c1da7-130">Include the [Protected](../../../language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="c1da7-131">変数の読み取りや書き込みは、クラス内のどこからでも、また、それから派生した任意のクラス内から行うことができますが、派生チェーン内のクラスの外部から行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="c1da7-131">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="c1da7-132">同じアセンブリ内からのみ変数にアクセスできるようにするには</span><span class="sxs-lookup"><span data-stu-id="c1da7-132">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="c1da7-133">モジュール、クラス、または構造体の内部で、ただしプロシージャの外部に、変数の `Dim` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="c1da7-133">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="c1da7-134">`Dim` ステートメントに [Friend](../../../language-reference/modifiers/friend.md) キーワードを含めます。</span><span class="sxs-lookup"><span data-stu-id="c1da7-134">Include the [Friend](../../../language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="c1da7-135">変数の読み取りや書き込みは、モジュール、クラス、または構造体内のどこからでも、また同じアセンブリ内の任意のコードから行うことができますが、アセンブリの外部から行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="c1da7-135">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1da7-136">例</span><span class="sxs-lookup"><span data-stu-id="c1da7-136">Example</span></span>  

 <span data-ttu-id="c1da7-137">次の例は、`Public`、`Protected`、`Friend`、`Protected Friend`、および `Private` アクセス レベルによる変数の宣言を示しています。</span><span class="sxs-lookup"><span data-stu-id="c1da7-137">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="c1da7-138">`Dim` ステートメントでアクセス レベルを指定する場合は、`Dim` キーワードを含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c1da7-138">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="c1da7-139">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c1da7-139">.NET Framework Security</span></span>  

 <span data-ttu-id="c1da7-140">変数のアクセス レベルの制限を強めるほど、悪意のあるコードによってそれが不正使用される可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="c1da7-140">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1da7-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1da7-141">See also</span></span>

- [<span data-ttu-id="c1da7-142">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="c1da7-142">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="c1da7-143">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="c1da7-143">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="c1da7-144">Public</span><span class="sxs-lookup"><span data-stu-id="c1da7-144">Public</span></span>](../../../language-reference/modifiers/public.md)
- [<span data-ttu-id="c1da7-145">Protected</span><span class="sxs-lookup"><span data-stu-id="c1da7-145">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="c1da7-146">Friend</span><span class="sxs-lookup"><span data-stu-id="c1da7-146">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="c1da7-147">Private</span><span class="sxs-lookup"><span data-stu-id="c1da7-147">Private</span></span>](../../../language-reference/modifiers/private.md)
