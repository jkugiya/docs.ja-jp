---
description: 詳細については、「CorMethodImpl 列挙型」を参照してください。
title: CorMethodImpl 列挙型
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
ms.openlocfilehash: 157db81a72742f1f2aae7e95249b819b2396ef4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784393"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="07307-103">CorMethodImpl 列挙型</span><span class="sxs-lookup"><span data-stu-id="07307-103">CorMethodImpl Enumeration</span></span>

<span data-ttu-id="07307-104">メソッド実装の機能を記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="07307-104">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07307-105">構文</span><span class="sxs-lookup"><span data-stu-id="07307-105">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a><span data-ttu-id="07307-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="07307-106">Members</span></span>  
  
|<span data-ttu-id="07307-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="07307-107">Member</span></span>|<span data-ttu-id="07307-108">説明</span><span class="sxs-lookup"><span data-stu-id="07307-108">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="07307-109">コードの種類を記述するフラグ。</span><span class="sxs-lookup"><span data-stu-id="07307-109">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="07307-110">メソッドの実装が Microsoft 中間言語 (MSIL) であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-110">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="07307-111">メソッド実装がネイティブであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-111">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="07307-112">メソッドの実装が OPTIL であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-112">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="07307-113">メソッドの実装が共通言語ランタイムによって提供されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-113">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="07307-114">コードがマネージとアンマネージのどちらであるかを示すフラグ。</span><span class="sxs-lookup"><span data-stu-id="07307-114">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="07307-115">メソッドの実装がアンマネージであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-115">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="07307-116">メソッドの実装が管理されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-116">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="07307-117">メソッドが定義されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-117">Specifies that the method is defined.</span></span> <span data-ttu-id="07307-118">このフラグは、主にマージシナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="07307-118">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="07307-119">HRESULT 変換のメソッドシグネチャを破損させることができないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-119">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="07307-120">共通言語ランタイムによる内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="07307-120">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="07307-121">メソッドがその本体を通じてシングルスレッドであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-121">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="07307-122">メソッドがインライン化できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-122">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="07307-123">可能な場合は、メソッドをインライン展開することを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-123">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="07307-124">メソッドを最適化しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="07307-124">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="07307-125">の最大有効値 `CorMethodImpl` 。</span><span class="sxs-lookup"><span data-stu-id="07307-125">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07307-126">要件</span><span class="sxs-lookup"><span data-stu-id="07307-126">Requirements</span></span>  

 <span data-ttu-id="07307-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07307-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07307-128">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="07307-128">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="07307-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07307-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07307-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="07307-130">See also</span></span>

- [<span data-ttu-id="07307-131">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="07307-131">Metadata Enumerations</span></span>](metadata-enumerations.md)
