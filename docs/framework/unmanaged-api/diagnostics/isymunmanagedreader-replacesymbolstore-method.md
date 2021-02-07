---
description: '詳細について: ISymUnmanagedReader:: 置換 Esymstore メソッド'
title: ISymUnmanagedReader::ReplaceSymbolStore メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
ms.openlocfilehash: e05344ee0b14d40d735ca3e557c319998daf7849
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763763"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="4c5b9-103">ISymUnmanagedReader::ReplaceSymbolStore メソッド</span><span class="sxs-lookup"><span data-stu-id="4c5b9-103">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>

<span data-ttu-id="4c5b9-104">既存のシンボル ストアをデルタ シンボル ストアで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4c5b9-104">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="4c5b9-105">このメソッドは、指定されたデルタが更新ではなく完全な置換として機能する点を除いて、"更新プログラム" [ストア](isymunmanagedreader-updatesymbolstore-method.md) メソッドに似ています。</span><span class="sxs-lookup"><span data-stu-id="4c5b9-105">This method is similar to the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c5b9-106">またはパラメーターのいずれか1つだけを指定する必要があります。両方を指定すること `filename` はでき `pIStream` ません。</span><span class="sxs-lookup"><span data-stu-id="4c5b9-106">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="4c5b9-107">を `filename` 指定した場合、シンボルストアはそのファイル内のシンボルで更新されます。</span><span class="sxs-lookup"><span data-stu-id="4c5b9-107">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="4c5b9-108">を指定した場合、 `pIStream` ストアはからのデータで更新され <xref:System.Runtime.InteropServices.ComTypes.IStream> ます。</span><span class="sxs-lookup"><span data-stu-id="4c5b9-108">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c5b9-109">構文</span><span class="sxs-lookup"><span data-stu-id="4c5b9-109">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c5b9-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4c5b9-110">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="4c5b9-111">からシンボルストアを格納しているファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="4c5b9-111">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="4c5b9-112">からパラメーターの代わりに使用されるファイルストリーム `filename` 。</span><span class="sxs-lookup"><span data-stu-id="4c5b9-112">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c5b9-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="4c5b9-113">Return Value</span></span>  

 <span data-ttu-id="4c5b9-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c5b9-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c5b9-115">要件</span><span class="sxs-lookup"><span data-stu-id="4c5b9-115">Requirements</span></span>  

 <span data-ttu-id="4c5b9-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="4c5b9-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5b9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c5b9-117">See also</span></span>

- [<span data-ttu-id="4c5b9-118">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4c5b9-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
