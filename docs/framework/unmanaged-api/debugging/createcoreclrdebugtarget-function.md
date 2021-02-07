---
description: '詳細情報: CreateCoreClrDebugTarget 関数'
title: CreateCoreClrDebugTarget 関数
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: 30a6af29e6e1a6ee2c827049a3c792f2d663a702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661577"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="f0522-103">CreateCoreClrDebugTarget 関数</span><span class="sxs-lookup"><span data-stu-id="f0522-103">CreateCoreClrDebugTarget Function</span></span>

<span data-ttu-id="f0522-104">リモートコンピューター上で実行されているデバッガープロキシへの接続を作成し、 [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) オブジェクトを返します。このオブジェクトを使用して、リモートコンピューター上で実行中のプロセスおよび読み込まれたランタイムのクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f0522-104">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0522-105">構文</span><span class="sxs-lookup"><span data-stu-id="f0522-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0522-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0522-106">Parameters</span></span>  

 `dwAddress`  
 <span data-ttu-id="f0522-107">[in] リモート対象コンピューターの IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="f0522-107">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="f0522-108">入出力作成される [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) オブジェクトへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f0522-108">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0522-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f0522-109">Return Value</span></span>  

 <span data-ttu-id="f0522-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0522-110">S_OK</span></span>  
 <span data-ttu-id="f0522-111">プロセス内の CLR 数が正常に判別され、対応するハンドルとパスの配列が正しく入力されました。</span><span class="sxs-lookup"><span data-stu-id="f0522-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="f0522-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f0522-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="f0522-113">`ppTarget`  用に十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="f0522-113">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="f0522-114">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="f0522-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="f0522-115">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f0522-115">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0522-116">要件</span><span class="sxs-lookup"><span data-stu-id="f0522-116">Requirements</span></span>  

 <span data-ttu-id="f0522-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0522-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0522-118">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="f0522-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="f0522-119">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="f0522-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="f0522-120">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="f0522-120">**.NET Framework Versions:** 3.5 SP1</span></span>
