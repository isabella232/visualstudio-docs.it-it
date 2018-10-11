---
title: I riferimenti al servizio di risoluzione dei problemi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 696c6f2a0e738d965b5992e3df52a77831ab27a0
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880890"
---
# <a name="troubleshooting-service-references"></a>Risoluzione dei problemi relativi ai riferimenti al servizio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [riferimenti al servizio di risoluzione dei problemi](https://docs.microsoft.com/visualstudio/data-tools/troubleshooting-service-references).

Questo argomento elenca i problemi comuni che possono verificarsi quando si sta lavorando [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] oppure [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] fa riferimento [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="error-returning-data-from-a-service"></a>Errore durante la restituzione dei dati da un servizio
 Quando si restituisce un `DataSet` o `DataTable` da un servizio, è possibile ricevere un'eccezione "è stata superata la quota delle dimensioni massime dei messaggi in ingresso". Per impostazione predefinita, il `MaxReceivedMessageSize` proprietà per alcune associazioni è impostata su un valore relativamente basso limita l'esposizione agli attacchi denial of service. È possibile aumentare questo valore per evitare l'eccezione.

 Per correggere l'errore:

1.  Nelle **Esplora soluzioni**, doppio clic sul file app. config per aprirlo.

2.  Individuare il `MaxReceivedMessageSize` proprietà e modificarlo in un valore maggiore.

## <a name="cannot-find-a-service-in-my-solution"></a>Impossibile trovare un servizio nella soluzione
 Quando si fa clic il **Discover** pulsante il **aggiungere riferimenti al servizio** nella finestra di dialogo uno o più progetti di libreria di servizi WCF nella soluzione non vengono visualizzati nell'elenco dei servizi. Ciò può verificarsi se una libreria di servizi è stato aggiunto alla soluzione ma non è ancora stata compilata.

 Per correggere l'errore:

-   Nelle **Esplora soluzioni**, fare clic sul progetto libreria di servizi WCF e fare clic su **compilazione**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Errore di accesso a un servizio su un Desktop remoto
 Quando un utente accede a un servizio WCF ospitato sul Web tramite una connessione desktop remoto e l'utente non dispone di autorizzazioni amministrative, viene utilizzata l'autenticazione NTLM. Se l'utente non ha le autorizzazioni amministrative, l'utente potrebbe ricevere il messaggio di errore seguente: "la richiesta HTTP non è autorizzata con lo schema di autenticazione client 'Anonimo'. L'intestazione di autenticazione ricevuta dal server: 'NTLM'."

 Per correggere l'errore:

1.  Nel progetto sito Web, aprire il **proprietà** pagine.

2.  Nel **opzioni di avvio** scheda, deseleziona le **autenticazione NTLM** casella di controllo.

    > [!NOTE]
    > Sarà necessario disattivare l'autenticazione NTLM solo per i siti Web che contengono esclusivamente servizi WCF. Sicurezza per i servizi WCF è gestita tramite la configurazione nel file Web. config. In questo modo l'autenticazione NTLM non necessari.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Livello di accesso per classi generate impostazione non ha alcun effetto
 Impostando il **livello di accesso per classi generate** opzione il **riferimenti al servizio di configurare** finestra di dialogo **interno** o **Friend** potrebbe non funzionare. Anche se viene visualizzata l'opzione da impostare nella finestra di dialogo, le classi di supporto risultante verranno generate con un livello di accesso di `Public`.

 Si tratta di una limitazione nota di determinati tipi, ad esempio quelli serializzato mediante il <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Codice di errore debug del servizio
 Quando si esegue il codice per un servizio WCF dal codice client e si verifichi un errore correlato ai simboli mancanti. Ciò può verificarsi quando un servizio che faceva parte della soluzione è stato spostato o rimosso dalla soluzione.

 Quando si aggiunge un riferimento a un servizio WCF che fa parte della soluzione corrente, viene aggiunto una dipendenza di compilazione esplicita tra il progetto di servizio e il progetto di client del servizio. In questo modo si garantisce che il client accede sempre i file binari del servizio aggiornati, che è particolarmente importante per gli scenari, ad esempio l'esecuzione di istruzioni dal codice client nel codice del servizio di debug.

 Se il progetto di servizio viene rimosso dalla soluzione, viene invalidata questa dipendenza di compilazione esplicita. Visual Studio non può più garantire che il progetto di servizio viene ricompilato base alle esigenze.

 Per correggere questo errore, è necessario ricompilare manualmente il progetto di servizio:

1.  Scegliere **Opzioni** dal menu **Strumenti**.

2.  Nel **le opzioni** finestra di dialogo espandere **progetti e soluzioni**e quindi selezionare **generali**.

3.  Assicurarsi che il **advanced Mostra configurazioni della build** casella di controllo sia selezionata e quindi fare clic su **OK**.

4.  Caricare il progetto di servizio WCF. Per altre informazioni, vedere [NIB procedura: creare soluzioni multiprogetto](http://msdn.microsoft.com/en-us/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).

5.  Nel **Configuration Manager** finestra di dialogo, impostare il **configurazione soluzione attiva** a **Debug**. Per altre informazioni, vedere [How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md) (Procedura: Creare e modificare le configurazioni).

6.  Nelle **Esplora soluzioni**, selezionare il progetto di servizio WCF.

7.  Nel **compilare** menu, fare clic su **ricompilare** per ricompilare il progetto di servizio WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services non vengono visualizzati in Browser
 Quando prova a visualizzare una rappresentazione XML dei dati in un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], Internet Explorer che potrebbero essere erroneamente i dati come un feed RSS. È necessario assicurarsi che l'opzione per visualizzare feed RSS sia disabilitata.

 Per correggere questo errore, disabilitare il feed RSS:

1.  In Internet Explorer sul **degli strumenti** menu, fare clic su **Opzioni Internet**.

2.  Nel **contenuti** nella scheda il **feed** fare clic su **impostazioni**.

3.  Nel **impostazioni Feed** della finestra di dialogo deseleziona le **attivare la visualizzazione di lettura feed** casella di controllo e quindi fare clic su **OK**.

4.  Fare clic su **OK** per chiudere la **Opzioni Internet** nella finestra di dialogo.

## <a name="see-also"></a>Vedere anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)