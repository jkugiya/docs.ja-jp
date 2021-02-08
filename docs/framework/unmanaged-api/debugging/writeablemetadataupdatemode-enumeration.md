---
description: '詳細については、次を参照してください: WriteableMetadataUpdateMode 列挙型'
title: WriteableMetadataUpdateMode 列挙型
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
ms.openlocfilehash: b8136963e315c429643bd0ebf4bdb509d5173bec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800514"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="e7455-103">WriteableMetadataUpdateMode 列挙型</span><span class="sxs-lookup"><span data-stu-id="e7455-103">WriteableMetadataUpdateMode Enumeration</span></span>

<span data-ttu-id="e7455-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="e7455-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e7455-105">メモリ内のメタデータ更新をデバッガーに対して可視にするかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="e7455-105">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7455-106">構文</span><span class="sxs-lookup"><span data-stu-id="e7455-106">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="e7455-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="e7455-107">Members</span></span>  
  
|<span data-ttu-id="e7455-108">メンバー名</span><span class="sxs-lookup"><span data-stu-id="e7455-108">Member name</span></span>|<span data-ttu-id="e7455-109">説明</span><span class="sxs-lookup"><span data-stu-id="e7455-109">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="e7455-110">メモリ内のメタデータ更新を可視にするときに、.NET Framework の以前のバージョンとの互換性を保持します。</span><span class="sxs-lookup"><span data-stu-id="e7455-110">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="e7455-111">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7455-111">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="e7455-112">メモリ内のメタデータ更新をデバッガーに対して可視にします。</span><span class="sxs-lookup"><span data-stu-id="e7455-112">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7455-113">解説</span><span class="sxs-lookup"><span data-stu-id="e7455-113">Remarks</span></span>  

 <span data-ttu-id="e7455-114">列挙体のメンバーを `WriteableMetadataUpdateMode` [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) メソッドに渡して、ターゲットプロセス内のメタデータに対するメモリ内更新がデバッガーに表示されるかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="e7455-114">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="e7455-115">`LegacyCompatPolicy` オプションは、4.5.2 より前の .NET Framework のバージョンと同じ動作を適用します。</span><span class="sxs-lookup"><span data-stu-id="e7455-115">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="e7455-116">これは多くの場合、メタデータの更新が可視でないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="e7455-116">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="e7455-117">しかし、多数のデバッグ メソッドを呼び出すとデバッガーは明示的に強制変換し、更新を可視にします。</span><span class="sxs-lookup"><span data-stu-id="e7455-117">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="e7455-118">たとえば、デバッガーが、メソッドの元のメタデータに見つからない変数のインデックス [を渡すと](icordebugilframe-getlocalvariable-method.md) 、そのモジュールのすべてのメタデータが、プロセスの現在の状態と一致するスナップショットに更新されます。</span><span class="sxs-lookup"><span data-stu-id="e7455-118">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="e7455-119">言い換えれば、`LegacyCompatPolicy` オプションでは、メタデータの更新によりアンマネージ デバギング API のその他の部分がどのように使用されているかによって、使用可能なメタデータ更新がデバッガーに対して全く可視でない場合、一部が可視になる場合、すべてが可視になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e7455-119">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7455-120">要件</span><span class="sxs-lookup"><span data-stu-id="e7455-120">Requirements</span></span>  

 <span data-ttu-id="e7455-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7455-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7455-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7455-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7455-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7455-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7455-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7455-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7455-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7455-125">See also</span></span>

- [<span data-ttu-id="e7455-126">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="e7455-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="e7455-127">SetWriteableMetadataUpdateMode メソッド</span><span class="sxs-lookup"><span data-stu-id="e7455-127">SetWriteableMetadataUpdateMode Method</span></span>](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
