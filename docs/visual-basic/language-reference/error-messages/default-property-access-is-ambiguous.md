---
description: "詳細情報: BC30686:Default プロパティ アクセスは、インターフェイス '<defaultpropertyname>' の継承インターフェイス メンバー '<interfacename1>' とインターフェイス '<defaultpropertyname>' の '<interfacename2>' との間で不適切です。"
title: Default プロパティ アクセスは、インターフェイス '<defaultpropertyname>' の継承インターフェイス メンバー '<interfacename1>' とインターフェイス '<defaultpropertyname>' の '<interfacename2>' との間で不適切です。
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: edf2823fb11184efb2c3101b81119ea1696234db
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455224"
---
# <a name="bc30686-default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="3e581-103">BC30686:Default プロパティ アクセスは、インターフェイス '\<defaultpropertyname>' の継承インターフェイス メンバー '\<interfacename1>' とインターフェイス '\<defaultpropertyname>' の '\<interfacename2>' との間で不適切です。</span><span class="sxs-lookup"><span data-stu-id="3e581-103">BC30686: Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>

<span data-ttu-id="3e581-104">インターフェイスは、それぞれが同じ名前の既定のプロパティを宣言する 2 つのインターフェイスから継承します。</span><span class="sxs-lookup"><span data-stu-id="3e581-104">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="3e581-105">コンパイラは、この既定のプロパティへのアクセスを修飾なしで解決することはできません。</span><span class="sxs-lookup"><span data-stu-id="3e581-105">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="3e581-106">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="3e581-106">The following example illustrates this.</span></span>

```vb
Public Interface Iface1
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface2
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface3
    Inherits Iface1, Iface2
End Interface
Public Class testClass
    Public Sub accessDefaultProperty()
        Dim testObj As Iface3
        Dim testInt As Integer = testObj(1)
    End Sub
End Class
```

<span data-ttu-id="3e581-107">`testObj(1)` を指定すると、コンパイラは、それを既定のプロパティに解決しようとします。</span><span class="sxs-lookup"><span data-stu-id="3e581-107">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="3e581-108">ただし、継承されたインターフェイスにより 2 つの既定のプロパティが考えられるため、コンパイラがこのエラーを通知します。</span><span class="sxs-lookup"><span data-stu-id="3e581-108">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>

<span data-ttu-id="3e581-109">**エラー ID:** BC30686</span><span class="sxs-lookup"><span data-stu-id="3e581-109">**Error ID:** BC30686</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3e581-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3e581-110">To correct this error</span></span>

- <span data-ttu-id="3e581-111">同じ名前のメンバーを継承しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="3e581-111">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="3e581-112">前の例では、`testObj` が、メンバーのいずれか (たとえば `Iface2`) を必要としない場合は、次のように宣言します。</span><span class="sxs-lookup"><span data-stu-id="3e581-112">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>

  ```vb
  Dim testObj As Iface1
  ```

  <span data-ttu-id="3e581-113">\- または -</span><span class="sxs-lookup"><span data-stu-id="3e581-113">\-or-</span></span>

- <span data-ttu-id="3e581-114">クラスに継承するインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="3e581-114">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="3e581-115">その後、異なる名前を持つ継承されたプロパティのそれぞれを実装できます。</span><span class="sxs-lookup"><span data-stu-id="3e581-115">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="3e581-116">ただし、実装するクラスの既定のプロパティにすることができるのは、そのうちの 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="3e581-116">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="3e581-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="3e581-117">The following example illustrates this.</span></span>

  ```vb
  Public Class useIface3
      Implements Iface3
      Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop
          ' Insert code to define Get and Set procedures for prop1.
      End Property
      Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop
          ' Insert code to define Get and Set procedures for prop2.
      End Property
  End Class
  ```

## <a name="see-also"></a><span data-ttu-id="3e581-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e581-118">See also</span></span>

- [<span data-ttu-id="3e581-119">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e581-119">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
