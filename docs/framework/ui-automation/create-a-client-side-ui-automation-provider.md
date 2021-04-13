---
title: クライアント側 UI オートメーション プロバイダーの作成
description: クライアント側 UI オートメーション プロバイダーを作成する方法の例を確認します。 例では、コンソール ウィンドウ用の簡単なクライアント側プロバイダーを実装します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: 17a6deca2efc67d1409e89f7accf7a3b89a27807
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276543"
---
# <a name="create-a-client-side-ui-automation-provider"></a>クライアント側 UI オートメーション プロバイダーの作成

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックのコード例では、クライアント側 UI オートメーション プロバイダーを実装する方法を示します。  
  
## <a name="example"></a>例  

 コンソール ウィンドウの非常に単純なクライアント側プロバイダーを実装するダイナミックリンク ライブラリ (DLL) に、次のコード例を組み込むことができます。 このコードは、有用な機能は備えていませんが、UI オートメーション クライアント アプリケーションによって登録できるプロバイダー アセンブリを設定する際の基本的な手順を示すために用意されています。  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション プロバイダーの概要](ui-automation-providers-overview.md)
- [クライアント側プロバイダー アセンブリの登録](register-a-client-side-provider-assembly.md)
