---
description: 詳細については、「' Object ' 型の引数を使用する場合は、' FilePut ' ではなく ' FilePutObject ' を使用する」を参照してください。
title: 型 'Object' の引数を使う場合は、'FilePut' ではなく 'FilePutObject' を使用してください。
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 5e5822999aa39bff4d43f83a2719341034cdcadc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460099"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="d1219-103">型 'Object' の引数を使う場合は、'FilePut' ではなく 'FilePutObject' を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d1219-103">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>

<span data-ttu-id="d1219-104">`FilePut` メソッドには、型 `Object`の引数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1219-104">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="d1219-105">あいまいさを避けるため、`FilePutObject` の代わりに `FilePut` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1219-105">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1219-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d1219-106">To correct this error</span></span>  
  
- <span data-ttu-id="d1219-107">`FilePut` を `FilePutObject` で置き換え</span><span class="sxs-lookup"><span data-stu-id="d1219-107">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="d1219-108">`Object` 引数をより具体的な種類にキャストします。</span><span class="sxs-lookup"><span data-stu-id="d1219-108">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="d1219-109">`My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1219-109">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1219-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1219-110">See also</span></span>

- [<span data-ttu-id="d1219-111">マイファイル (コンピューター)</span><span class="sxs-lookup"><span data-stu-id="d1219-111">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="d1219-112">My. Computer. FileSystem. WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="d1219-112">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
