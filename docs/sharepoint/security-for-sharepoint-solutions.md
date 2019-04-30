---
title: Sicurezza per le soluzioni SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 31bcd41dc1a6fd7f314c7d701f52c3728dd2ee8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009801"
---
# <a name="security-for-sharepoint-solutions"></a>Sicurezza per le soluzioni SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incorpora le funzionalità seguenti che consentono di migliorare la sicurezza delle applicazioni di SharePoint.

## <a name="safe-control-entries"></a>Voci di controllo sicure
 Ogni elemento del progetto SharePoint creato nella [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] ha un **voci di controllo sicure** insieme di controlli di proprietà che rappresenta una cassaforte. Relativi **sicuro** sottoproprietà consente di specificare i controlli che si ritengano protetto. Per altre informazioni, vedere [fornire le informazioni del pacchetto e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [specifica di Web part sicure](http://go.microsoft.com/fwlink/?LinkId=177521).

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers attribute
 Per impostazione predefinita, solo le applicazioni considerate completamente attendibili dal sistema di sicurezza (CA) di accesso di codice runtime possono accedere a un assembly di codice gestito condiviso. Contrassegnare un assembly completamente attendibile con l'attributo AllowPartiallyTrustedCallers consente agli assembly parzialmente attendibili per accedervi.

 L'attributo AllowPartiallyTrustedCallers viene aggiunto a qualsiasi soluzione di SharePoint che viene distribuito non in cache assembly globali del sistema ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Ad esempio soluzioni create mediante sandbox o soluzioni distribuite nella directory Bin dell'applicazione SharePoint. Per altre informazioni, vedere [modifiche della sicurezza versione 1 per Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) e [distribuzione di Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).

## <a name="safe-against-script-property"></a>Proprietà sicurezza script
 *Creare uno script injection* consiste nell'inserimento di codice potenzialmente dannoso in controlli o le pagine Web. Per proteggersi dagli attacchi script injection i siti di SharePoint 2010, i collaboratori non è possibile visualizzare o modificare le Web part o le relative proprietà per impostazione predefinita. Questo comportamento è controllato da un attributo di SafeControl denominato SafeAgainstScript. Nelle [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)], impostare questo attributo in un elemento di progetto **voci di controllo sicure** sottoproprietà **sicurezza Script**. Per altre informazioni, vedere [fornire le informazioni del pacchetto e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [come: Contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Vista e Windows 7 User Account Control
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporare una funzionalità di sicurezza nota come controllo Account utente (UAC). Per sviluppare soluzioni di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sul [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] sistemi, controllo dell'account utente richiede l'esecuzione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come amministratore di sistema. Dal **avviare** menu, aprire il menu di scelta rapida per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], quindi scegliere **Esegui come amministratore**.

 Per configurare il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scelta rapida per sempre Esegui come amministratore, aprire il menu di scelta rapida, scegliere **delle proprietà**, scegliere il **avanzate** pulsante nel **proprietà**finestra di dialogo e quindi selezionare il **Esegui come amministratore** casella di controllo.

 Per altre informazioni, vedere [Configuring User Account Control in Windows Vista e comprensione](http://go.microsoft.com/fwlink/?LinkID=156476). e [controllo Account utente di Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Considerazioni sulle autorizzazioni di SharePoint
 Per sviluppare soluzioni di SharePoint, è necessario disporre delle autorizzazioni sufficienti per eseguire e il debug delle soluzioni di SharePoint. Prima di testare una soluzione di SharePoint, eseguire i passaggi seguenti per assicurarsi di avere le autorizzazioni necessarie:

1. Aggiungere l'account utente con privilegi di amministratore nel sistema.

2. Aggiungere l'account utente come amministratore di Farm per il server SharePoint.

    1. In Amministrazione centrale SharePoint 2010, scegliere il **gestire il gruppo di amministratori farm** collegamento.

    2. Nel **gli amministratori di Farm** pagina, scegliere il **New** l'opzione di menu

3. Aggiungere l'account utente per al gruppo WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Risorse aggiuntive sulla sicurezza
 Per altre informazioni sui problemi di sicurezza, vedere gli argomenti seguenti.

### <a name="visual-studio-security"></a>sicurezza Visual Studio

- [Sicurezza e le autorizzazioni utente](http://go.microsoft.com/fwlink/?LinkId=177503)

- [Security in Native and codice .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)

- [Sicurezza in .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)

### <a name="sharepoint-security"></a>Sicurezza di SharePoint

- [Sicurezza e amministrazione di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177501)

- [Centro risorse di sicurezza di SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)

- [Protezione delle Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)

- [Miglioramento della sicurezza delle applicazioni Web: Minacce e contromisure](http://go.microsoft.com/fwlink/?LinkID=140080)

### <a name="general-security"></a>Sicurezza generale

- [MSDN Security Development Lifecycle](http://go.microsoft.com/fwlink/?LinkID=147149)

- [Creazione di applicazioni ASP.NET protette: L'autenticazione, autorizzazione e comunicazioni protette](http://go.microsoft.com/fwlink/?LinkId=177494)

## <a name="see-also"></a>Vedere anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)