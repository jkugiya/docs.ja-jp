---
description: '詳細情報: 方法:オブジェクト変数がインスタンスを参照しないようにする (Visual Basic)'
title: '方法: オブジェクト変数がインスタンスを参照しないようにする'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 2897720b52e708847fdd139be512e578a7420241
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481871"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="4d1aa-103">方法: オブジェクト変数がインスタンスを参照しないようにする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d1aa-103">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>

<span data-ttu-id="4d1aa-104">オブジェクト変数を [Nothing](../../../language-reference/nothing.md) に設定すると、任意のオブジェクト インスタンスとの関連付けを解除できます。</span><span class="sxs-lookup"><span data-stu-id="4d1aa-104">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="4d1aa-105">オブジェクト変数とオブジェクト インスタンスの関連付けを解除するには</span><span class="sxs-lookup"><span data-stu-id="4d1aa-105">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="4d1aa-106">代入ステートメントで変数を `Nothing` に設定します。</span><span class="sxs-lookup"><span data-stu-id="4d1aa-106">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="4d1aa-107">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="4d1aa-107">Robust Programming</span></span>  

 <span data-ttu-id="4d1aa-108">コードで、`Nothing` に設定されているオブジェクト変数のメンバーにアクセスしようとすると、<xref:System.NullReferenceException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="4d1aa-108">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="4d1aa-109">オブジェクト変数を頻繁に `Nothing` に設定する場合、または変数が初期化されていない可能性がある場合は、メンバー アクセスを `Try...Catch...Finally` ブロックで囲むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4d1aa-109">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4d1aa-110">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4d1aa-110">.NET Framework Security</span></span>  

 <span data-ttu-id="4d1aa-111">機密データを含むオブジェクトに対してオブジェクト変数を使用する場合は、これらのオブジェクトのいずれかをアクティブに処理していないときに、この変数を `Nothing` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="4d1aa-111">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="4d1aa-112">これにより、悪意のあるコードからデータにアクセスされる可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="4d1aa-112">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1aa-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d1aa-113">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="4d1aa-114">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="4d1aa-114">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="4d1aa-115">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="4d1aa-115">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="4d1aa-116">Nothing</span><span class="sxs-lookup"><span data-stu-id="4d1aa-116">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="4d1aa-117">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="4d1aa-117">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
