---
description: 詳細については、「' Object ' 型の引数を使用するときに ' FileGet ' ではなく ' FileGetObject ' を使用する」を参照してください。
title: 型 'Object' の引数を使用する場合は、'FileGet' ではなく 'FileGetObject' を使用してください。
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 4481fdced961cacf0e652c141601efa13bec776b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471163"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="cc13c-103">型 'Object' の引数を使用する場合は、'FileGet' ではなく 'FileGetObject' を使用してください。</span><span class="sxs-lookup"><span data-stu-id="cc13c-103">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>

<span data-ttu-id="cc13c-104">`FileGet` メソッドには、型 `Object`の引数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc13c-104">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="cc13c-105">あいまいさを避けるため、`FileGetObject` の代わりに `FileGet` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc13c-105">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="cc13c-106">`My.Computer.Filesystem` によって提供される機能は、`FileGet` または `FileGetObject` よりも使いやすく、パフォーマンスが優れています。</span><span class="sxs-lookup"><span data-stu-id="cc13c-106">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc13c-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="cc13c-107">To correct this error</span></span>  
  
1. <span data-ttu-id="cc13c-108">`FileGet` を `FileGetObject` で置き換え</span><span class="sxs-lookup"><span data-stu-id="cc13c-108">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2. <span data-ttu-id="cc13c-109">`Object` 引数をより具体的な種類にキャストします。</span><span class="sxs-lookup"><span data-stu-id="cc13c-109">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc13c-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc13c-110">See also</span></span>

- [<span data-ttu-id="cc13c-111">マイファイル (コンピューター)</span><span class="sxs-lookup"><span data-stu-id="cc13c-111">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
