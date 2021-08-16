---
title: Sicurezza per SharePoint soluzioni | Microsoft Docs
description: Informazioni sulle funzionalità Visual Studio incorporate per migliorare la sicurezza delle SharePoint applicazioni.
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
ms.openlocfilehash: c46356124b7ed957d3ff61d4118ade2638538d242686875f4a69972b254a3a16
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367466"
---
# <a name="security-for-sharepoint-solutions"></a>Sicurezza per SharePoint soluzioni
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]include le funzionalità seguenti per migliorare la sicurezza delle SharePoint applicazioni.

## <a name="safe-control-entries"></a>Cassaforte voci di controllo
 Ogni SharePoint di progetto creato in ha una [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Cassaforte proprietà Control **Entries** che rappresenta una raccolta di controlli sicuri. La **Cassaforte** sottoproprietà consente di specificare i controlli che si considerano sicuri. Per altre informazioni, vedere [Fornire informazioni sul pacchetto e sulla distribuzione negli elementi del progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e Specifica [Cassaforte Web part](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts).

## <a name="allowpartiallytrustedcallers-attribute"></a>attributo AllowPartiallyTrustedCallers
 Per impostazione predefinita, solo le applicazioni completamente attendibili dal sistema di sicurezza dall'accesso di codice di runtime possono accedere a un assembly di codice gestito condiviso. Contrassegnare un assembly completamente attendibile con l'attributo AllowPartiallyTrustedCallers consente agli assembly parzialmente attendibili di accedervi.

 L'attributo AllowPartiallyTrustedCallers viene aggiunto a qualsiasi soluzione SharePoint non distribuita nella Global Assembly Cache di sistema ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). Sono incluse le soluzioni in modalità sandbox o le soluzioni distribuite nella directory bin SharePoint dell'applicazione. Per altre informazioni, vedere [Version 1 Security Changes for the Microsoft .NET Framework](/previous-versions/msp-n-p/ff921345(v=pandp.10)) and [Deploying Web part in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

## <a name="safe-against-script-property"></a>Cassaforte sulla proprietà script
 *L'inserimento* di script è l'inserimento di codice potenzialmente dannoso in controlli o pagine Web. Per proteggere i SharePoint 2010 dall'inserimento di script, i collaboratori non possono visualizzare o modificare le web part o le relative proprietà per impostazione predefinita. Questo comportamento è controllato da un attributo SafeControl denominato SafeAgainstScript. In [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] impostare questo attributo nella sottoproprietà Control **Entries** Cassaforte di un elemento di progetto Cassaforte **Against Script**. Per altre informazioni, vedere [Fornire informazioni su pacchetti e distribuzioni negli](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) elementi del progetto e [Procedura: Contrassegnare i controlli come controlli sicuri.](../sharepoint/how-to-mark-controls-as-safe-controls.md)

## <a name="vista-and-windows-7-user-account-control"></a>Controllo dell'account utente Windows Vista e Windows 7
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporano una funzionalità di sicurezza nota come Controllo dell'account utente. Per sviluppare SharePoint in sistemi e , Controllo dell'account utente richiede [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] l'esecuzione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come amministratore di sistema. Dal menu **Start** aprire il menu di scelta rapida per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , quindi scegliere Esegui come **amministratore**.

 Per configurare il collegamento per l'esecuzione sempre come amministratore, aprire il relativo menu di scelta rapida, scegliere Proprietà , scegliere il pulsante Avanzate nella finestra di dialogo Proprietà e quindi selezionare la casella di controllo Esegui come [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] amministratore .    

 Per altre informazioni, vedere [Understanding and Configuring User Account Control in Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). e [Windows 7 Controllo dell'account utente](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10)).

## <a name="sharepoint-permissions-considerations"></a>SharePoint sulle autorizzazioni
 Per sviluppare SharePoint, è necessario disporre di autorizzazioni sufficienti per l'esecuzione e il debug SharePoint soluzioni. Prima di poter testare una SharePoint, seguire questa procedura per assicurarsi di disporre delle autorizzazioni necessarie:

1. Aggiungere l'account utente come amministratore nel sistema.

2. Aggiungere l'account utente come amministratore della farm per il server SharePoint server.

    1. In SharePoint 2010 Central Administration scegliere il **collegamento Manage the farm administrators group (Gestisci il** gruppo amministratori farm).

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

- [Ciclo di vita dello sviluppo della sicurezza MSDN](https://www.microsoft.com/msrc?rtc=1)

- [Come compilare applicazioni ASP.NET protette: autenticazione, autorizzazione e comunicazioni protette (la pagina potrebbe essere in inglese)](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>Vedi anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)