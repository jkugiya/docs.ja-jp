---
description: 詳細については、「LogSwitchCallReason 列挙型」を参照してください。
title: LogSwitchCallReason 列挙型
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
ms.openlocfilehash: 46c457ee4c12fe9a73796aa7b7a5f599d90c9c6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800612"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="b08bb-103">LogSwitchCallReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="b08bb-103">LogSwitchCallReason Enumeration</span></span>

<span data-ttu-id="b08bb-104">デバッグとトレースの切り替えで実行された操作を示します。</span><span class="sxs-lookup"><span data-stu-id="b08bb-104">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b08bb-105">構文</span><span class="sxs-lookup"><span data-stu-id="b08bb-105">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="b08bb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b08bb-106">Members</span></span>  
  
|<span data-ttu-id="b08bb-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b08bb-107">Member</span></span>|<span data-ttu-id="b08bb-108">説明</span><span class="sxs-lookup"><span data-stu-id="b08bb-108">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="b08bb-109">デバッグ/トレーススイッチが作成されました。</span><span class="sxs-lookup"><span data-stu-id="b08bb-109">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="b08bb-110">デバッグ/トレーススイッチが変更されました。</span><span class="sxs-lookup"><span data-stu-id="b08bb-110">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="b08bb-111">デバッグ/トレーススイッチが削除されました。</span><span class="sxs-lookup"><span data-stu-id="b08bb-111">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b08bb-112">要件</span><span class="sxs-lookup"><span data-stu-id="b08bb-112">Requirements</span></span>  

 <span data-ttu-id="b08bb-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b08bb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b08bb-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b08bb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b08bb-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b08bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b08bb-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b08bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b08bb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b08bb-117">See also</span></span>

- [<span data-ttu-id="b08bb-118">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="b08bb-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
