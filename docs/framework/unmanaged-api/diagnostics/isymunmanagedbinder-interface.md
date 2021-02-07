---
description: 詳細については、「ISymUnmanagedBinder インターフェイス」を参照してください。
title: ISymUnmanagedBinder インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
ms.openlocfilehash: 14ebccb028ab3388a8058dd05504c56a6df74c95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689925"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="da561-103">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da561-103">ISymUnmanagedBinder Interface</span></span>

<span data-ttu-id="da561-104">アンマネージド コードのシンボル バインダーを表します。</span><span class="sxs-lookup"><span data-stu-id="da561-104">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="da561-105">信頼されていないソースからプログラムデータベース (PDB) ファイルを開くと、セキュリティ上の危険があります。</span><span class="sxs-lookup"><span data-stu-id="da561-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da561-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="da561-106">Methods</span></span>  
  
|<span data-ttu-id="da561-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="da561-107">Method</span></span>|<span data-ttu-id="da561-108">説明</span><span class="sxs-lookup"><span data-stu-id="da561-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da561-109">GetReaderForFile メソッド</span><span class="sxs-lookup"><span data-stu-id="da561-109">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="da561-110">メタデータインターフェイスとファイル名を指定すると、モジュールに関連付けられているデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) 構造体が返されます。</span><span class="sxs-lookup"><span data-stu-id="da561-110">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="da561-111">GetReaderFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="da561-111">GetReaderFromStream Method</span></span>](isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="da561-112">メタデータインターフェイスと、シンボルストアを含むストリームが指定された場合、は、指定されたシンボルストアからデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) 構造体を返します。</span><span class="sxs-lookup"><span data-stu-id="da561-112">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da561-113">要件</span><span class="sxs-lookup"><span data-stu-id="da561-113">Requirements</span></span>  

 <span data-ttu-id="da561-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="da561-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da561-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="da561-115">See also</span></span>

- [<span data-ttu-id="da561-116">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da561-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="da561-117">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da561-117">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="da561-118">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da561-118">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
