---
description: '詳細情報: 構造体およびその他のプログラミング要素 (Visual Basic)'
title: 構造体とその他のプログラミング要素
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 62052389b617849566a3cd0c475a2eb5da9e61ca
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430587"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="06f94-103">構造体およびその他のプログラミング要素 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06f94-103">Structures and Other Programming Elements (Visual Basic)</span></span>

<span data-ttu-id="06f94-104">構造体は、配列、オブジェクト、およびプロシージャと組み合わせて使用したり、相互に使用し合ったりすることができます。</span><span class="sxs-lookup"><span data-stu-id="06f94-104">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="06f94-105">この相互作用には、これらの要素で個別に使用されるものと同じ構文が使用されます。</span><span class="sxs-lookup"><span data-stu-id="06f94-105">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06f94-106">構造体宣言で構造体の要素を初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="06f94-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="06f94-107">構造型であると宣言されている変数の要素にのみ、値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="06f94-107">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="06f94-108">構造体と配列</span><span class="sxs-lookup"><span data-stu-id="06f94-108">Structures and Arrays</span></span>  

 <span data-ttu-id="06f94-109">構造体には、配列を 1 つ以上の要素として含めることができます。</span><span class="sxs-lookup"><span data-stu-id="06f94-109">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="06f94-110">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="06f94-110">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 <span data-ttu-id="06f94-111">構造体内の配列の値には、オブジェクトのプロパティにアクセスする場合と同じ方法でアクセスします。</span><span class="sxs-lookup"><span data-stu-id="06f94-111">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="06f94-112">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="06f94-112">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="06f94-113">構造体の配列を宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="06f94-113">You can also declare an array of structures.</span></span> <span data-ttu-id="06f94-114">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="06f94-114">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="06f94-115">同じ規則に従って、このデータ アーキテクチャのコンポーネントにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="06f94-115">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="06f94-116">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="06f94-116">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="06f94-117">構造体とオブジェクト</span><span class="sxs-lookup"><span data-stu-id="06f94-117">Structures and Objects</span></span>  

 <span data-ttu-id="06f94-118">構造体には、オブジェクトを 1 つ以上の要素として含めることができます。</span><span class="sxs-lookup"><span data-stu-id="06f94-118">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="06f94-119">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="06f94-119">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="06f94-120">このような宣言では、`Object` ではなく特定のオブジェクト クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06f94-120">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="06f94-121">構造体とプロシージャ</span><span class="sxs-lookup"><span data-stu-id="06f94-121">Structures and Procedures</span></span>  

 <span data-ttu-id="06f94-122">プロシージャ引数として構造体を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="06f94-122">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="06f94-123">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="06f94-123">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="06f94-124">前の例では、"*参照渡し*" で構造体を渡しています。こうすることで、呼び出し元のコードで変更が有効になるように、プロシージャでその要素を変更できます。</span><span class="sxs-lookup"><span data-stu-id="06f94-124">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="06f94-125">このような変更から構造体を保護する場合は、値で渡します。</span><span class="sxs-lookup"><span data-stu-id="06f94-125">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="06f94-126">`Function` プロシージャから構造体を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="06f94-126">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="06f94-127">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="06f94-127">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a><span data-ttu-id="06f94-128">構造体内の構造体</span><span class="sxs-lookup"><span data-stu-id="06f94-128">Structures Within Structures</span></span>  

 <span data-ttu-id="06f94-129">構造体には他の構造体を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="06f94-129">Structures can contain other structures.</span></span> <span data-ttu-id="06f94-130">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="06f94-130">The following example illustrates this.</span></span>  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 <span data-ttu-id="06f94-131">この手法を使用して、あるモジュールで定義された構造体を別のモジュールで定義された構造体内にカプセル化することもできます。</span><span class="sxs-lookup"><span data-stu-id="06f94-131">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="06f94-132">構造体には、任意の深さで他の構造体を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="06f94-132">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f94-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="06f94-133">See also</span></span>

- [<span data-ttu-id="06f94-134">データの種類</span><span class="sxs-lookup"><span data-stu-id="06f94-134">Data Types</span></span>](index.md)
- [<span data-ttu-id="06f94-135">基本データ型</span><span class="sxs-lookup"><span data-stu-id="06f94-135">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="06f94-136">複合データ型</span><span class="sxs-lookup"><span data-stu-id="06f94-136">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="06f94-137">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="06f94-137">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="06f94-138">構造体</span><span class="sxs-lookup"><span data-stu-id="06f94-138">Structures</span></span>](structures.md)
- [<span data-ttu-id="06f94-139">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="06f94-139">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="06f94-140">方法: 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="06f94-140">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="06f94-141">構造体変数</span><span class="sxs-lookup"><span data-stu-id="06f94-141">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="06f94-142">構造体とクラス</span><span class="sxs-lookup"><span data-stu-id="06f94-142">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="06f94-143">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="06f94-143">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
