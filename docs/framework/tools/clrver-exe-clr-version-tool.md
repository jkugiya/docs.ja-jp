---
title: Clrver.exe (CLR バージョン ツール)
description: Clrver.exe (CLR バージョン ツール) を確認します。 このツールによって、コンピューターにインストールされている共通言語ランタイム (CLR) のすべてのバージョンが報告されます。
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: 0787cdf09d55a8464db7f5495b5aeed52c22f5d4
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654181"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="0e6fb-104">Clrver.exe (CLR バージョン ツール)</span><span class="sxs-lookup"><span data-stu-id="0e6fb-104">Clrver.exe (CLR Version Tool)</span></span>

<span data-ttu-id="0e6fb-105">CLR バージョン ツール (Clrver.exe) は、コンピューターにインストールされている共通言語ランタイム (CLR: Common Language Runtime) のすべてのバージョンを報告します。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-105">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="0e6fb-106">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="0e6fb-107">ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-107">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="0e6fb-108">コマンド プロンプトで、次のコマンドを入力します:</span><span class="sxs-lookup"><span data-stu-id="0e6fb-108">At the command prompt, enter the following command:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e6fb-109">構文</span><span class="sxs-lookup"><span data-stu-id="0e6fb-109">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="0e6fb-110">Options</span><span class="sxs-lookup"><span data-stu-id="0e6fb-110">Options</span></span>  
  
|<span data-ttu-id="0e6fb-111">オプション</span><span class="sxs-lookup"><span data-stu-id="0e6fb-111">Option</span></span>|<span data-ttu-id="0e6fb-112">説明</span><span class="sxs-lookup"><span data-stu-id="0e6fb-112">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="0e6fb-113">CLR を使用しているコンピューター上のすべてのプロセスを表示します。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-113">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="0e6fb-114">*pid*</span><span class="sxs-lookup"><span data-stu-id="0e6fb-114">*pid*</span></span>|<span data-ttu-id="0e6fb-115">指定したプロセス ID (PID) のプロセスで使用されている CLR のバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-115">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="0e6fb-116">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-116">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e6fb-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="0e6fb-117">Remarks</span></span>  

 <span data-ttu-id="0e6fb-118">オプションを指定せずに Clrver.exe を呼び出した場合、インストールされている CLR のすべてのバージョンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-118">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="0e6fb-119">別のユーザーの PID を指定する場合、バージョン情報を取得するには、管理アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-119">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e6fb-120">Windows Vista 以降では、ユーザー アカウント制御 (UAC: User Account Control) でユーザーの権限が決定されます。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-120">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="0e6fb-121">ユーザーが組み込みの Administrators グループのメンバーである場合、そのユーザーには標準ユーザー アクセス トークンおよび管理者アクセス トークンの 2 つのランタイム アクセス トークンが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-121">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="0e6fb-122">既定では、ユーザーは標準ユーザー ロールに所属します。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-122">By default, you are in the standard user role.</span></span> <span data-ttu-id="0e6fb-123">管理アクセス許可を必要とするコードを実行するには、最初に、ユーザーの権限を標準ユーザーから管理者に昇格させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-123">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="0e6fb-124">この操作は、コマンド プロンプトの起動時にコマンド プロンプト アイコンを右クリックし、管理者として実行することを指定して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-124">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="0e6fb-125">SYSTEM、LOCAL SERVICE、および NETWORK SERVICE の各プロセスの CLR バージョンを確認しようとすると、PID が存在しないことを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-125">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0e6fb-126">使用例</span><span class="sxs-lookup"><span data-stu-id="0e6fb-126">Examples</span></span>  

 <span data-ttu-id="0e6fb-127">コンピューターにインストールされている CLR のすべてのバージョンを表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-127">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="0e6fb-128">プロセス 128 で使用されている CLR のバージョンを表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-128">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="0e6fb-129">すべてのマネージド プロセスとそれらのプロセスで使用されている CLR のバージョンを表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0e6fb-129">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="0e6fb-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e6fb-130">See also</span></span>

- [<span data-ttu-id="0e6fb-131">ツール</span><span class="sxs-lookup"><span data-stu-id="0e6fb-131">Tools</span></span>](index.md)
- [<span data-ttu-id="0e6fb-132">開発者コマンドライン シェル</span><span class="sxs-lookup"><span data-stu-id="0e6fb-132">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
