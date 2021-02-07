---
description: '詳細について: ISymUnmanagedBinder3:: GetReaderFromCallback メソッド'
title: ISymUnmanagedBinder3::GetReaderFromCallback メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
ms.openlocfilehash: ba7c819678fee7625f3cddb29d99f5d7f4c6f991
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689873"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="97f2c-103">ISymUnmanagedBinder3::GetReaderFromCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="97f2c-103">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>

<span data-ttu-id="97f2c-104">`IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` メモリからデバッグディレクトリ情報を取得するために、ユーザーがまたはのいずれかを使用してを実装または提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="97f2c-104">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97f2c-105">構文</span><span class="sxs-lookup"><span data-stu-id="97f2c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97f2c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="97f2c-106">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="97f2c-107">からメタデータインポートインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="97f2c-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="97f2c-108">からファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="97f2c-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="97f2c-109">から検索パスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="97f2c-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="97f2c-110">からシンボルリーダーの検索を実行するときに使用するポリシーを指定する [Corsymsearchpolicyattributes](corsymsearchpolicyattributes-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="97f2c-110">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="97f2c-111">からコールバック関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="97f2c-111">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="97f2c-112">入出力返された [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="97f2c-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97f2c-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="97f2c-113">Return Value</span></span>  

 <span data-ttu-id="97f2c-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="97f2c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97f2c-115">要件</span><span class="sxs-lookup"><span data-stu-id="97f2c-115">Requirements</span></span>  

 <span data-ttu-id="97f2c-116">**ヘッダー:** CorSym .idl</span><span class="sxs-lookup"><span data-stu-id="97f2c-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f2c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="97f2c-117">See also</span></span>

- [<span data-ttu-id="97f2c-118">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="97f2c-118">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
