---
description: '詳細情報: Implements ステートメント'
title: Implements ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: aa53d1f3b4ba9d9111f5ffb09198a11511f8d9e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768988"
---
# <a name="implements-statement"></a><span data-ttu-id="73aab-103">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="73aab-103">Implements Statement</span></span>

<span data-ttu-id="73aab-104">それが存在するクラスまたは構造体の定義に、実装する必要のある 1 つ以上のインターフェイス、つまりインターフェイス メンバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="73aab-104">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73aab-105">構文</span><span class="sxs-lookup"><span data-stu-id="73aab-105">Syntax</span></span>  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="73aab-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="73aab-106">Parts</span></span>  

 `interfacename`  
 <span data-ttu-id="73aab-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="73aab-107">Required.</span></span> <span data-ttu-id="73aab-108">クラスまたは構造体に、対応するメンバーによって実装されるプロパティ、プロシージャ、およびイベントを持つインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="73aab-108">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="73aab-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="73aab-109">Required.</span></span> <span data-ttu-id="73aab-110">実装されるインターフェイスのメンバー。</span><span class="sxs-lookup"><span data-stu-id="73aab-110">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73aab-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="73aab-111">Remarks</span></span>  

 <span data-ttu-id="73aab-112">インターフェイスは、インターフェイスによってカプセル化されるメンバー (プロパティ、プロシージャ、およびイベント) を表すプロトタイプのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="73aab-112">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="73aab-113">インターフェイスには、メンバーの宣言のみが含まれます。クラスと構造体で、これらのメンバーを実装します。</span><span class="sxs-lookup"><span data-stu-id="73aab-113">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="73aab-114">詳細については、「[インターフェイス](../../programming-guide/language-features/interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73aab-114">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="73aab-115">`Implements` ステートメントは、`Class` または `Structure` ステートメントの直後に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73aab-115">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="73aab-116">インターフェイスを実装する場合は、インターフェイスで宣言されたすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73aab-116">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="73aab-117">メンバーを省略すると、構文エラーと見なされます。</span><span class="sxs-lookup"><span data-stu-id="73aab-117">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="73aab-118">個々のメンバーを実装するには、クラスまたは構造体でメンバーを宣言するときに、[Implements](implements-clause.md) キーワード (`Implements` ステートメントとは別) を指定します。</span><span class="sxs-lookup"><span data-stu-id="73aab-118">To implement an individual member, you specify the [Implements](implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="73aab-119">詳細については、「[インターフェイス](../../programming-guide/language-features/interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73aab-119">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="73aab-120">クラスでは、プロパティとプロシージャの [Private](../modifiers/private.md) 実装を使用できますが、インターフェイスの型として宣言された変数に、実装するクラスのインスタンスをキャストすることによってのみ、これらのメンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="73aab-120">Classes can use [Private](../modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73aab-121">例</span><span class="sxs-lookup"><span data-stu-id="73aab-121">Example</span></span>  

 <span data-ttu-id="73aab-122">次の例は、`Implements` ステートメントを使用して、インターフェイスのメンバーを実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="73aab-122">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="73aab-123">これは、イベント、プロパティ、およびプロシージャを含む `ICustomerInfo` という名前のインターフェイスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="73aab-123">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="73aab-124">クラス `customerInfo` では、インターフェイスで定義されているすべてのメンバーを実装します。</span><span class="sxs-lookup"><span data-stu-id="73aab-124">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="73aab-125">クラス `customerInfo` では、別のソース コード行で `Implements` ステートメントを使用して、クラスで `ICustomerInfo` インターフェイスのすべてのメンバーを実装していることを示していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="73aab-125">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="73aab-126">次に、クラスの各メンバーで、そのメンバー宣言の一部として `Implements` キーワードを使用して、そのインターフェイス　メンバーを実装していることを示しています。</span><span class="sxs-lookup"><span data-stu-id="73aab-126">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73aab-127">例</span><span class="sxs-lookup"><span data-stu-id="73aab-127">Example</span></span>  

 <span data-ttu-id="73aab-128">次の 2 つのプロシージャでは、前の例で実装したインターフェイスを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="73aab-128">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="73aab-129">実装をテストするには、これらのプロシージャをプロジェクトに追加し、`testImplements` プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="73aab-129">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="73aab-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="73aab-130">See also</span></span>

- [<span data-ttu-id="73aab-131">Implements</span><span class="sxs-lookup"><span data-stu-id="73aab-131">Implements</span></span>](implements-clause.md)
- [<span data-ttu-id="73aab-132">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="73aab-132">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="73aab-133">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73aab-133">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
