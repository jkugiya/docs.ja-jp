---
description: '詳細について: ICorDebugMergedAssemblyRecord:: GetSimpleName メソッド'
title: ICorDebugMergedAssemblyRecord::GetSimpleName メソッド
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: e77a5cc7df009a5bc55a7eb952ead80e5f81f271
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650392"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="b7c1d-103">ICorDebugMergedAssemblyRecord::GetSimpleName メソッド</span><span class="sxs-lookup"><span data-stu-id="b7c1d-103">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>

<span data-ttu-id="b7c1d-104">アセンブリの簡易名を取得します。</span><span class="sxs-lookup"><span data-stu-id="b7c1d-104">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7c1d-105">構文</span><span class="sxs-lookup"><span data-stu-id="b7c1d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7c1d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b7c1d-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="b7c1d-107">[in] `szName` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="b7c1d-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b7c1d-108">[out] `szName` バッファーに実際に書き込まれた文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7c1d-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="b7c1d-109">文字配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7c1d-109">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7c1d-110">解説</span><span class="sxs-lookup"><span data-stu-id="b7c1d-110">Remarks</span></span>  

 <span data-ttu-id="b7c1d-111">このメソッドは、アセンブリの簡易名 ("System.Collections" など) を取得します。簡易名には、ファイル拡張子、バージョン、カルチャ、公開キー トークンが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="b7c1d-111">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="b7c1d-112">これはマネージド コード内の <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="b7c1d-112">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7c1d-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7c1d-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7c1d-114">要件</span><span class="sxs-lookup"><span data-stu-id="b7c1d-114">Requirements</span></span>  

 <span data-ttu-id="b7c1d-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7c1d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7c1d-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7c1d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7c1d-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7c1d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7c1d-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7c1d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c1d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7c1d-119">See also</span></span>

- [<span data-ttu-id="b7c1d-120">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7c1d-120">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="b7c1d-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7c1d-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
