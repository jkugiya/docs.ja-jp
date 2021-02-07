---
description: '詳細については、次を参照してください: CodeChunkInfo 構造体'
title: CodeChunkInfo 構造体
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: 017a9ee8c608d4efae98eb0a342a3371ef8ec310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712351"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="fd129-103">CodeChunkInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="fd129-103">CodeChunkInfo Structure</span></span>

<span data-ttu-id="fd129-104">メモリ内のコードの単一のチャンクを表しています。</span><span class="sxs-lookup"><span data-stu-id="fd129-104">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd129-105">構文</span><span class="sxs-lookup"><span data-stu-id="fd129-105">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="fd129-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="fd129-106">Members</span></span>  
  
|<span data-ttu-id="fd129-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="fd129-107">Member</span></span>|<span data-ttu-id="fd129-108">説明</span><span class="sxs-lookup"><span data-stu-id="fd129-108">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="fd129-109">`CORDB_ADDRESS`チャンクの開始アドレスを示す値です。</span><span class="sxs-lookup"><span data-stu-id="fd129-109">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="fd129-110">チャンクのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="fd129-110">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd129-111">解説</span><span class="sxs-lookup"><span data-stu-id="fd129-111">Remarks</span></span>  

 <span data-ttu-id="fd129-112">コードの1つのチャンクは、関数などのコードオブジェクトの一部であるネイティブコードの領域です。</span><span class="sxs-lookup"><span data-stu-id="fd129-112">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd129-113">要件</span><span class="sxs-lookup"><span data-stu-id="fd129-113">Requirements</span></span>  

 <span data-ttu-id="fd129-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd129-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd129-115">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="fd129-115">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="fd129-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd129-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd129-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd129-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd129-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd129-118">See also</span></span>

- [<span data-ttu-id="fd129-119">GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="fd129-119">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="fd129-120">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="fd129-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="fd129-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="fd129-121">Debugging</span></span>](index.md)
