---
description: ': Fusion インターフェイスの詳細情報'
title: Fusion インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
ms.openlocfilehash: 3b6ca64b40ebc1a7b38129d897059ca628d3914c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761066"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="f1b40-103">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-103">Fusion Interfaces</span></span>

<span data-ttu-id="f1b40-104">このセクションでは、アプリケーションのリソースのプロパティにアクセスするために fusion API が使用するアンマネージインターフェイスについて説明し、アプリケーションのリソースの正しいバージョンを特定します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-104">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1b40-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f1b40-105">In This Section</span></span>  

 [<span data-ttu-id="f1b40-106">IAppIdAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-106">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="f1b40-107">アプリケーション id と参照のキーを生成して比較するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-107">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="f1b40-108">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-108">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="f1b40-109">グローバルアセンブリキャッシュの表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-109">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="f1b40-110">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-110">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="f1b40-111">グローバルアセンブリキャッシュ内の1つのアセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-111">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="f1b40-112">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-112">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="f1b40-113">オブジェクトの配列の列挙子を表し `IAssemblyName` ます。</span><span class="sxs-lookup"><span data-stu-id="f1b40-113">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="f1b40-114">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="f1b40-115">アセンブリの一意の id を記述および操作するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-115">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="f1b40-116">IDefinitionAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-116">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="f1b40-117">現在のスコープ内のアプリケーションを定義するコードの一意の識別子を表します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-117">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="f1b40-118">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="f1b40-119">現在のスコープ内のアプリケーションを定義するコードの一意の署名を表します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-119">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="f1b40-120">IEnumDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-120">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="f1b40-121">オブジェクトのコレクションの列挙子として機能し `IDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="f1b40-121">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="f1b40-122">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-122">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="f1b40-123">現在のスコープ内のコードオブジェクトの属性の列挙子として機能します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-123">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="f1b40-124">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-124">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="f1b40-125">オブジェクトのコレクションの列挙子として機能し `IReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="f1b40-125">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="f1b40-126">IIdentityAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-126">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="f1b40-127">コードオブジェクトの id キーを管理します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-127">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="f1b40-128">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-128">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="f1b40-129">グローバルアセンブリキャッシュにインストールされている参照アセンブリの列挙子を表します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-129">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="f1b40-130">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-130">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="f1b40-131">グローバルアセンブリキャッシュにインストールされている項目を表します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-131">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="f1b40-132">IReferenceAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-132">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="f1b40-133">現在のスコープ内のアプリケーションの一意の識別子への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-133">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="f1b40-134">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1b40-134">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="f1b40-135">コードオブジェクトの一意の署名への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="f1b40-135">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f1b40-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1b40-136">Reference</span></span>  

 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="f1b40-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1b40-137">Related Sections</span></span>  

 [<span data-ttu-id="f1b40-138">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="f1b40-138">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="f1b40-139">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="f1b40-139">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="f1b40-140">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="f1b40-140">Fusion Structures</span></span>](fusion-structures.md)
