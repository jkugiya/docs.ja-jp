---
description: 詳細については、「CorSymAddrKind 列挙型」を参照してください。
title: CorSymAddrKind 列挙体
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: 94ee9f3da63a33a9f4a80289dbf9b03969d37b3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800501"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="6fece-103">CorSymAddrKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="6fece-103">CorSymAddrKind Enumeration</span></span>

<span data-ttu-id="6fece-104">メモリアドレスの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-104">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fece-105">構文</span><span class="sxs-lookup"><span data-stu-id="6fece-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a><span data-ttu-id="6fece-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="6fece-106">Members</span></span>  
  
|<span data-ttu-id="6fece-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="6fece-107">Member</span></span>|<span data-ttu-id="6fece-108">説明</span><span class="sxs-lookup"><span data-stu-id="6fece-108">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="6fece-109">Microsoft 中間言語 (MSIL) のローカル変数またはパラメーターインデックスを示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-109">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="6fece-110">モジュール内の相対仮想アドレスを示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-110">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="6fece-111">CPU レジスタを示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-111">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="6fece-112">は、最初のアドレスがレジスタで、2番目のアドレスがオフセットであることを示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-112">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="6fece-113">ベースアドレスからのオフセットを示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-113">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="6fece-114">最初のアドレスがレジスタの低い部分であり、2番目のアドレスが上位部分であることを示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-114">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="6fece-115">最初のアドレスがレジスタの下位にあり、2番目が上位の部分、3番目のアドレスがオフセットであることを示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-115">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="6fece-116">は、最初のアドレスがレジスタ、2番目のアドレスがオフセット、3番目がレジスタの上位部分であることを示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-116">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="6fece-117">最初のアドレスがフィールドの先頭で、2番目のアドレスがフィールド長であることを示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-117">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="6fece-118">は、最初のアドレスがセクションで、2番目のアドレスがオフセットであることを示します。</span><span class="sxs-lookup"><span data-stu-id="6fece-118">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6fece-119">要件</span><span class="sxs-lookup"><span data-stu-id="6fece-119">Requirements</span></span>  

 <span data-ttu-id="6fece-120">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="6fece-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fece-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fece-121">See also</span></span>

- [<span data-ttu-id="6fece-122">シンボル ストア診断列挙型</span><span class="sxs-lookup"><span data-stu-id="6fece-122">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
