---
description: 詳細については、「Fusion グローバル静的関数」を参照してください。
title: Fusion グローバル静的関数
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
ms.openlocfilehash: c696908f72d67ecff5e7383e7a2754dd5436b819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761084"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="4d925-103">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="4d925-103">Fusion Global Static Functions</span></span>

<span data-ttu-id="4d925-104">このセクションでは、fusion API が使用するアンマネージグローバル静的関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="4d925-104">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4d925-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4d925-105">In This Section</span></span>  

 [<span data-ttu-id="4d925-106">ClearDownloadCache 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-106">ClearDownloadCache Function</span></span>](cleardownloadcache-function.md)  
 <span data-ttu-id="4d925-107">ダウンロードされたアセンブリのグローバルアセンブリキャッシュを消去します。</span><span class="sxs-lookup"><span data-stu-id="4d925-107">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="4d925-108">CompareAssemblyIdentity 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-108">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)  
 <span data-ttu-id="4d925-109">2つのアセンブリ id を比較して、それらが等しいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="4d925-109">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="4d925-110">CreateApplicationContext 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-110">CreateApplicationContext Function</span></span>](createapplicationcontext-function.md)  
 <span data-ttu-id="4d925-111">内部でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="4d925-111">Internal only.</span></span> <span data-ttu-id="4d925-112">(この関数は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません)。</span><span class="sxs-lookup"><span data-stu-id="4d925-112">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="4d925-113">CreateAssemblyCache 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-113">CreateAssemblyCache Function</span></span>](createassemblycache-function.md)  
 <span data-ttu-id="4d925-114">グローバルアセンブリキャッシュを表す新しい [Iassemblycache](iassemblycache-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-114">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="4d925-115">CreateAssemblyEnum 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-115">CreateAssemblyEnum Function</span></span>](createassemblyenum-function.md)  
 <span data-ttu-id="4d925-116">指定したアセンブリ内に存在するオブジェクトのリストを表す [Iassemblyenum](iassemblyenum-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-116">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="4d925-117">CreateAssemblyNameObject 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-117">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)  
 <span data-ttu-id="4d925-118">指定した名前のアセンブリの一意の id を表す [IAssemblyName](iassemblyname-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-118">Gets a pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="4d925-119">CreateHistoryReader 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-119">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)  
 <span data-ttu-id="4d925-120">指定されたファイルの履歴リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d925-120">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="4d925-121">CreateInstallReferenceEnum 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-121">CreateInstallReferenceEnum Function</span></span>](createinstallreferenceenum-function.md)  
 <span data-ttu-id="4d925-122">指定したアセンブリへのアプリケーションの参照のリストを表す [Iinstallreferenceenum](iinstallreferenceenum-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-122">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="4d925-123">GetAppIdAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-123">GetAppIdAuthority Function</span></span>](getappidauthority-function.md)  
 <span data-ttu-id="4d925-124">アプリケーション id と参照のキーを管理する [Iappidauthority](iappidauthority-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-124">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="4d925-125">GetAssemblyIdentityFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-125">GetAssemblyIdentityFromFile Function</span></span>](getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="4d925-126">指定した `IUnknown` `IID` ファイルパスのアセンブリ内で、指定したを持つオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-126">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="4d925-127">GetCachePath 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-127">GetCachePath Function</span></span>](getcachepath-function.md)  
 <span data-ttu-id="4d925-128">指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-128">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="4d925-129">GetHistoryFileDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-129">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)  
 <span data-ttu-id="4d925-130">アプリケーション履歴ディレクトリのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-130">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="4d925-131">GetIdentityAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-131">GetIdentityAuthority Function</span></span>](getidentityauthority-function.md)  
 <span data-ttu-id="4d925-132">コードオブジェクトのキーを管理する [Iidentity authority](iidentityauthority-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-132">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="4d925-133">IsFrameworkAssembly 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-133">IsFrameworkAssembly Function</span></span>](isframeworkassembly-function.md)  
 <span data-ttu-id="4d925-134">指定したアセンブリが管理されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-134">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="4d925-135">NukeDownloadedCache 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-135">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)  
 <span data-ttu-id="4d925-136">共通言語ランタイムのダウンロードキャッシュを削除します。</span><span class="sxs-lookup"><span data-stu-id="4d925-136">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="4d925-137">PreBindAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="4d925-137">PreBindAssemblyEx Function</span></span>](prebindassemblyex-function.md)  
 <span data-ttu-id="4d925-138">アセンブリのポリシー後の表示名を取得します。</span><span class="sxs-lookup"><span data-stu-id="4d925-138">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4d925-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d925-139">Related Sections</span></span>  

 [<span data-ttu-id="4d925-140">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d925-140">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="4d925-141">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="4d925-141">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="4d925-142">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="4d925-142">Fusion Structures</span></span>](fusion-structures.md)  
  
 [<span data-ttu-id="4d925-143">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="4d925-143">Global Assembly Cache</span></span>](../../app-domains/gac.md)
