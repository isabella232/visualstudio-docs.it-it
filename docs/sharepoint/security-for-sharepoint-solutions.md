---
title: Sicurezza per SharePoint soluzioni | Microsoft Docs
description: Scoprire le funzionalità Visual Studio incorporate per migliorare la sicurezza delle applicazioni SharePoint applicazioni.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d287552b07f67c7415688fefd87f876242b230f4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635563"
---
# <a name="security-for-sharepoint-solutions"></a>Sicurezza per SharePoint soluzioni
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]incorpora le funzionalità seguenti per migliorare la sicurezza delle SharePoint applicazioni.

## <a name="safe-control-entries"></a>Cassaforte voci di controllo
 Ogni SharePoint di progetto creato in ha una [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] **proprietà Cassaforte Control Entries** che rappresenta una raccolta di controlli sicuri. La **Cassaforte** sottoproprietà consente di specificare i controlli da considerare sicuri. Per altre informazioni, vedere [Fornire informazioni sul pacchetto e sulla distribuzione negli](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) elementi del progetto e Specifica [Cassaforte Web part](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts).

## <a name="allowpartiallytrustedcallers-attribute"></a>attributo AllowPartiallyTrustedCallers
 Per impostazione predefinita, solo le applicazioni completamente attendibili dal sistema di sicurezza dall'accesso di codice di runtime possono accedere a un assembly di codice gestito condiviso. Contrassegnare un assembly completamente attendibile con l'attributo AllowPartiallyTrustedCallers consente agli assembly parzialmente attendibili di accedervi.

 L'attributo AllowPartiallyTrustedCallers viene aggiunto a qualsiasi SharePoint soluzione non distribuita nella Global Assembly Cache di sistema ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). Sono incluse soluzioni in modalità sandbox o soluzioni distribuite nella SharePoint bin dell'applicazione. Per altre informazioni, vedere Modifiche alla [sicurezza della versione 1](/previous-versions/msp-n-p/ff921345(v=pandp.10)) per Microsoft .NET Framework e Distribuzione di Web part [in SharePoint Foundation.](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))

## <a name="safe-against-script-property"></a>Cassaforte sulla proprietà script
 *L'inserimento* di script injection è l'inserimento di codice potenzialmente dannoso in controlli o pagine Web. Per proteggere i SharePoint 2010 da script injection, i collaboratori non possono visualizzare o modificare le web part o le relative proprietà per impostazione predefinita. Questo comportamento è controllato da un attributo SafeControl denominato SafeAgainstScript. In impostare questo attributo nella sottoproprietà Voci di controllo Cassaforte di un elemento di progetto Cassaforte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Su script**.  Per altre informazioni, vedere [Fornire informazioni sul pacchetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e sulla distribuzione negli elementi del progetto e [Procedura: Contrassegnare i controlli come controlli sicuri.](../sharepoint/how-to-mark-controls-as-safe-controls.md)

## <a name="vista-and-windows-7-user-account-control"></a>Controllo dell'account utente di Vista e Windows 7
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporano una funzionalità di sicurezza nota come Controllo dell'account utente. Per sviluppare SharePoint soluzioni nei sistemi e , il controllo dell'account utente richiede [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] l'esecuzione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come amministratore di sistema. Dal menu **Start** aprire il menu di scelta rapida per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e quindi scegliere Esegui come **amministratore**.

 Per configurare il collegamento per l'esecuzione sempre come amministratore, aprire il relativo menu di scelta rapida, scegliere Proprietà, scegliere il pulsante Avanzate nella finestra di dialogo Proprietà e quindi selezionare la casella di controllo Esegui come [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] amministratore.    

 Per altre informazioni, vedere [Informazioni e configurazione del controllo dell'account utente in Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). e [Windows 7 Controllo dell'account utente](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10)).

## <a name="sharepoint-permissions-considerations"></a>SharePoint sulle autorizzazioni
 Per sviluppare SharePoint soluzioni, è necessario disporre di autorizzazioni sufficienti per eseguire ed eseguire il debug SharePoint soluzioni. Prima di testare una soluzione SharePoint, seguire questa procedura per assicurarsi di disporre delle autorizzazioni necessarie:

1. Aggiungere l'account utente come amministratore nel sistema.

2. Aggiungere l'account utente come amministratore farm per il server SharePoint server.

    1. In SharePoint 2010 Central Administration (Amministrazione centrale 2010) scegliere **il collegamento Manage the farm administrators group (Gestisci** il gruppo amministratori farm).

    2. Nella pagina **Amministratori farm** scegliere l'opzione **di** menu Nuovo

3. Aggiungere l'account utente al gruppo WSS_ADMIN_WPG utente.

## <a name="additional-security-resources"></a>Risorse di sicurezza aggiuntive
 Per altre informazioni sui problemi di sicurezza, vedere quanto segue.

### <a name="visual-studio-security"></a>sicurezza Visual Studio

- [Sicurezza e autorizzazioni utente](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [Sicurezza nel codice nativo e nel codice .NET Framework](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [Sicurezza in .NET Framework](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>SharePoint sicurezza

- [SharePoint Amministrazione e sicurezza di Foundation](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [SharePoint Centro risorse per la sicurezza](/sharepoint/dev/)

- [Protezione dei Web part in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [Miglioramento della sicurezza delle applicazioni Web: minacce e contromisure](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>Sicurezza generale

- [Ciclo di vita dello sviluppo per la sicurezza MSDN](https://www.microsoft.com/msrc?rtc=1)

- [Come compilare applicazioni ASP.NET protette: autenticazione, autorizzazione e comunicazioni protette (la pagina potrebbe essere in inglese)](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>Vedi anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)