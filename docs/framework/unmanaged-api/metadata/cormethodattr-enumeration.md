---
description: '詳細については、次を参照してください: CorMethodAttr 列挙型'
title: CorMethodAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
ms.openlocfilehash: 4050235675f4b237b184d31378a614a0613ab3df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784380"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="2752c-103">CorMethodAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="2752c-103">CorMethodAttr Enumeration</span></span>

<span data-ttu-id="2752c-104">メソッドの機能を記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="2752c-104">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2752c-105">構文</span><span class="sxs-lookup"><span data-stu-id="2752c-105">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="2752c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2752c-106">Members</span></span>  
  
|<span data-ttu-id="2752c-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="2752c-107">Member</span></span>|<span data-ttu-id="2752c-108">説明</span><span class="sxs-lookup"><span data-stu-id="2752c-108">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="2752c-109">メンバーアクセスを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-109">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="2752c-110">メンバーを参照できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-110">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="2752c-111">メンバーが親の型によってのみアクセス可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-111">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="2752c-112">このアセンブリ内のサブタイプだけがメンバーにアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-112">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="2752c-113">メンバーがアセンブリ内のすべてのユーザーによって accessibly されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-113">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="2752c-114">メンバーが型とサブタイプによってのみアクセス可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-114">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="2752c-115">メンバーが、派生クラスおよびそのアセンブリ内の他の型によってアクセス可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-115">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="2752c-116">スコープへのアクセス権を持つすべての型からメンバーにアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-116">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="2752c-117">メンバーがインスタンスのメンバーとしてではなく、型の一部として定義されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-117">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="2752c-118">メソッドをオーバーライドできないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-118">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="2752c-119">メソッドをオーバーライドできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-119">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="2752c-120">メソッドが名前だけではなく、名前とシグネチャで非表示になるように指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-120">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="2752c-121">仮想テーブルのレイアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-121">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="2752c-122">仮想テーブルでこのメソッドに使用されるスロットを再利用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-122">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="2752c-123">既定値です。</span><span class="sxs-lookup"><span data-stu-id="2752c-123">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="2752c-124">メソッドが常に仮想テーブル内の新しいスロットを取得することを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-124">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="2752c-125">メソッドを、表示されているのと同じ型でオーバーライドできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-125">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="2752c-126">メソッドが実装されていないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-126">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="2752c-127">メソッドが特別であり、その名前がどのように説明するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-127">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="2752c-128">メソッドの実装が PInvoke を使用して転送されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-128">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="2752c-129">メソッドがアンマネージコードにエクスポートされたマネージメソッドであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-129">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="2752c-130">共通言語ランタイムによる内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="2752c-130">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="2752c-131">共通言語ランタイムがメソッド名のエンコーディングを確認する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-131">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="2752c-132">メソッドにセキュリティが関連付けられていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-132">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="2752c-133">メソッドが、セキュリティコードを含む別のメソッドを呼び出すことを指定します。</span><span class="sxs-lookup"><span data-stu-id="2752c-133">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2752c-134">要件</span><span class="sxs-lookup"><span data-stu-id="2752c-134">Requirements</span></span>  

 <span data-ttu-id="2752c-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2752c-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2752c-136">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="2752c-136">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2752c-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2752c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2752c-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="2752c-138">See also</span></span>

- [<span data-ttu-id="2752c-139">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="2752c-139">Metadata Enumerations</span></span>](metadata-enumerations.md)
