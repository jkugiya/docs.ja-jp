---
description: '詳細情報: ICorDebugProcess6:: Markデバッガ添付メソッド'
title: ICorDebugProcess6::MarkDebuggerAttached メソッド
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: adbe16049cea73ca5e797f7758a17902b33645c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691381"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="cbc59-103">ICorDebugProcess6::MarkDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="cbc59-103">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>

<span data-ttu-id="cbc59-104">.NET Framework クラス ライブラリの <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドが `true` を返すように、デバッグ対象の内部状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="cbc59-104">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc59-105">構文</span><span class="sxs-lookup"><span data-stu-id="cbc59-105">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbc59-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cbc59-106">Parameters</span></span>  

 `fIsAttached`  
 <span data-ttu-id="cbc59-107">`true` メソッドが、デバッガーが接続されていることを示す必要がある場合は、<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>。それ以外の場合は、`false`。</span><span class="sxs-lookup"><span data-stu-id="cbc59-107">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbc59-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="cbc59-108">Return Value</span></span>  

 <span data-ttu-id="cbc59-109">メソッドは、次の表に記載されている値を返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="cbc59-109">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="cbc59-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="cbc59-110">Return value</span></span>|<span data-ttu-id="cbc59-111">説明</span><span class="sxs-lookup"><span data-stu-id="cbc59-111">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="cbc59-112">デバッグ対象は正常に更新されました。</span><span class="sxs-lookup"><span data-stu-id="cbc59-112">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="cbc59-113"><xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドを格納するアセンブリが読み込まれていないか、メタデータの欠落などの他のエラーが原因で認識されません。</span><span class="sxs-lookup"><span data-stu-id="cbc59-113">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="cbc59-114">このエラーは一般的なもので、問題ありません。</span><span class="sxs-lookup"><span data-stu-id="cbc59-114">This error is common and benign.</span></span> <span data-ttu-id="cbc59-115">追加のアセンブリを読み込むときに、再度メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbc59-115">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="cbc59-116">その他の失敗した `HRESULT` 値。</span><span class="sxs-lookup"><span data-stu-id="cbc59-116">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="cbc59-117">可能性が高いその他の値は、不適切に動作するデバッガーまたはコンパイラ コンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="cbc59-117">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbc59-118">解説</span><span class="sxs-lookup"><span data-stu-id="cbc59-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbc59-119">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="cbc59-119">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbc59-120">要件</span><span class="sxs-lookup"><span data-stu-id="cbc59-120">Requirements</span></span>  

 <span data-ttu-id="cbc59-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbc59-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbc59-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbc59-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbc59-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbc59-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbc59-124">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbc59-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc59-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="cbc59-125">See also</span></span>

- [<span data-ttu-id="cbc59-126">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cbc59-126">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="cbc59-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cbc59-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
