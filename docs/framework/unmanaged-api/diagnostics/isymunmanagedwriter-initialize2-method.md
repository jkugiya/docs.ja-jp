---
description: '詳細について: ISymUnmanagedWriter:: Initialize2 メソッド'
title: ISymUnmanagedWriter::Initialize2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 0d4c769c9f1b571296cbfe159057df083a6d5ca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762280"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="2a714-103">ISymUnmanagedWriter::Initialize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2a714-103">ISymUnmanagedWriter::Initialize2 Method</span></span>

<span data-ttu-id="2a714-104">このライターが関連付けられるメタデータエミッタインターフェイスを設定し、デバッグシンボルの書き込み先となる出力ファイル名を設定します。</span><span class="sxs-lookup"><span data-stu-id="2a714-104">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="2a714-105">この方法では、プログラムデータベース (PDB) ファイルの最終的な場所を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2a714-105">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a714-106">構文</span><span class="sxs-lookup"><span data-stu-id="2a714-106">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a714-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2a714-107">Parameters</span></span>  

 `emitter`  
 <span data-ttu-id="2a714-108">からメタデータエミッタインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2a714-108">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="2a714-109">から `WCHAR` デバッグシンボルが書き込まれるファイル名を格納しているへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2a714-109">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="2a714-110">ファイル名を使用しないライターに対してファイル名を指定した場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="2a714-110">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="2a714-111">から指定されている場合、シンボルライターは、 <xref:System.Runtime.InteropServices.ComTypes.IStream> パラメーターで指定されたファイルではなく、指定されたにシンボルを出力し `filename` ます。</span><span class="sxs-lookup"><span data-stu-id="2a714-111">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="2a714-112">`pIStream` パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="2a714-112">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="2a714-113">[入力] `true` 完全な再構築の場合は、 `false` インクリメンタルコンパイルの場合は。</span><span class="sxs-lookup"><span data-stu-id="2a714-113">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="2a714-114">から `WCHAR` PDB ファイルの最終的な場所へのパス文字列であるへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2a714-114">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a714-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="2a714-115">Return Value</span></span>  

 <span data-ttu-id="2a714-116">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a714-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a714-117">要件</span><span class="sxs-lookup"><span data-stu-id="2a714-117">Requirements</span></span>  

 <span data-ttu-id="2a714-118">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="2a714-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a714-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a714-119">See also</span></span>

- [<span data-ttu-id="2a714-120">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a714-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="2a714-121">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="2a714-121">Initialize Method</span></span>](isymunmanagedwriter-initialize-method.md)
