---
title: トラブルシューティング:サービス アプリケーションをインストールできない場合
description: サービス アプリケーションをインストールできない場合には、トラブルシューティングを行います。 サービスクラスの ServiceName プロパティが正しく設定されていることを確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
ms.openlocfilehash: 057fe52d43daad90df862c3acaec41a427333cba
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494429"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="d01d3-104">トラブルシューティング:サービス アプリケーションをインストールできない場合</span><span class="sxs-lookup"><span data-stu-id="d01d3-104">Troubleshooting: Service Application Won't Install</span></span>

<span data-ttu-id="d01d3-105">サービス アプリケーションが正しくインストールされない場合は、サービス クラスの <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティが、そのサービスのインストーラーで示されているのと同じ値に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d01d3-105">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="d01d3-106">サービスが正しくインストールされるためには、両方のインスタンスで同じ値になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d01d3-106">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d01d3-107">また、インストール ログを見て、インストール プロセスについてのフィードバックを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="d01d3-107">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="d01d3-108">同じ名前の別のサービスが既にインストールされているかどうかも確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d01d3-108">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="d01d3-109">インストールが成功するには、サービス名が一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d01d3-109">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d01d3-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d01d3-110">See also</span></span>

- [<span data-ttu-id="d01d3-111">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="d01d3-111">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
