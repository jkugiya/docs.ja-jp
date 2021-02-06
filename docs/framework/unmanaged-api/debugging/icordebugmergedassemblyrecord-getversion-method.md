---
description: '詳細について: ICorDebugMergedAssemblyRecord:: GetVersion メソッド'
title: ICorDebugMergedAssemblyRecord::GetVersion メソッド
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 0e87e2bbb1207ebd1eb5775b7f52d5689b4e8727
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650340"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="69be3-103">ICorDebugMergedAssemblyRecord::GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="69be3-103">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>

<span data-ttu-id="69be3-104">アセンブリのバージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="69be3-104">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69be3-105">構文</span><span class="sxs-lookup"><span data-stu-id="69be3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69be3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="69be3-106">Parameters</span></span>  

 `pMajor`  
 <span data-ttu-id="69be3-107">[out] メジャー バージョン番号へのポインター。</span><span class="sxs-lookup"><span data-stu-id="69be3-107">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="69be3-108">[out] マイナー バージョン番号へのポインター。</span><span class="sxs-lookup"><span data-stu-id="69be3-108">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="69be3-109">[out] ビルド番号へのポインター。</span><span class="sxs-lookup"><span data-stu-id="69be3-109">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="69be3-110">[out] リビジョン番号へのポインター。</span><span class="sxs-lookup"><span data-stu-id="69be3-110">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69be3-111">解説</span><span class="sxs-lookup"><span data-stu-id="69be3-111">Remarks</span></span>  

 <span data-ttu-id="69be3-112">アセンブリのバージョン番号については、<xref:System.Version> クラスのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="69be3-112">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69be3-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="69be3-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69be3-114">要件</span><span class="sxs-lookup"><span data-stu-id="69be3-114">Requirements</span></span>  

 <span data-ttu-id="69be3-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69be3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69be3-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69be3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69be3-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69be3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69be3-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69be3-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69be3-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="69be3-119">See also</span></span>

- [<span data-ttu-id="69be3-120">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69be3-120">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="69be3-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="69be3-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
