---
title: CorFlags.exe (CorFlags 変換ツール)
description: CorFlags.exe (CorFlags 変換ツール) を理解します。 このツールにより、ポータブル実行可能ファイル イメージのヘッダー内の CorFlags セクションを構成できます。
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: 4481e6718372fe7b58dbc05ab7cfe35e6d3047ce
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258053"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (CorFlags 変換ツール)

CorFlags 変換ツールを使用して、ポータブル実行可能 (PE) ファイル イメージのヘッダー内の CorFlags セクションを設定できます。  
  
 このツールは、Visual Studio と共に自動的にインストールされます。 ツールを実行するには、[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を使用します。  
  
 コマンド プロンプトに次のように入力します。  
  
## <a name="syntax"></a>構文  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a>パラメーター  
  
|必須パラメーター|説明|  
|------------------------|-----------------|  
|`assembly`|CorFlags を設定するアセンブリの名前。|  
  
|オプション|説明|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|32BITREQUIRED フラグを設定します。|  
|`-32BIT[REQ]-`|32BITREQUIRED フラグをクリアします。|  
|`-32BITPREF+`|32BITPREFERRED フラグを設定します。 アプリは、64 ビット プラットフォーム上でも 32 ビット プロセスとして実行します。 このフラグは、EXE ファイルでのみ設定します。 このフラグを DLL で設定した場合、64 ビット プロセスで DLL を読み込むことができず、<xref:System.BadImageFormatException> 例外がスローされます。 このフラグを設定した EXE ファイルは、64 ビット プロセスで読み込むことができます。<br /><br /> .NET Framework 4.5 で新たに追加されました。|  
|`-32BITPREF-`|32BITPREFERRED フラグをクリアします。<br /><br /> .NET Framework 4.5 で新たに追加されました。|  
|`-?`|このツールのコマンド構文とオプションを表示します。|  
|`-Force`|厳密な名前が付けられているアセンブリであっても、強制的に更新します。 **重要:** 厳密な名前が付けられているアセンブリを更新する場合は、そのコードを実行する前に再署名する必要があります。|  
|`-help`|このツールのコマンド構文とオプションを表示します。|  
|`-ILONLY+`|ILONLY フラグを設定します。|  
|`-ILONLY-`|ILONLY フラグをクリアします。|  
|`-nologo`|Microsoft 著作権情報を表示しません。|  
|`-RevertCLRHeader`|CLR ヘッダー バージョンを 2.0 に戻します。|  
|`-UpgradeCLRHeader`|CLR ヘッダー バージョンを 2.5 にアップグレードします。 **注:** アセンブリをネイティブに実行するには、CLR ヘッダー バージョン 2.5 以降が必要です。|  
  
## <a name="remarks"></a>Remarks  

 オプションが何も指定されていない場合、CorFlags 変換ツールは指定されているアセンブリのフラグを表示します。  
  
## <a name="see-also"></a>関連項目

- [ツール](index.md)
- [64 ビット アプリケーション](../64-bit-apps.md)
- [開発者コマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)
