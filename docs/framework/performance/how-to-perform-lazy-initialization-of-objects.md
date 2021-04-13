---
title: '方法: オブジェクトの遅延初期化を実行する'
description: System.Lazy<T> クラスを使用してオブジェクトの遅延初期化を実行する方法をご覧ください。 遅延初期化は、不要なオブジェクトが作成されないことを意味します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
ms.openlocfilehash: 3de0d8ea8266931c2bcda5c59c1fef97602673d5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278129"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a><span data-ttu-id="46928-104">方法: オブジェクトの遅延初期化を実行する</span><span class="sxs-lookup"><span data-stu-id="46928-104">How to: Perform Lazy Initialization of Objects</span></span>

<span data-ttu-id="46928-105"><xref:System.Lazy%601?displayProperty=nameWithType> クラスは、オブジェクトの遅延初期化とインスタンス化を実行する操作を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="46928-105">The <xref:System.Lazy%601?displayProperty=nameWithType> class simplifies the work of performing lazy initialization and instantiation of objects.</span></span> <span data-ttu-id="46928-106">オブジェクトを限定的に初期化すれば、不要なオブジェクトを作成する必要がなくなります。また、オブジェクトに初めてアクセスするときまで、そのオブジェクトの初期化を延期できます。</span><span class="sxs-lookup"><span data-stu-id="46928-106">By initializing objects in a lazy manner, you can avoid having to create them at all if they are never needed, or you can postpone their initialization until they are first accessed.</span></span> <span data-ttu-id="46928-107">詳細については、「[限定的な初期化](lazy-initialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46928-107">For more information, see [Lazy Initialization](lazy-initialization.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="46928-108">例</span><span class="sxs-lookup"><span data-stu-id="46928-108">Example</span></span>  

 <span data-ttu-id="46928-109">次の例では、<xref:System.Lazy%601> で値を初期化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="46928-109">The following example shows how to initialize a value with <xref:System.Lazy%601>.</span></span> <span data-ttu-id="46928-110">`someCondition` 変数を true または false に設定する他の一部のコードでは、遅延変数は必要ないものとします。</span><span class="sxs-lookup"><span data-stu-id="46928-110">Assume that the lazy variable might not be needed, depending on some other code that sets the `someCondition` variable to true or false.</span></span>  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
  {  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
  }  
```  
  
## <a name="example"></a><span data-ttu-id="46928-111">例</span><span class="sxs-lookup"><span data-stu-id="46928-111">Example</span></span>  

 <span data-ttu-id="46928-112">次の例では、<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> クラスを使用して、現在のスレッド上の現在のオブジェクト インスタンスでのみ表示される型を初期化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="46928-112">The following example shows how to use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to initialize a type that is visible only to the current object instance on the current thread.</span></span>  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="46928-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="46928-113">See also</span></span>

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [<span data-ttu-id="46928-114">限定的な初期化</span><span class="sxs-lookup"><span data-stu-id="46928-114">Lazy Initialization</span></span>](lazy-initialization.md)
