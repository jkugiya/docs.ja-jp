---
description: '詳細情報: その他のデータ型 (Visual Basic)'
title: その他のデータ型
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 3875a3fc3027d573013470cb96c9482a0be6cbbf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461997"
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="39d4a-103">その他のデータ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d4a-103">Miscellaneous Data Types (Visual Basic)</span></span>

<span data-ttu-id="39d4a-104">Visual Basic には、数値や文字を対象としていない複数のデータ型が用意されています。</span><span class="sxs-lookup"><span data-stu-id="39d4a-104">Visual Basic supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="39d4a-105">これらは、yes/no の値、日付/時刻の値、オブジェクト アドレスなど、特殊なデータを扱います。</span><span class="sxs-lookup"><span data-stu-id="39d4a-105">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="39d4a-106">Visual Basic データ型を並べて比較している表を、[データ型](../../../language-reference/data-types/index.md)に関するページで参照してください。</span><span class="sxs-lookup"><span data-stu-id="39d4a-106">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="39d4a-107">ブール型</span><span class="sxs-lookup"><span data-stu-id="39d4a-107">Boolean Type</span></span>  

 <span data-ttu-id="39d4a-108">[Boolean データ型](../../../language-reference/data-types/boolean-data-type.md)は、`True` または `False` と解釈される符号なしの値です。</span><span class="sxs-lookup"><span data-stu-id="39d4a-108">The [Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="39d4a-109">データ幅は、実装するプラットフォームによって異なります。</span><span class="sxs-lookup"><span data-stu-id="39d4a-109">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="39d4a-110">変数が 2 つの状態 (true/false、yes/no、on/off など) の値のみを含む可能性がある場合は、`Boolean` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="39d4a-110">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="39d4a-111">日付型</span><span class="sxs-lookup"><span data-stu-id="39d4a-111">Date Type</span></span>  

 <span data-ttu-id="39d4a-112">[Date データ型](../../../language-reference/data-types/date-data-type.md)は、日付と時刻の両方の情報を保持する 64 ビット値です。</span><span class="sxs-lookup"><span data-stu-id="39d4a-112">The [Date Data Type](../../../language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="39d4a-113">各インクリメントはグレゴリオ暦の西暦 1 年 1 月 1 日 (午前 12:00) からの経過時間を 100 ナノ秒単位で表します。</span><span class="sxs-lookup"><span data-stu-id="39d4a-113">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="39d4a-114">変数が日付値、時刻値、またはその両方を含む可能性がある場合は、`Date` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="39d4a-114">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="39d4a-115">オブジェクトの型</span><span class="sxs-lookup"><span data-stu-id="39d4a-115">Object Type</span></span>  

 <span data-ttu-id="39d4a-116">[Object データ型](../../../language-reference/data-types/object-data-type.md)は、自らのアプリケーションまたはその他のアプリケーション内のオブジェクト インスタンスを指す 32 ビットのアドレスです。</span><span class="sxs-lookup"><span data-stu-id="39d4a-116">The [Object Data Type](../../../language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="39d4a-117">`Object` 変数は、アプリケーションによって認識される任意のオブジェクト、または任意のデータ型のデータを参照できます。</span><span class="sxs-lookup"><span data-stu-id="39d4a-117">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="39d4a-118">これには、"*値型*" (`Integer`、`Boolean`、構造体インスタンスなど) と "*参照型*" (`String` や <xref:System.Windows.Forms.Form>などのクラスから作成されるオブジェクトのインスタンスおよび配列インスタンス) の両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39d4a-118">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="39d4a-119">変数に含まれるポインターが、コンパイル時にはわからないクラスのインスタンスを指している場合、またはさまざまなデータ型の値を指す可能性がある場合は、`Object` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="39d4a-119">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="39d4a-120">`Object` データ型の利点は、任意のデータ型のデータを格納するために使用できることです。</span><span class="sxs-lookup"><span data-stu-id="39d4a-120">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="39d4a-121">欠点は、実行時間が長くなる追加処理が発生し、アプリケーションのパフォーマンスが低下することです。</span><span class="sxs-lookup"><span data-stu-id="39d4a-121">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="39d4a-122">値型の `Object` 変数を使用すると、"*ボックス化*" と "*ボックス化解除*" が発生します。</span><span class="sxs-lookup"><span data-stu-id="39d4a-122">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="39d4a-123">参照型に対して使用すると、"*遅延バインディング*" が発生します。</span><span class="sxs-lookup"><span data-stu-id="39d4a-123">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d4a-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="39d4a-124">See also</span></span>

- [<span data-ttu-id="39d4a-125">型文字</span><span class="sxs-lookup"><span data-stu-id="39d4a-125">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="39d4a-126">基本データ型</span><span class="sxs-lookup"><span data-stu-id="39d4a-126">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="39d4a-127">数値のデータ型</span><span class="sxs-lookup"><span data-stu-id="39d4a-127">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="39d4a-128">文字データ型</span><span class="sxs-lookup"><span data-stu-id="39d4a-128">Character Data Types</span></span>](character-data-types.md)
- [<span data-ttu-id="39d4a-129">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="39d4a-129">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="39d4a-130">事前バインディングと遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="39d4a-130">Early and Late Binding</span></span>](../early-late-binding/index.md)
