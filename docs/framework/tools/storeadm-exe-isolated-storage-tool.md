---
title: Storeadm.exe (分離ストレージ ツール)
description: Storeadm.exe (分離ストレージ ツール) について説明します。 このツールによって、現在のユーザーに関するすべての既存ストアの一覧表示または削除を行うことができます。
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
ms.openlocfilehash: e6c2fc15ba2b6fef27bb57344628638a99103916
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258739"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="e79f1-104">Storeadm.exe (分離ストレージ ツール)</span><span class="sxs-lookup"><span data-stu-id="e79f1-104">Storeadm.exe (Isolated Storage Tool)</span></span>

<span data-ttu-id="e79f1-105">分離ストレージ ツールは、現在のユーザーに関するすべての既存ストアの一覧表示または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="e79f1-105">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="e79f1-106">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="e79f1-107">ツールを実行するには、[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を使用します。</span><span class="sxs-lookup"><span data-stu-id="e79f1-107">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>
  
 <span data-ttu-id="e79f1-108">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="e79f1-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e79f1-109">構文</span><span class="sxs-lookup"><span data-stu-id="e79f1-109">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="e79f1-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e79f1-110">Parameters</span></span>  
  
|<span data-ttu-id="e79f1-111">オプション</span><span class="sxs-lookup"><span data-stu-id="e79f1-111">Option</span></span>|<span data-ttu-id="e79f1-112">説明</span><span class="sxs-lookup"><span data-stu-id="e79f1-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e79f1-113">**/h** **[elp]**</span><span class="sxs-lookup"><span data-stu-id="e79f1-113">**/h**[**elp**]</span></span>|<span data-ttu-id="e79f1-114">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="e79f1-114">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="e79f1-115">**/list**</span><span class="sxs-lookup"><span data-stu-id="e79f1-115">**/list**</span></span>|<span data-ttu-id="e79f1-116">現在のユーザーに関するすべての既存ストアを表示します。</span><span class="sxs-lookup"><span data-stu-id="e79f1-116">Displays all existing stores for the current user.</span></span> <span data-ttu-id="e79f1-117">このユーザーによって実行された、すべてのアプリケーションまたはアセンブリに関するストアなどが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-117">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="e79f1-118">**/machine**</span><span class="sxs-lookup"><span data-stu-id="e79f1-118">**/machine**</span></span>|<span data-ttu-id="e79f1-119">コンピューター ストアを選択します。</span><span class="sxs-lookup"><span data-stu-id="e79f1-119">Selects the machine store.</span></span> <span data-ttu-id="e79f1-120">このオプションを **/list** または **/remove** オプションと一緒に使用すると、それらのアクションをマシン ストアに適用する必要があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-120">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="e79f1-121">.NET Framework 2.0 で新たに追加されました。</span><span class="sxs-lookup"><span data-stu-id="e79f1-121">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="e79f1-122">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="e79f1-122">**/quiet**</span></span>|<span data-ttu-id="e79f1-123">クワイエット モードを指定します。このモードでは、情報の出力が中止され、エラー メッセージだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-123">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="e79f1-124">**/remove**</span><span class="sxs-lookup"><span data-stu-id="e79f1-124">**/remove**</span></span>|<span data-ttu-id="e79f1-125">現在のユーザーに関するすべての既存ストアを削除します。</span><span class="sxs-lookup"><span data-stu-id="e79f1-125">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="e79f1-126">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="e79f1-126">**/roaming**</span></span>|<span data-ttu-id="e79f1-127">ローミング ストアを選択します。</span><span class="sxs-lookup"><span data-stu-id="e79f1-127">Selects the roaming store.</span></span> <span data-ttu-id="e79f1-128">このオプションを **/list** または **/remove** オプションと一緒に使用すると、それらのアクションをローミング ストアに適用する必要があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-128">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="e79f1-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="e79f1-129">**/?**</span></span>|<span data-ttu-id="e79f1-130">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="e79f1-130">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e79f1-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="e79f1-131">Remarks</span></span>  

 <span data-ttu-id="e79f1-132">オプションを指定せずにコマンド ラインから Storeadm.exe を実行すると、Storeadm.exe に関する構文とオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-132">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="e79f1-133">一般に、 **/list** オプションと **/remove** オプションは同時に使用されますが、2 つ以上のオプションを指定した場合、それらのオプションはコマンド ラインに表示されている順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-133">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="e79f1-134">アプリケーションは、ユーザー ストアまたはコンピューター ストアのいずれかを選択して保存できます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-134">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="e79f1-135">ローカル ストアは、該当するユーザーに関するデータのローミングが有効な場合でも、ローミングされないことが保証されている場所 (Windows 2000 以降) に存在します。</span><span class="sxs-lookup"><span data-stu-id="e79f1-135">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="e79f1-136">ローミング ストアは、ローミングできる場所に存在しますが、ローミングできるのは、Windows NT の管理機能を通じて、該当するユーザーに対してローミングが有効化されている場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-136">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="e79f1-137">コンピューター ストアは、コンピューターのすべてのユーザーに共通で、コンピューターの共通ディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-137">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e79f1-138">コンピューター ストアは .NET Framework Version 2.0 で新たに追加されました。</span><span class="sxs-lookup"><span data-stu-id="e79f1-138">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="e79f1-139">ユーザーに対してローミングが実際に有効になっているかどうかは、Storeadm.exe の管理に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="e79f1-139">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="e79f1-140">オプションを指定せずに Storeadm.exe を実行した場合、すべてのアクションがローカル ストアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-140">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="e79f1-141">**/roaming** オプションを指定した場合は、すべてのアクションが、ローミングできるストアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-141">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="e79f1-142">**/machine** オプションを指定してこのツールを実行すると、すべてのアクションがコンピューター ストアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e79f1-142">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e79f1-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="e79f1-143">See also</span></span>

- [<span data-ttu-id="e79f1-144">ツール</span><span class="sxs-lookup"><span data-stu-id="e79f1-144">Tools</span></span>](index.md)
- [<span data-ttu-id="e79f1-145">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="e79f1-145">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="e79f1-146">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="e79f1-146">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
