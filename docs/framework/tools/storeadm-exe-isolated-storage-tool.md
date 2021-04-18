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
ms.openlocfilehash: 89eb2b35dc640f21f3d6d6ca7f477841f1a020c7
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494039"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="43b26-104">Storeadm.exe (分離ストレージ ツール)</span><span class="sxs-lookup"><span data-stu-id="43b26-104">Storeadm.exe (Isolated Storage Tool)</span></span>

<span data-ttu-id="43b26-105">分離ストレージ ツールは、現在のユーザーに関するすべての既存ストアの一覧表示または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="43b26-105">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="43b26-106">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="43b26-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="43b26-107">ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。</span><span class="sxs-lookup"><span data-stu-id="43b26-107">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>
  
 <span data-ttu-id="43b26-108">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="43b26-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b26-109">構文</span><span class="sxs-lookup"><span data-stu-id="43b26-109">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="43b26-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="43b26-110">Parameters</span></span>  
  
|<span data-ttu-id="43b26-111">オプション</span><span class="sxs-lookup"><span data-stu-id="43b26-111">Option</span></span>|<span data-ttu-id="43b26-112">説明</span><span class="sxs-lookup"><span data-stu-id="43b26-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="43b26-113">**/h** **[elp]**</span><span class="sxs-lookup"><span data-stu-id="43b26-113">**/h**[**elp**]</span></span>|<span data-ttu-id="43b26-114">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="43b26-114">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="43b26-115">**/list**</span><span class="sxs-lookup"><span data-stu-id="43b26-115">**/list**</span></span>|<span data-ttu-id="43b26-116">現在のユーザーに関するすべての既存ストアを表示します。</span><span class="sxs-lookup"><span data-stu-id="43b26-116">Displays all existing stores for the current user.</span></span> <span data-ttu-id="43b26-117">このユーザーによって実行された、すべてのアプリケーションまたはアセンブリに関するストアなどが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43b26-117">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="43b26-118">**/machine**</span><span class="sxs-lookup"><span data-stu-id="43b26-118">**/machine**</span></span>|<span data-ttu-id="43b26-119">コンピューター ストアを選択します。</span><span class="sxs-lookup"><span data-stu-id="43b26-119">Selects the machine store.</span></span> <span data-ttu-id="43b26-120">このオプションを **/list** または **/remove** オプションと一緒に使用すると、それらのアクションをマシン ストアに適用する必要があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="43b26-120">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="43b26-121">.NET Framework 2.0 で新たに追加されました。</span><span class="sxs-lookup"><span data-stu-id="43b26-121">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="43b26-122">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="43b26-122">**/quiet**</span></span>|<span data-ttu-id="43b26-123">クワイエット モードを指定します。このモードでは、情報の出力が中止され、エラー メッセージだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43b26-123">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="43b26-124">**/remove**</span><span class="sxs-lookup"><span data-stu-id="43b26-124">**/remove**</span></span>|<span data-ttu-id="43b26-125">現在のユーザーに関するすべての既存ストアを削除します。</span><span class="sxs-lookup"><span data-stu-id="43b26-125">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="43b26-126">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="43b26-126">**/roaming**</span></span>|<span data-ttu-id="43b26-127">ローミング ストアを選択します。</span><span class="sxs-lookup"><span data-stu-id="43b26-127">Selects the roaming store.</span></span> <span data-ttu-id="43b26-128">このオプションを **/list** または **/remove** オプションと一緒に使用すると、それらのアクションをローミング ストアに適用する必要があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="43b26-128">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="43b26-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="43b26-129">**/?**</span></span>|<span data-ttu-id="43b26-130">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="43b26-130">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43b26-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="43b26-131">Remarks</span></span>  

 <span data-ttu-id="43b26-132">オプションを指定せずにコマンド ラインから Storeadm.exe を実行すると、Storeadm.exe に関する構文とオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43b26-132">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="43b26-133">一般に、 **/list** オプションと **/remove** オプションは同時に使用されますが、2 つ以上のオプションを指定した場合、それらのオプションはコマンド ラインに表示されている順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="43b26-133">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="43b26-134">アプリケーションは、ユーザー ストアまたはコンピューター ストアのいずれかを選択して保存できます。</span><span class="sxs-lookup"><span data-stu-id="43b26-134">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="43b26-135">ローカル ストアは、該当するユーザーに関するデータのローミングが有効な場合でも、ローミングされないことが保証されている場所に存在します。</span><span class="sxs-lookup"><span data-stu-id="43b26-135">The local store exists in a location that is guaranteed not to roam, even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="43b26-136">ローミング ストアは、ローミングできる場所に存在しますが、ローミングできるのは、Windows の管理機能を通じて、該当するユーザーに対してローミングが有効化されている場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="43b26-136">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows administration.</span></span>  
  
- <span data-ttu-id="43b26-137">コンピューター ストアは、コンピューターのすべてのユーザーに共通で、コンピューターの共通ディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="43b26-137">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>
  
<span data-ttu-id="43b26-138">ユーザーに対してローミングが実際に有効になっているかどうかは、Storeadm.exe の管理に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="43b26-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="43b26-139">オプションを指定せずに Storeadm.exe を実行した場合、すべてのアクションがローカル ストアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="43b26-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="43b26-140">**/roaming** オプションを指定した場合は、すべてのアクションが、ローミングできるストアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="43b26-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="43b26-141">**/machine** オプションを指定してこのツールを実行すると、すべてのアクションがコンピューター ストアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="43b26-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b26-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="43b26-142">See also</span></span>

- [<span data-ttu-id="43b26-143">ツール</span><span class="sxs-lookup"><span data-stu-id="43b26-143">Tools</span></span>](index.md)
- [<span data-ttu-id="43b26-144">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="43b26-144">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="43b26-145">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="43b26-145">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
