---
title: クライアント アプリケーションに UI オートメーション プロバイダーを実装する
description: アプリケーションでクライアント側 UI オートメーション プロバイダーを実装する方法の例を確認します。 これは、一般的ではないシナリオであることに注意してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: 486e05f9080b686c48454dfcfceaaa666fa57f67
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269588"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>クライアント アプリケーションに UI オートメーション プロバイダーを実装する

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックのコード例では、アプリケーション内のクライアント側 UI オートメーション プロバイダーを実装する方法を示します。  
  
 これは、一般的ではないシナリオです。 通常は、UI オートメーション クライアント アプリケーションは、サーバー側プロバイダーを使用するか、または DLL 内に存在するクライアント側プロバイダーを使用します。  
  
## <a name="example"></a>例  

 次のコード例では、コンソール ウィンドウ用の簡単なプロバイダーを実装します。 このコードは、有用な機能は備えていませんが、クライアント コード内でプロバイダーを設定し、 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>を使用して登録する際の基本的な手順を示すために用意されています。  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション プロバイダーの概要](ui-automation-providers-overview.md)
- [クライアント側プロバイダー アセンブリの登録](register-a-client-side-provider-assembly.md)
- [クライアント側 UI オートメーション プロバイダーの作成](create-a-client-side-ui-automation-provider.md)
- [クライアント側 UI オートメーション プロバイダーの実装](client-side-ui-automation-provider-implementation.md)
