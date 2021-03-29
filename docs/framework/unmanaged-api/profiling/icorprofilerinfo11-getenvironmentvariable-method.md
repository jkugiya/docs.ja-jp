---
description: '詳細情報: ICorProfilerInfo11::GetEnvironmentVariable メソッド'
title: ICorProfilerInfo11::GetEnvironmentVariable メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.GetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 635c5fb67b880c39f15fbc194a51a706d9ef7fe4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805832"
---
# <a name="icorprofilerinfo11getenvironmentvariable-method"></a><span data-ttu-id="ea981-103">ICorProfilerInfo11::GetEnvironmentVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="ea981-103">ICorProfilerInfo11::GetEnvironmentVariable Method</span></span>

<span data-ttu-id="ea981-104">プロセスから環境変数を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea981-104">Gets an environment variable from the process.</span></span> <span data-ttu-id="ea981-105">Windows 以外のプラットフォームでは、スレッド セーフを確保するために、ランタイムに環境変数の内部キャッシュが保持されます。</span><span class="sxs-lookup"><span data-stu-id="ea981-105">On non-Windows platforms the runtime keeps an internal cache of environment variables to ensure thread safety.</span></span> <span data-ttu-id="ea981-106">つまり、`getenv` を呼び出しても、新しい環境変数や、起動後にプロセスで実行されているマネージド コードによって設定された更新された環境変数は読み取られません。</span><span class="sxs-lookup"><span data-stu-id="ea981-106">This means that calling `getenv` will not read any new or updated environment variables set by managed code running in the process after startup.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="ea981-107">構文</span><span class="sxs-lookup"><span data-stu-id="ea981-107">Syntax</span></span>  
  
```cpp  
    HRESULT GetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in]         ULONG cchValue,
                [out]        ULONG *pcchValue,
                [out, annotation("_Out_writes_to_(cchValue, *pcchValue)")]
                             WCHAR szValue[]);
```  
  
## <a name="parameters"></a><span data-ttu-id="ea981-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea981-108">Parameters</span></span>

<span data-ttu-id="ea981-109">`szName` [入力] 取得する環境変数の名前が含まれている null で終わるワイド文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ea981-109">`szName` [in] A pointer to a null terminated wide character string containing the name of the environment variable to get.</span></span>

<span data-ttu-id="ea981-110">`cchValue` [入力] `szValue` の長さ (文字数)。</span><span class="sxs-lookup"><span data-stu-id="ea981-110">`cchValue` [in] The length, in characters, of `szValue`.</span></span>

<span data-ttu-id="ea981-111">`pcchValue` [出力] `szValue` の合計の文字の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ea981-111">`pcchValue` [out] A pointer to the total character length of `szValue`.</span></span>

<span data-ttu-id="ea981-112">`szValue` [出力] 呼び出し元によって提供されたワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="ea981-112">`szValue` [out] A caller provided wide character buffer.</span></span> <span data-ttu-id="ea981-113">関数が戻るとき、このバッファーに環境変数の値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ea981-113">When the function returns the buffer will contain the value of the environment variable.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea981-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="ea981-114">Requirements</span></span>  

<span data-ttu-id="ea981-115">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea981-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="ea981-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea981-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="ea981-117">**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea981-117">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea981-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea981-118">See also</span></span>

- [<span data-ttu-id="ea981-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea981-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ea981-120">ICorProfilerInfo11 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea981-120">ICorProfilerInfo11 Interface</span></span>](icorprofilerinfo11-interface.md)
