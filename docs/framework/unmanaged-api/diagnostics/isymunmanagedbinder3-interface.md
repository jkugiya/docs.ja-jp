---
description: 詳細については、「ISymUnmanagedBinder3 インターフェイス」を参照してください。
title: ISymUnmanagedBinder3 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: 6d2172fb119076cea6d0f912fb3f403d36856599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689834"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="a3a24-103">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3a24-103">ISymUnmanagedBinder3 Interface</span></span>

<span data-ttu-id="a3a24-104">シンボルバインダーインターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="a3a24-104">Extends the symbol binder interface.</span></span> <span data-ttu-id="a3a24-105">このインターフェイスを取得するには `QueryInterface` 、インターフェイスを実装するオブジェクトに対してを呼び出し `ISymUnmanagedBinder` ます。</span><span class="sxs-lookup"><span data-stu-id="a3a24-105">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a3a24-106">信頼されていないソースからプログラムデータベース (PDB) ファイルを開くと、セキュリティ上の危険があります。</span><span class="sxs-lookup"><span data-stu-id="a3a24-106">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3a24-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="a3a24-107">Methods</span></span>  
  
|<span data-ttu-id="a3a24-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="a3a24-108">Method</span></span>|<span data-ttu-id="a3a24-109">説明</span><span class="sxs-lookup"><span data-stu-id="a3a24-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3a24-110">GetReaderFromCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="a3a24-110">GetReaderFromCallback Method</span></span>](isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="a3a24-111">`IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` メモリからデバッグディレクトリ情報を取得するために、またはのいずれかを使用して、ユーザーがを実装または提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a3a24-111">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3a24-112">要件</span><span class="sxs-lookup"><span data-stu-id="a3a24-112">Requirements</span></span>  

 <span data-ttu-id="a3a24-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a3a24-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a24-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3a24-114">See also</span></span>

- [<span data-ttu-id="a3a24-115">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3a24-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="a3a24-116">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3a24-116">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="a3a24-117">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3a24-117">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
