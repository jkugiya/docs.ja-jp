---
description: 詳細については、「関数ポインターの LPOVERLAPPED_COMPLETION_ROUTINE」を参照してください。
title: LPOVERLAPPED_COMPLETION_ROUTINE 関数ポインター
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
ms.openlocfilehash: 6645e6a9746404a4ae355a22cf16e6d164c63bed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679837"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a><span data-ttu-id="50506-103">LPOVERLAPPED_COMPLETION_ROUTINE 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="50506-103">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>

<span data-ttu-id="50506-104">デバイスに対する重複 I/O (非同期 I/O) が完了したときに、ホストに通知する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="50506-104">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="50506-105">この関数ポインターは .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="50506-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50506-106">構文</span><span class="sxs-lookup"><span data-stu-id="50506-106">Syntax</span></span>  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50506-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50506-107">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="50506-108">からデバイスが閉じられている場合は、エラーコードである値。それ以外の場合、この値は0です。</span><span class="sxs-lookup"><span data-stu-id="50506-108">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="50506-109">デバイスを閉じると、デバイスに対するすべての保留中の i/o が直ちに完了します。</span><span class="sxs-lookup"><span data-stu-id="50506-109">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="50506-110">からI/o 操作によって転送されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="50506-110">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="50506-111">からI/o 要求を完了するために使用される情報を格納する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="50506-111">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50506-112">解説</span><span class="sxs-lookup"><span data-stu-id="50506-112">Remarks</span></span>  

 <span data-ttu-id="50506-113">`LPOVERLAPPED_COMPLETION_ROUTINE`ポイントがコールバック関数であり、ホストアプリケーションのライターによって実装されている必要がある関数。</span><span class="sxs-lookup"><span data-stu-id="50506-113">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="50506-114">コールバック関数を使用すると、ホストは、完了した i/o 要求を処理できます。</span><span class="sxs-lookup"><span data-stu-id="50506-114">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50506-115">要件</span><span class="sxs-lookup"><span data-stu-id="50506-115">Requirements</span></span>  

 <span data-ttu-id="50506-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50506-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50506-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="50506-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50506-118">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="50506-118">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="50506-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50506-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50506-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="50506-120">See also</span></span>

- [<span data-ttu-id="50506-121">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="50506-121">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
