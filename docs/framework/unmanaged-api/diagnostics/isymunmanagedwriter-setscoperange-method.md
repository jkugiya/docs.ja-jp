---
description: '詳細について: ISymUnmanagedWriter:: SetScopeRange メソッド'
title: ISymUnmanagedWriter::SetScopeRange メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
ms.openlocfilehash: 43cfbeaa0d366b9f2d25068cfa7b91a0fea8ac59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762059"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="999d5-103">ISymUnmanagedWriter::SetScopeRange メソッド</span><span class="sxs-lookup"><span data-stu-id="999d5-103">ISymUnmanagedWriter::SetScopeRange Method</span></span>

<span data-ttu-id="999d5-104">指定した構文のスコープのオフセット範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="999d5-104">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="999d5-105">スコープは新しい現在のスコープになり、スコープのスタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="999d5-105">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="999d5-106">スコープは階層を形成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="999d5-106">Scopes must form a hierarchy.</span></span> <span data-ttu-id="999d5-107">兄弟を重ねることはできません。</span><span class="sxs-lookup"><span data-stu-id="999d5-107">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999d5-108">構文</span><span class="sxs-lookup"><span data-stu-id="999d5-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="999d5-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="999d5-109">Parameters</span></span>  

 `scopeId`  
 <span data-ttu-id="999d5-110">からスコープのスコープ識別子。</span><span class="sxs-lookup"><span data-stu-id="999d5-110">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="999d5-111">からメソッドの先頭からの構文のスコープの最初の命令のオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="999d5-111">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="999d5-112">からメソッドの先頭からの構文のスコープの最後の命令のオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="999d5-112">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="999d5-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="999d5-113">Return Value</span></span>  

 <span data-ttu-id="999d5-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="999d5-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="999d5-115">解説</span><span class="sxs-lookup"><span data-stu-id="999d5-115">Remarks</span></span>  

 <span data-ttu-id="999d5-116">[ISymUnmanagedWriter:: OpenScope](isymunmanagedwriter-openscope-method.md) は、 `ISymUnmanagedWriter::SetScopeRange` 後でスコープの開始オフセットと終了オフセットを定義するためにと共に使用できる非透過スコープ識別子を返します。</span><span class="sxs-lookup"><span data-stu-id="999d5-116">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="999d5-117">この場合、 `ISymUnmanagedWriter::OpenScope` と [ISymUnmanagedWriter:: cloに](isymunmanagedwriter-closescope-method.md) 渡されるオフセットは無視されます。</span><span class="sxs-lookup"><span data-stu-id="999d5-117">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="999d5-118">スコープ識別子は、現在のメソッドでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="999d5-118">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="999d5-119">要件</span><span class="sxs-lookup"><span data-stu-id="999d5-119">Requirements</span></span>  

 <span data-ttu-id="999d5-120">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="999d5-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="999d5-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="999d5-121">See also</span></span>

- [<span data-ttu-id="999d5-122">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="999d5-122">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
