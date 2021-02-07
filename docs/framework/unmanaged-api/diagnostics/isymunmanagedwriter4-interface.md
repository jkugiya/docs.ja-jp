---
description: 詳細については、「ISymUnmanagedWriter4 インターフェイス」を参照してください。
title: ISymUnmanagedWriter4 インターフェイス
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: 3814d7e2728f28d224a4e9a6d99f699f220e8a4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761682"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="744a6-103">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="744a6-103">ISymUnmanagedWriter4 Interface</span></span>

<span data-ttu-id="744a6-104">ISymUnmanagedWriter4 インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="744a6-104">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="744a6-105">構文</span><span class="sxs-lookup"><span data-stu-id="744a6-105">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="744a6-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="744a6-106">Methods</span></span>  

 <span data-ttu-id="744a6-107">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="744a6-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="744a6-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="744a6-108">Method</span></span>|<span data-ttu-id="744a6-109">説明</span><span class="sxs-lookup"><span data-stu-id="744a6-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="744a6-110">GetDebugInfoWithPadding メソッド</span><span class="sxs-lookup"><span data-stu-id="744a6-110">GetDebugInfoWithPadding Method</span></span>](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="744a6-111">関数は [GetDebugInfo メソッド](isymunmanagedwriter-getdebuginfo-method.md) と同じですが、文字列データを固定サイズにするために、終端の null 文字の後にパス文字列がゼロで埋め込まれる点が異なり `MAX_PATH` ます。</span><span class="sxs-lookup"><span data-stu-id="744a6-111">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="744a6-112">埋め込みは、パス文字列の長さがより小さい場合にのみ指定 `MAX_PATH` します。</span><span class="sxs-lookup"><span data-stu-id="744a6-112">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="744a6-113">これにより、PE ファイルを区別するツールを簡単に記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="744a6-113">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="744a6-114">要件</span><span class="sxs-lookup"><span data-stu-id="744a6-114">Requirements</span></span>  

 <span data-ttu-id="744a6-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="744a6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744a6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="744a6-116">See also</span></span>

- [<span data-ttu-id="744a6-117">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="744a6-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="744a6-118">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="744a6-118">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
