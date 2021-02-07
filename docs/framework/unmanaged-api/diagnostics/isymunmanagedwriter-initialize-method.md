---
description: '詳細情報: ISymUnmanagedWriter:: Initialize メソッド'
title: ISymUnmanagedWriter::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
ms.openlocfilehash: eab60e9539df3d43a1602268d704ac324f028915
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762293"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="024d3-103">ISymUnmanagedWriter::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="024d3-103">ISymUnmanagedWriter::Initialize Method</span></span>

<span data-ttu-id="024d3-104">このライターが関連付けられるメタデータエミッタインターフェイスを設定し、デバッグシンボルの書き込み先となる出力ファイル名を設定します。</span><span class="sxs-lookup"><span data-stu-id="024d3-104">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="024d3-105">このメソッドを呼び出すことができるのは1回だけです。他のライターメソッドの前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="024d3-105">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="024d3-106">一部のライターでは、ファイル名が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="024d3-106">Some writers may require a file name.</span></span> <span data-ttu-id="024d3-107">ただし、ファイル名を使用しないライターに悪影響を及ぼすことなく、常にファイル名をこのメソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="024d3-107">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="024d3-108">構文</span><span class="sxs-lookup"><span data-stu-id="024d3-108">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="024d3-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="024d3-109">Parameters</span></span>  

 `emitter`  
 <span data-ttu-id="024d3-110">からメタデータエミッタインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="024d3-110">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="024d3-111">からデバッグシンボルが書き込まれるファイル名。</span><span class="sxs-lookup"><span data-stu-id="024d3-111">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="024d3-112">ファイル名を使用しないライターに対してファイル名を指定した場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="024d3-112">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="024d3-113">から指定した場合、シンボルライターは、パラメーターで指定されたファイルではなく、指定されたにシンボルを出力し <xref:System.Runtime.InteropServices.ComTypes.IStream> `filename` ます。</span><span class="sxs-lookup"><span data-stu-id="024d3-113">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="024d3-114">`pIStream` パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="024d3-114">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="024d3-115">[入力] `true` 完全な再構築の場合は、 `false` インクリメンタルコンパイルの場合は。</span><span class="sxs-lookup"><span data-stu-id="024d3-115">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="024d3-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="024d3-116">Return Value</span></span>  

 <span data-ttu-id="024d3-117">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="024d3-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="024d3-118">要件</span><span class="sxs-lookup"><span data-stu-id="024d3-118">Requirements</span></span>  

 <span data-ttu-id="024d3-119">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="024d3-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024d3-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="024d3-120">See also</span></span>

- [<span data-ttu-id="024d3-121">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="024d3-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="024d3-122">Initialize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="024d3-122">Initialize2 Method</span></span>](isymunmanagedwriter-initialize2-method.md)
