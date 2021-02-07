---
description: '詳細について: ISymUnmanagedBinder2:: GetReaderForFile2 メソッド'
title: ISymUnmanagedBinder2::GetReaderForFile2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: c1a180ceec07c3087150613365acfce646adc34e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689938"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="918c4-103">ISymUnmanagedBinder2::GetReaderForFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="918c4-103">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>

<span data-ttu-id="918c4-104">メタデータインターフェイスとファイル名を指定すると、モジュールに関連付けられているデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスが返されます。</span><span class="sxs-lookup"><span data-stu-id="918c4-104">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="918c4-105">このメソッドは、 [ISymUnmanagedBinder:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) メソッドよりも、プログラムデータベース (PDB) ファイルをより広範囲に検索します。</span><span class="sxs-lookup"><span data-stu-id="918c4-105">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="918c4-106">構文</span><span class="sxs-lookup"><span data-stu-id="918c4-106">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="918c4-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="918c4-107">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="918c4-108">からメタデータインポートインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="918c4-108">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="918c4-109">からファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="918c4-109">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="918c4-110">から検索パスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="918c4-110">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="918c4-111">からシンボルリーダーの検索を実行するときに使用するポリシーを指定する [Corsymsearchpolicyattributes](corsymsearchpolicyattributes-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="918c4-111">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="918c4-112">入出力返された [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="918c4-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="918c4-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="918c4-113">Return Value</span></span>  

 <span data-ttu-id="918c4-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="918c4-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="918c4-115">要件</span><span class="sxs-lookup"><span data-stu-id="918c4-115">Requirements</span></span>  

 <span data-ttu-id="918c4-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="918c4-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="918c4-117">解説</span><span class="sxs-lookup"><span data-stu-id="918c4-117">Remarks</span></span>  

 <span data-ttu-id="918c4-118">このバージョンのメソッドでは、モジュールの横の右側以外の領域で PDB ファイルを検索できます。</span><span class="sxs-lookup"><span data-stu-id="918c4-118">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="918c4-119">検索ポリシーは、 [Corsymsearchpolicyattributes](corsymsearchpolicyattributes-enumeration.md)を組み合わせることによって制御できます。</span><span class="sxs-lookup"><span data-stu-id="918c4-119">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="918c4-120">たとえば、は、 `AllowReferencePathAccess | AllowSymbolServerAccess` 実行可能ファイルの横にある PDB とシンボルサーバーを検索しますが、レジストリに対してクエリを実行したり、実行可能ファイルのパスを使用したりしません。</span><span class="sxs-lookup"><span data-stu-id="918c4-120">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="918c4-121">パラメーターを `searchPath` 指定すると、これらのディレクトリは常に検索されます。</span><span class="sxs-lookup"><span data-stu-id="918c4-121">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="918c4-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="918c4-122">See also</span></span>

- [<span data-ttu-id="918c4-123">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="918c4-123">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="918c4-124">GetReaderForFile メソッド</span><span class="sxs-lookup"><span data-stu-id="918c4-124">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)
