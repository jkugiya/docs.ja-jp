---
title: コピー コンストラクターを記述する方法 - C# プログラミング ガイド
description: クラスのインスタンスを受け取り、入力の値を使用して新しいインスタンスを返すコピー コンストラクターを C# で記述する方法について説明します。
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: c61018444dd600d6f33765b104034355d0301667
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255237"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="7c0e0-103">コピー コンストラクターを記述する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="7c0e0-103">How to write a copy constructor (C# Programming Guide)</span></span>

<span data-ttu-id="7c0e0-104">オブジェクトには C# [レコード](records.md)によってコピー コンストラクターが提供されますが、クラスには自分でそれを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c0e0-104">C# [records](records.md) provide a copy constructor for objects, but for classes you have to write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c0e0-105">例</span><span class="sxs-lookup"><span data-stu-id="7c0e0-105">Example</span></span>  

 <span data-ttu-id="7c0e0-106">次の例の `Person`[クラス](../../language-reference/keywords/class.md)では、`Person` のインスタンスを引数として受け取るコピー コンストラクターが定義されています。</span><span class="sxs-lookup"><span data-stu-id="7c0e0-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="7c0e0-107">引数のプロパティの値は、`Person`の新しいインスタンスのプロパティに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="7c0e0-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="7c0e0-108">このコードには、コピーするインスタンスの `Name` プロパティと `Age` プロパティをクラスのインスタンス コンストラクターに渡す代替のコピー コンストラクターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c0e0-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[CopyConstructor](snippets/how-to-write-a-copy-constructor/Program.cs)]

## <a name="see-also"></a><span data-ttu-id="7c0e0-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c0e0-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="7c0e0-110">レコード</span><span class="sxs-lookup"><span data-stu-id="7c0e0-110">Records</span></span>](records.md)
- [<span data-ttu-id="7c0e0-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="7c0e0-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7c0e0-112">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="7c0e0-112">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="7c0e0-113">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="7c0e0-113">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="7c0e0-114">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="7c0e0-114">Finalizers</span></span>](./destructors.md)
