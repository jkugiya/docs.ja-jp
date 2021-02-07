---
description: '詳細については、次を参照してください: ISymUnmanagedWriter::D efineSequencePoints メソッド'
title: ISymUnmanagedWriter::DefineSequencePoints メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: 0c5ac9854ef341512f58cb1cd63ed7dfcde9962e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762332"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="a1873-103">ISymUnmanagedWriter::DefineSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="a1873-103">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>

<span data-ttu-id="a1873-104">現在のメソッド内のシーケンス ポイントのグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="a1873-104">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="a1873-105">開始行と開始列はそれぞれ、メソッド内のステートメントの開始を定義します。</span><span class="sxs-lookup"><span data-stu-id="a1873-105">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="a1873-106">各終了行と終了列は、メソッド内のステートメントの末尾を定義します。</span><span class="sxs-lookup"><span data-stu-id="a1873-106">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="a1873-107">配列は、オフセットの昇順で並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1873-107">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="a1873-108">オフセットは、常にメソッドの先頭からバイト単位で測定されます。</span><span class="sxs-lookup"><span data-stu-id="a1873-108">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1873-109">構文</span><span class="sxs-lookup"><span data-stu-id="a1873-109">Syntax</span></span>  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1873-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1873-110">Parameters</span></span>  

 `document`  
 <span data-ttu-id="a1873-111">からシーケンスポイントが定義されているドキュメントオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a1873-111">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="a1873-112">から、、 `ULONG32` `offsets` `lines` `columns` 、 `endLines` 、および `endColumns` の各バッファーのサイズを示す。</span><span class="sxs-lookup"><span data-stu-id="a1873-112">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="a1873-113">からメソッドの先頭から計測されたシーケンスポイントのオフセット。</span><span class="sxs-lookup"><span data-stu-id="a1873-113">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="a1873-114">からシーケンスポイントの開始行番号。</span><span class="sxs-lookup"><span data-stu-id="a1873-114">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="a1873-115">からシーケンスポイントの開始列番号。</span><span class="sxs-lookup"><span data-stu-id="a1873-115">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="a1873-116">からシーケンスポイントの終了行番号。</span><span class="sxs-lookup"><span data-stu-id="a1873-116">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="a1873-117">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a1873-117">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="a1873-118">からシーケンスポイントの終了列番号。</span><span class="sxs-lookup"><span data-stu-id="a1873-118">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="a1873-119">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a1873-119">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1873-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="a1873-120">Return Value</span></span>  

 <span data-ttu-id="a1873-121">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a1873-121">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1873-122">要件</span><span class="sxs-lookup"><span data-stu-id="a1873-122">Requirements</span></span>  

 <span data-ttu-id="a1873-123">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a1873-123">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1873-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1873-124">See also</span></span>

- [<span data-ttu-id="a1873-125">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1873-125">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
