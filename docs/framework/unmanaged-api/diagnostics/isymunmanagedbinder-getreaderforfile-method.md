---
description: '詳細について: ISymUnmanagedBinder:: GetReaderForFile メソッド'
title: ISymUnmanagedBinder::GetReaderForFile メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
ms.openlocfilehash: ede494cbc1bbe4059b98a639c1d0621dc2cbdfa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790218"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="b4abe-103">ISymUnmanagedBinder::GetReaderForFile メソッド</span><span class="sxs-lookup"><span data-stu-id="b4abe-103">ISymUnmanagedBinder::GetReaderForFile Method</span></span>

<span data-ttu-id="b4abe-104">メタデータインターフェイスとファイル名を指定すると、モジュールに関連付けられているデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスが返されます。</span><span class="sxs-lookup"><span data-stu-id="b4abe-104">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="b4abe-105">このメソッドは、プログラムデータベース (PDB) ファイルが実行可能ファイルの横にある場合にのみ、ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="b4abe-105">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="b4abe-106">この変更は、セキュリティ上の目的で行われています。</span><span class="sxs-lookup"><span data-stu-id="b4abe-106">This change has been made for security purposes.</span></span> <span data-ttu-id="b4abe-107">PDB ファイルをより広範囲に検索する必要がある場合は、 [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b4abe-107">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4abe-108">構文</span><span class="sxs-lookup"><span data-stu-id="b4abe-108">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4abe-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b4abe-109">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="b4abe-110">からメタデータインポートインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b4abe-110">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b4abe-111">からファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b4abe-111">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="b4abe-112">から検索パスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b4abe-112">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b4abe-113">入出力返された [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="b4abe-113">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4abe-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="b4abe-114">Return Value</span></span>  

 <span data-ttu-id="b4abe-115">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4abe-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4abe-116">要件</span><span class="sxs-lookup"><span data-stu-id="b4abe-116">Requirements</span></span>  

 <span data-ttu-id="b4abe-117">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="b4abe-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4abe-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4abe-118">See also</span></span>

- [<span data-ttu-id="b4abe-119">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4abe-119">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="b4abe-120">GetReaderForFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="b4abe-120">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)
