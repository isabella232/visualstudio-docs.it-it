---
title: Requisiti per lo sviluppo di soluzioni di SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c9d6a726b290bfed1c086f9fb03290a37c91490
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118879"
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>Requisiti per lo sviluppo di soluzioni SharePoint
È necessario installare i prerequisiti seguenti nel sistema prima di poter usare gli strumenti di sviluppo di soluzioni SharePoint inclusi in Visual Studio:

- Visual Studio con c# e/o Visual Basic o un'edizione di Visual Studio Application Lifecycle Management (ALM).

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installazione a 64 bit [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] o a 64 bit [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

     oppure

- [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] installazione a 64 bit [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] o a 64 bit [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

> [!NOTE]
> Anche se solo i sistemi operativi server sono ufficialmente supportati da SharePoint, sono consentiti due sistemi operativi client: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] e [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1. Per altre informazioni, vedere [Guida all'installazione di SharePoint Server 2010 per sviluppatori Workstation](http://go.microsoft.com/fwlink/?LinkID=164557).

Tipi di progetto di modello di integrazione applicativa dei dati (BDC) aziendale richiedono che [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] essere installato nel sistema.

Per sviluppare soluzioni di SharePoint in Visual Studio, è necessario installare SharePoint nello stesso computer di Visual Studio. Inoltre, gli strumenti di sviluppo SharePoint supportano solo una configurazione autonoma di SharePoint; non supportano una configurazione di farm (remoto).

> [!NOTE]
> Progetti di SharePoint in Visual Studio supportano solo [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]. Se si seleziona [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] per un nuovo progetto di SharePoint, continueranno a utilizzare [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].

Per altre informazioni su come installare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vedere [installare Visual Studio](../install/install-visual-studio.md).

## <a name="vista-and-windows-7-user-account-control-uac"></a>Vista e Windows 7 controllo dell'Account utente (UAC)
[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporare funzionalità di sicurezza che è noto come controllo Account utente (UAC). Per sviluppare soluzioni di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sul [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] sistemi, controllo dell'account utente richiede l'esecuzione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come amministratore di sistema. Sul desktop, aprire il menu di scelta rapida [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], quindi scegliere **Esegui come amministratore**.

Per configurare il collegamento sul desktop per essere eseguita sempre come amministratore, aprire il menu di scelta rapida, scegliere **delle proprietà**, scegliere il **Advanced** e quindi selezionare il **Esegui come amministratore**  casella di controllo.

Per altre informazioni, vedere [Configuring User Account Control in Windows Vista e comprensione](http://go.microsoft.com/fwlink/?LinkID=156476). e [controllo Account utente di Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Considerazioni sulle autorizzazioni di SharePoint
Per sviluppare soluzioni di SharePoint, è necessario disporre delle autorizzazioni sufficienti per eseguire e il debug delle soluzioni di SharePoint. Prima di testare una soluzione di SharePoint, eseguire i passaggi seguenti per assicurarsi di avere le autorizzazioni necessarie:

1. Aggiungere l'account utente con privilegi di amministratore nel sistema.

2. Aggiungere l'account utente come amministratore di Farm per il server SharePoint.

    1. In Amministrazione centrale SharePoint, scegliere il **gestire il gruppo di amministratori farm** collegamento.

    2. Nel **gli amministratori di Farm** pagina, scegliere il **New** pulsante.

3. Aggiungere l'account utente per al gruppo WSS_ADMIN_WPG.

## <a name="see-also"></a>Vedere anche
[Iniziare a usare &#40;sviluppo per SharePoint in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
