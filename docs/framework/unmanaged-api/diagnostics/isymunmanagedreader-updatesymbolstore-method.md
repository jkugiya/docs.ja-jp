---
description: '詳細について: ISymUnmanagedReader:: アップデート Ymbold Store メソッド'
title: ISymUnmanagedReader::UpdateSymbolStore メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
ms.openlocfilehash: eb6ca01b7978b66d0a8674e5b83ce26ee341e890
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763749"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="fe214-103">ISymUnmanagedReader::UpdateSymbolStore メソッド</span><span class="sxs-lookup"><span data-stu-id="fe214-103">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>

<span data-ttu-id="fe214-104">既存のシンボル ストアをデルタ シンボル ストアで更新します。</span><span class="sxs-lookup"><span data-stu-id="fe214-104">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="fe214-105">このメソッドは、元のポータブル実行可能 (PE) ファイルにデルタを一致するようにシンボルストアを更新するために、エディットコンティニュシナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="fe214-105">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe214-106">またはパラメーターのいずれか1つだけを指定する必要があります。両方を指定すること `filename` はでき `pIStream` ません。</span><span class="sxs-lookup"><span data-stu-id="fe214-106">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="fe214-107">を `filename` 指定した場合、シンボルストアはそのファイル内のシンボルで更新されます。</span><span class="sxs-lookup"><span data-stu-id="fe214-107">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="fe214-108">を指定した場合、 `pIStream` ストアはからのデータで更新され <xref:System.Runtime.InteropServices.ComTypes.IStream> ます。</span><span class="sxs-lookup"><span data-stu-id="fe214-108">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe214-109">構文</span><span class="sxs-lookup"><span data-stu-id="fe214-109">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe214-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fe214-110">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="fe214-111">からシンボルストアが格納されているファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="fe214-111">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="fe214-112">からパラメーターの代わりに使用されるファイルストリーム `filename` 。</span><span class="sxs-lookup"><span data-stu-id="fe214-112">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe214-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="fe214-113">Return Value</span></span>  

 <span data-ttu-id="fe214-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="fe214-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe214-115">要件</span><span class="sxs-lookup"><span data-stu-id="fe214-115">Requirements</span></span>  

 <span data-ttu-id="fe214-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="fe214-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe214-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe214-117">See also</span></span>

- [<span data-ttu-id="fe214-118">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe214-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
