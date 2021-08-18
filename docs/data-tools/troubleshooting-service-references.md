---
title: Risoluzione dei problemi relativi ai riferimenti al servizio
description: Esaminare i problemi comuni che possono verificarsi quando si lavora con Windows Communication Foundation (WCF) o WCF Data Services riferimenti in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 649204a074980c547fc238ba0c7db923c7ff199b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031601"
---
# <a name="troubleshoot-service-references"></a>Risolvere i problemi relativi ai riferimenti al servizio

In questo argomento vengono elencati i problemi comuni che possono verificarsi quando si lavora con Windows Communication Foundation (WCF) o WCF Data Services riferimenti in Visual Studio.

## <a name="error-returning-data-from-a-service"></a>Errore durante la restituzione di dati da un servizio

Quando si restituisce un oggetto o da un servizio, è possibile che venga visualizzata l'eccezione "È stata superata la quota di dimensioni massime per i messaggi `DataSet` `DataTable` in arrivo". Per impostazione predefinita, la proprietà per alcune associazioni è impostata su un valore relativamente piccolo per limitare l'esposizione `MaxReceivedMessageSize` ad attacchi Denial of Service. È possibile aumentare questo valore per impedire l'eccezione. Per altre informazioni, vedere <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Per correggere l'errore: 

1. In **Esplora soluzioni** fare doppio clic sul file *app.config* per aprirlo.

2. Individuare la `MaxReceivedMessageSize` proprietà e impostarla su un valore più grande.

## <a name="cannot-find-a-service-in-my-solution"></a>Impossibile trovare un servizio nella soluzione

Quando si fa clic  **sul pulsante** Individua nella finestra di dialogo Aggiungi riferimenti al servizio, uno o più progetti wcf service library nella soluzione non vengono visualizzati nell'elenco dei servizi. Ciò può verificarsi se una libreria del servizio è stata aggiunta alla soluzione ma non è ancora stata compilata.

Per correggere l'errore: 

- In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto libreria di servizi WCF e scegliere **Compila.**

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Errore durante l'accesso a un servizio tramite desktop remoto

Quando un utente accede a un servizio WCF ospitato sul Web tramite una connessione Desktop remoto e l'utente non dispone di autorizzazioni amministrative, viene utilizzata l'autenticazione NTLM. Se l'utente non dispone di autorizzazioni amministrative, è possibile che venga visualizzato il messaggio di errore seguente: "La richiesta HTTP non è autorizzata con lo schema di autenticazione client "Anonimo". L'intestazione di autenticazione ricevuta dal server è "NTLM".

Per correggere l'errore: 

1. Nel progetto del sito Web aprire le **pagine** Proprietà.

2. Nella scheda **Opzioni di** avvio deselezionare la casella di controllo Autenticazione **NTLM** .

    > [!NOTE]
    > È consigliabile disattivare l'autenticazione NTLM solo per i siti Web che contengono esclusivamente servizi WCF. La sicurezza per i servizi WCF viene gestita tramite la configurazione nel file *web.config.* In questo modo l'autenticazione NTLM non è necessaria.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>L'impostazione del livello di accesso per le classi generate non ha alcun effetto

**L'impostazione dell'opzione Livello** di accesso per le classi generate nella finestra **di** dialogo Configura riferimenti al servizio su **Interno** o **Friend** potrebbe non funzionare sempre. Anche se l'opzione sembra essere impostata nella finestra di dialogo, le classi di supporto risultanti vengono generate con un livello di accesso di `Public` .

Si tratta di una limitazione nota di determinati tipi, ad esempio quelli serializzati tramite <xref:System.Xml.Serialization.XmlSerializer> .

## <a name="error-debugging-service-code"></a>Codice del servizio di debug degli errori

Quando si esegue un'istruzione nel codice per un servizio WCF dal codice client, è possibile che venga visualizzato un errore relativo ai simboli mancanti. Ciò può verificarsi quando un servizio che fa parte della soluzione è stato spostato o rimosso dalla soluzione.

Quando si aggiunge per la prima volta un riferimento a un servizio WCF che fa parte della soluzione corrente, viene aggiunta una dipendenza di compilazione esplicita tra il progetto del servizio e il progetto client del servizio. Ciò garantisce che il client accedono sempre ai file binari del servizio aggiornati, aspetto particolarmente importante per gli scenari di debug, ad esempio l'esecuzione di istruzioni dal codice client al codice del servizio.

Se il progetto del servizio viene rimosso dalla soluzione, questa dipendenza di compilazione esplicita viene invalidata. Visual Studio non può più garantire che il progetto di servizio sia ricompilato in base alle esigenze.

Per correggere l'errore, è necessario ricompilare manualmente il progetto di servizio:

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Nella finestra **di** dialogo Opzioni espandere **Progetti e soluzioni** e quindi selezionare **Generale.**

3. Assicurarsi che la casella **di controllo Mostra configurazioni build avanzate** sia selezionata e quindi fare clic su **OK.**

4. Caricare il progetto di servizio WCF.

5. Nella finestra **Gestione configurazione** finestra di dialogo, impostare **Configurazione soluzione attiva** su **Debug**. Per altre informazioni, vedere [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md).

6. Nella **Esplora soluzioni** selezionare il progetto di servizio WCF.

7. Scegliere **Ricompila** dal menu Compila **per** ricompilare il progetto di servizio WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services non vengono visualizzati nel browser

Quando tenta di visualizzare una rappresentazione XML dei dati in un oggetto , è Internet Explorer i dati potrebbero essere interpretati erroneamente [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] come feed RSS. Assicurarsi che l'opzione per visualizzare i feed RSS sia disabilitata.

Per correggere l'errore, disabilitare i feed RSS:

1. In Internet Explorer scegliere **Opzioni Internet** dal menu **Strumenti**.

2. Nella **sezione** Feed della scheda Contenuto **fare** clic su **Impostazioni**.

3. Nella finestra **di dialogo Impostazioni** feed deselezionare la casella di controllo Attiva visualizzazione lettura **feed** e quindi fare clic su **OK.**

4. Fare **clic su OK** per chiudere la finestra di **dialogo** Opzioni Internet .

## <a name="see-also"></a>Vedi anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
