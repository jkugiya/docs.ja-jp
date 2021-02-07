---
description: '詳細について: ICorDebugProcess7:: SetWriteableMetadataUpdateMode メソッド'
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
ms.openlocfilehash: 86ece68e160fbd61f44adcf495656c7b5d6b5153
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691264"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="a9108-103">ICorDebugProcess7::SetWriteableMetadataUpdateMode メソッド</span><span class="sxs-lookup"><span data-stu-id="a9108-103">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>

<span data-ttu-id="a9108-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="a9108-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a9108-105">デバッガーが、ターゲット プロセス内のメタデータに対するメモリ内更新をどのように処理するかを設定します。</span><span class="sxs-lookup"><span data-stu-id="a9108-105">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9108-106">構文</span><span class="sxs-lookup"><span data-stu-id="a9108-106">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9108-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9108-107">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="a9108-108">ターゲットプロセス内のメタデータに対するメモリ内更新をデバッガーに対して表示 () するか、非表示 () するかを指定する [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) 列挙値です `WriteableMetadataUpdateMode::AlwaysShowUpdates` `WriteableMetadataUpdateMode::LegacyCompatPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="a9108-108">A [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9108-109">解説</span><span class="sxs-lookup"><span data-stu-id="a9108-109">Remarks</span></span>  

 <span data-ttu-id="a9108-110">ターゲット プロセスのメタデータに対する更新は、[編集]、[続行] で行うか、プロファイラー、または <xref:System.Reflection.Emit?displayProperty=nameWithType> で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a9108-110">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9108-111">要件</span><span class="sxs-lookup"><span data-stu-id="a9108-111">Requirements</span></span>  

 <span data-ttu-id="a9108-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9108-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9108-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9108-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9108-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9108-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9108-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9108-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9108-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9108-116">See also</span></span>

- [<span data-ttu-id="a9108-117">ICorDebugProcess7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9108-117">ICorDebugProcess7 Interface</span></span>](icordebugprocess7-interface.md)
- [<span data-ttu-id="a9108-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9108-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
