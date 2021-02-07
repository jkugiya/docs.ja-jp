---
description: '詳細情報: FUSION_INSTALL_REFERENCE 構造'
title: FUSION_INSTALL_REFERENCE 構造体
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
ms.openlocfilehash: 4ac3d2f7d36dd017315a8a3ce6d6185e75f9ddc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761110"
---
# <a name="fusion_install_reference-structure"></a><span data-ttu-id="bca96-103">FUSION_INSTALL_REFERENCE 構造体</span><span class="sxs-lookup"><span data-stu-id="bca96-103">FUSION_INSTALL_REFERENCE Structure</span></span>

<span data-ttu-id="bca96-104">アプリケーションがグローバルアセンブリキャッシュにインストールしたアセンブリに対して行う参照を表します。</span><span class="sxs-lookup"><span data-stu-id="bca96-104">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca96-105">構文</span><span class="sxs-lookup"><span data-stu-id="bca96-105">Syntax</span></span>  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="bca96-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="bca96-106">Members</span></span>  
  
|<span data-ttu-id="bca96-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="bca96-107">Member</span></span>|<span data-ttu-id="bca96-108">説明</span><span class="sxs-lookup"><span data-stu-id="bca96-108">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="bca96-109">構造体のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="bca96-109">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="bca96-110">将来の拡張のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="bca96-110">Reserved for future extensibility.</span></span> <span data-ttu-id="bca96-111">この値は 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bca96-111">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="bca96-112">参照を追加するエンティティ。</span><span class="sxs-lookup"><span data-stu-id="bca96-112">The entity that adds the reference.</span></span> <span data-ttu-id="bca96-113">このフィールドには、次のいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bca96-113">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="bca96-114">-FUSION_REFCOUNT_MSI_GUID: アセンブリは、Microsoft Windows インストーラーを使用してインストールされたアプリケーションによって参照されています。</span><span class="sxs-lookup"><span data-stu-id="bca96-114">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="bca96-115">`szIdentifier`フィールドはに設定され、 `MSI` `szNonCanonicalData` フィールドはに設定され `Windows Installer` ます。</span><span class="sxs-lookup"><span data-stu-id="bca96-115">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="bca96-116">このスキームは、Windows サイドバイサイドアセンブリに使用されます。</span><span class="sxs-lookup"><span data-stu-id="bca96-116">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="bca96-117">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: アセンブリは、[ **プログラムの追加と削除** ] インターフェイスに表示されるアプリケーションによって参照されています。</span><span class="sxs-lookup"><span data-stu-id="bca96-117">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="bca96-118">`szIdentifier`フィールドは、アプリケーションを [**プログラムの追加と削除**] インターフェイスに登録するトークンを提供します。</span><span class="sxs-lookup"><span data-stu-id="bca96-118">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="bca96-119">-FUSION_REFCOUNT_FILEPATH_GUID: アセンブリは、ファイルシステム内のファイルによって表されるアプリケーションによって参照されています。</span><span class="sxs-lookup"><span data-stu-id="bca96-119">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="bca96-120">`szIdentifier`フィールドには、このファイルへのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bca96-120">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="bca96-121">-FUSION_REFCOUNT_OPAQUE_STRING_GUID: アセンブリは、不透明な文字列によってのみ表されるアプリケーションによって参照されています。</span><span class="sxs-lookup"><span data-stu-id="bca96-121">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="bca96-122">フィールドは、 `szIdentifier` この不透明な文字列を提供します。</span><span class="sxs-lookup"><span data-stu-id="bca96-122">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="bca96-123">グローバルアセンブリキャッシュは、この値を削除するときに、不透明な参照が存在するかどうかを確認しません。</span><span class="sxs-lookup"><span data-stu-id="bca96-123">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="bca96-124">-FUSION_REFCOUNT_OSINSTALL_GUID: この値は予約されています。</span><span class="sxs-lookup"><span data-stu-id="bca96-124">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="bca96-125">グローバルアセンブリキャッシュにアセンブリをインストールしたアプリケーションを識別する一意の文字列。</span><span class="sxs-lookup"><span data-stu-id="bca96-125">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="bca96-126">値は、フィールドの値によって異なり `guidScheme` ます。</span><span class="sxs-lookup"><span data-stu-id="bca96-126">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="bca96-127">参照を追加するエンティティによってのみ認識される文字列。</span><span class="sxs-lookup"><span data-stu-id="bca96-127">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="bca96-128">グローバルアセンブリキャッシュはこの文字列を格納しますが、この文字列は使用しません。</span><span class="sxs-lookup"><span data-stu-id="bca96-128">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bca96-129">要件</span><span class="sxs-lookup"><span data-stu-id="bca96-129">Requirements</span></span>  

 <span data-ttu-id="bca96-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bca96-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca96-131">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="bca96-131">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bca96-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca96-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca96-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="bca96-133">See also</span></span>

- [<span data-ttu-id="bca96-134">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="bca96-134">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="bca96-135">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="bca96-135">Global Assembly Cache</span></span>](../../app-domains/gac.md)
