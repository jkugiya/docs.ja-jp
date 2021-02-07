---
description: 詳細については、「ISymUnmanagedBinder2 インターフェイス」を参照してください。
title: ISymUnmanagedBinder2 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
ms.openlocfilehash: 73847cdc9366ec18974fac261cbbad4d7dc6ccc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689886"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="ca88e-103">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca88e-103">ISymUnmanagedBinder2 Interface</span></span>

<span data-ttu-id="ca88e-104">アンマネージコードのシンボルバインダーを表し、 [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="ca88e-104">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ca88e-105">信頼されていないソースからプログラムデータベース (PDB) ファイルを開くと、セキュリティ上の危険があります。</span><span class="sxs-lookup"><span data-stu-id="ca88e-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca88e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ca88e-106">Methods</span></span>  
  
|<span data-ttu-id="ca88e-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="ca88e-107">Method</span></span>|<span data-ttu-id="ca88e-108">説明</span><span class="sxs-lookup"><span data-stu-id="ca88e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca88e-109">GetReaderForFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="ca88e-109">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="ca88e-110">メタデータインターフェイスとファイル名を指定すると、モジュールに関連付けられているデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスが返されます。</span><span class="sxs-lookup"><span data-stu-id="ca88e-110">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="ca88e-111">[ISymUnmanagedBinder:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md)メソッドよりも広範な検索を提供します。</span><span class="sxs-lookup"><span data-stu-id="ca88e-111">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca88e-112">要件</span><span class="sxs-lookup"><span data-stu-id="ca88e-112">Requirements</span></span>  

 <span data-ttu-id="ca88e-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="ca88e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca88e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca88e-114">See also</span></span>

- [<span data-ttu-id="ca88e-115">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca88e-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="ca88e-116">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca88e-116">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="ca88e-117">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca88e-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
