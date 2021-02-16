---
description: '詳細情報: Visual Basic における Me、My、MyBase、MyClass'
title: Me、My、MyBase、および MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: 04be6cc7063101a59838bf809731a66c27007283
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432794"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="9583e-103">Visual Basic における Me、My、MyBase、MyClass</span><span class="sxs-lookup"><span data-stu-id="9583e-103">Me, My, MyBase, and MyClass in Visual Basic</span></span>

<span data-ttu-id="9583e-104">Visual Basic の `Me`、`My`、`MyBase`、`MyClass` は、名前は似ていますが目的が異なります。</span><span class="sxs-lookup"><span data-stu-id="9583e-104">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="9583e-105">このトピックでは、これらのエンティティを区別するために、それぞれについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9583e-105">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="9583e-106">Me</span><span class="sxs-lookup"><span data-stu-id="9583e-106">Me</span></span>  

 <span data-ttu-id="9583e-107">`Me` キーワードを使用すると、コードが現在実行されている、クラスまたは構造体の特定のインスタンスを参照できます。</span><span class="sxs-lookup"><span data-stu-id="9583e-107">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="9583e-108">`Me` は、現在のインスタンスを参照するオブジェクト変数または構造体変数と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="9583e-108">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="9583e-109">`Me` の使用は、クラスまたは構造体の現在実行されているインスタンスに関する情報を、別のクラス、構造体、またはモジュールのプロシージャに渡す際に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9583e-109">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="9583e-110">たとえば、モジュールに次のプロシージャがあるとします。</span><span class="sxs-lookup"><span data-stu-id="9583e-110">For example, suppose you have the following procedure in a module.</span></span>  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="9583e-111">このプロシージャを呼び出し、次のステートメントを使用して、<xref:System.Windows.Forms.Form> クラスの現在のインスタンスを引数として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="9583e-111">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="9583e-112">My</span><span class="sxs-lookup"><span data-stu-id="9583e-112">My</span></span>  

 <span data-ttu-id="9583e-113">`My` 機能を使用すると、多数の .NET Framework クラスに簡単かつ直感的にアクセスできるので、Visual Basic ユーザーはコンピューター、アプリケーション、設定、リソースなどを操作できます。</span><span class="sxs-lookup"><span data-stu-id="9583e-113">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="9583e-114">MyBase</span><span class="sxs-lookup"><span data-stu-id="9583e-114">MyBase</span></span>  

 <span data-ttu-id="9583e-115">`MyBase` キーワードは、クラスの現在のインスタンスの基底クラスを参照するオブジェクト変数と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="9583e-115">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="9583e-116">`MyBase` は、派生クラスでオーバーライドまたはシャドウされた基底クラスのメンバーにアクセスするためによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="9583e-116">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="9583e-117">`MyBase.New` は、派生クラスのコンストラクターから基底クラスのコンストラクターを明示的に呼び出すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9583e-117">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="9583e-118">MyClass</span><span class="sxs-lookup"><span data-stu-id="9583e-118">MyClass</span></span>  

 <span data-ttu-id="9583e-119">`MyClass` キーワードは、もともと実装されているクラスの現在のインスタンスを参照するオブジェクト変数と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="9583e-119">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="9583e-120">`MyClass` は `Me` に似ていますが、これに対するすべてのメソッド呼び出しは、メソッドが `NotOverridable` であるかのように扱われます。</span><span class="sxs-lookup"><span data-stu-id="9583e-120">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9583e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9583e-121">See also</span></span>

- [<span data-ttu-id="9583e-122">継承の基本</span><span class="sxs-lookup"><span data-stu-id="9583e-122">Inheritance Basics</span></span>](../language-features/objects-and-classes/inheritance-basics.md)
