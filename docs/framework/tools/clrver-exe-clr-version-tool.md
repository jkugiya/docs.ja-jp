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
# <a name="clrverexe-clr-version-tool"></a>Clrver.exe (CLR バージョン ツール)

CLR バージョン ツール (Clrver.exe) は、コンピューターにインストールされている共通言語ランタイム (CLR: Common Language Runtime) のすべてのバージョンを報告します。  
  
 このツールは、Visual Studio と共に自動的にインストールされます。 ツールを実行するには、[、Visual Studio 開発者コマンド プロンプトまたは Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell) を使用します。  
  
 コマンド プロンプトで、次のコマンドを入力します:  
  
## <a name="syntax"></a>構文  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a>Options  
  
|オプション|説明|  
|------------|-----------------|  
|`-all`|CLR を使用しているコンピューター上のすべてのプロセスを表示します。|  
|*pid*|指定したプロセス ID (PID) のプロセスで使用されている CLR のバージョンを表示します。|  
|`-?`|このツールのコマンド構文とオプションを表示します。|  
  
## <a name="remarks"></a>Remarks  

 オプションを指定せずに Clrver.exe を呼び出した場合、インストールされている CLR のすべてのバージョンが表示されます。 別のユーザーの PID を指定する場合、バージョン情報を取得するには、管理アクセス許可が必要です。  
  
> [!NOTE]
> Windows Vista 以降では、ユーザー アカウント制御 (UAC: User Account Control) でユーザーの権限が決定されます。 ユーザーが組み込みの Administrators グループのメンバーである場合、そのユーザーには標準ユーザー アクセス トークンおよび管理者アクセス トークンの 2 つのランタイム アクセス トークンが割り当てられています。 既定では、ユーザーは標準ユーザー ロールに所属します。 管理アクセス許可を必要とするコードを実行するには、最初に、ユーザーの権限を標準ユーザーから管理者に昇格させる必要があります。 この操作は、コマンド プロンプトの起動時にコマンド プロンプト アイコンを右クリックし、管理者として実行することを指定して行うことができます。  
  
 SYSTEM、LOCAL SERVICE、および NETWORK SERVICE の各プロセスの CLR バージョンを確認しようとすると、PID が存在しないことを示すメッセージが表示されます。  
  
## <a name="examples"></a>使用例  

 コンピューターにインストールされている CLR のすべてのバージョンを表示するコマンドを次に示します。  
  
 `clrver`  
  
 プロセス 128 で使用されている CLR のバージョンを表示するコマンドを次に示します。  
  
 `clrver 128`  
  
 すべてのマネージド プロセスとそれらのプロセスで使用されている CLR のバージョンを表示するコマンドを次に示します。  
  
 `Clrver -all`  
  
## <a name="see-also"></a>関連項目

- [ツール](index.md)
- [開発者コマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)
