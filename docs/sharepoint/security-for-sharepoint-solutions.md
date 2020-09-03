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
ms.openlocfilehash: 6dc1449a40528670274ea5b275cca3f0a8d2f277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "73983786"
---
# <a name="security-for-sharepoint-solutions"></a>Sicurezza per le soluzioni SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incorpora le funzionalità seguenti per migliorare la sicurezza delle applicazioni SharePoint.

## <a name="safe-control-entries"></a>Voci di controllo sicure
 Ogni elemento del progetto SharePoint creato in [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] dispone di una proprietà di **voci di controllo sicura** che rappresenta una raccolta di controlli sicuri. La relativa sottoproprietà **Safe** consente di specificare i controlli considerati protetti. Per altre informazioni, vedere [fornire informazioni sul pacchetto e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [specificando Web part sicuri](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts).

## <a name="allowpartiallytrustedcallers-attribute"></a>attributo AllowPartiallyTrustedCallers
 Per impostazione predefinita, solo le applicazioni completamente attendibili dal sistema di sicurezza dall'accesso di codice di runtime possono accedere a un assembly di codice gestito condiviso. Il contrassegno di un assembly completamente attendibile con l'attributo AllowPartiallyTrustedCallers consente di accedere a assembly parzialmente attendibili.

 L'attributo AllowPartiallyTrustedCallers viene aggiunto a qualsiasi soluzione di SharePoint non distribuita nel Global Assembly Cache di sistema ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). Sono incluse soluzioni o soluzioni create mediante sandbox distribuite nella directory bin dell'applicazione SharePoint. Per ulteriori informazioni, vedere [la pagina relativa alle modifiche di sicurezza della versione 1 per il Framework Microsoft .NET e la](/previous-versions/msp-n-p/ff921345(v=pandp.10)) [distribuzione di Web part in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

## <a name="safe-against-script-property"></a>Proprietà di script sicura
 L'inserimento di *script* è l'inserimento di codice potenzialmente dannoso in controlli o pagine Web. Per proteggere i siti di SharePoint 2010 dall'inserimento di script, i collaboratori non possono visualizzare o modificare le web part o le relative proprietà per impostazione predefinita. Questo comportamento è controllato da un attributo SafeControl denominato SafeAgainstScript. In [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] impostare questo attributo nelle **voci di controllo sicure** della sottoproprietà di un elemento di progetto su **script**. Per altre informazioni, vedere [fornire informazioni sul pacchetto e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [procedura: contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Controllo account utente di Windows 7 e vista
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporano una funzionalità di sicurezza nota come controllo dell'account utente (UAC). Per sviluppare soluzioni SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nei [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] sistemi e, il controllo dell'account utente richiede l'esecuzione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come amministratore di sistema. Dal menu **Start** aprire il menu di scelta rapida per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , quindi scegliere **Esegui come amministratore**.

 Per configurare il tasto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di scelta rapida per l'esecuzione sempre come amministratore, aprire il menu di scelta rapida, scegliere **Proprietà**, fare clic sul pulsante **Avanzate** nella finestra di dialogo **Proprietà** , quindi selezionare la casella di controllo **Esegui come amministratore** .

 Per ulteriori informazioni, vedere informazioni [e configurazione del controllo dell'account utente in Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). e il [controllo dell'account utente di Windows 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10)).

## <a name="sharepoint-permissions-considerations"></a>Considerazioni sulle autorizzazioni di SharePoint
 Per sviluppare soluzioni SharePoint, è necessario disporre di autorizzazioni sufficienti per eseguire ed eseguire il debug di soluzioni SharePoint. Prima di poter testare una soluzione di SharePoint, attenersi alla procedura seguente per assicurarsi di disporre delle autorizzazioni necessarie:

1. Aggiungere l'account utente come amministratore nel sistema.

2. Aggiungere l'account utente come amministratore della farm per il server SharePoint.

    1. In Amministrazione centrale SharePoint 2010, scegliere il collegamento **Gestisci gruppo amministratori farm** .

    2. Nella pagina **Amministratori farm** scegliere l'opzione di menu **nuovo**

3. Aggiungere l'account utente al gruppo WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Risorse di sicurezza aggiuntive
 Per ulteriori informazioni sui problemi di sicurezza, vedere gli argomenti seguenti.

### <a name="visual-studio-security"></a>sicurezza Visual Studio

- [Sicurezza e autorizzazioni utente](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [Sicurezza nel codice nativo e nel codice .NET Framework](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [Sicurezza in .NET Framework](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>Sicurezza di SharePoint

- [Amministrazione e sicurezza di SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [Centro risorse di sicurezza di SharePoint](/sharepoint/dev/)

- [Protezione Web part in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [Miglioramento della sicurezza delle applicazioni Web: minacce e contromisure](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>Sicurezza generale

- [Ciclo di vita di sviluppo della sicurezza MSDN](https://www.microsoft.com/msrc?rtc=1)

- [Come compilare applicazioni ASP.NET protette: autenticazione, autorizzazione e comunicazioni protette (la pagina potrebbe essere in inglese)](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>Vedere anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)