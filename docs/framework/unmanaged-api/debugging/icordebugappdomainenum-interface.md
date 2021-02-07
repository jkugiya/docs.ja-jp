---
description: 詳細については、「ICorDebugAppDomainEnum インターフェイス」を参照してください。
title: ICorDebugAppDomainEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
ms.openlocfilehash: dfea6254e6cf4f162e44d057fb4126a67a087b61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754161"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="2c3b3-103">ICorDebugAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c3b3-103">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="2c3b3-104">`Next`列挙体の次の位置から始まる指定された数の値を返すメソッドを提供し `ICorDebugAppDomainEnum` ます。</span><span class="sxs-lookup"><span data-stu-id="2c3b3-104">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="2c3b3-105">このインターフェイスは、"ICorDebugEnum" のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="2c3b3-105">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c3b3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2c3b3-106">Methods</span></span>  
  
|<span data-ttu-id="2c3b3-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="2c3b3-107">Method</span></span>|<span data-ttu-id="2c3b3-108">説明</span><span class="sxs-lookup"><span data-stu-id="2c3b3-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c3b3-109">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="2c3b3-109">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="2c3b3-110">現在のカーソル位置から開始して、指定した数のアプリケーションドメインをコレクションから取得します。</span><span class="sxs-lookup"><span data-stu-id="2c3b3-110">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c3b3-111">解説</span><span class="sxs-lookup"><span data-stu-id="2c3b3-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c3b3-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2c3b3-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c3b3-113">要件</span><span class="sxs-lookup"><span data-stu-id="2c3b3-113">Requirements</span></span>  

 <span data-ttu-id="2c3b3-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c3b3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c3b3-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c3b3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c3b3-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c3b3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c3b3-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c3b3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3b3-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c3b3-118">See also</span></span>

- [<span data-ttu-id="2c3b3-119">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c3b3-119">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="2c3b3-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c3b3-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
