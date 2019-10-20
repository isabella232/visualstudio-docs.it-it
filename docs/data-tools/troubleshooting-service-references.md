---
title: Risoluzione dei problemi relativi ai riferimenti al servizio
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 28ff14f10cd6ad5612551bb65b7b17f0280358f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639593"
---
# <a name="troubleshoot-service-references"></a>Risolvere i problemi relativi ai riferimenti al servizio

In questo argomento vengono elencati i problemi comuni che possono verificarsi quando si lavora con Windows Communication Foundation (WCF) o WCF Data Services riferimenti in Visual Studio.

## <a name="error-returning-data-from-a-service"></a>Errore durante la restituzione di dati da un servizio

Quando si restituisce un `DataSet` o `DataTable` da un servizio, è possibile che venga visualizzata un'eccezione "la quota di dimensioni massime per i messaggi in arrivo è stata superata". Per impostazione predefinita, la proprietà `MaxReceivedMessageSize` per alcune associazioni è impostata su un valore relativamente piccolo per limitare l'esposizione agli attacchi Denial of Service. È possibile aumentare questo valore per evitare l'eccezione. Per ulteriori informazioni, vedere <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Per correggere l'errore:

1. In **Esplora soluzioni**fare doppio clic sul file *app. config* per aprirlo.

2. Individuare la proprietà `MaxReceivedMessageSize` e impostarla su un valore più grande.

## <a name="cannot-find-a-service-in-my-solution"></a>Impossibile trovare un servizio nella soluzione

Quando si fa clic sul pulsante **individua** nella finestra di dialogo **Aggiungi riferimenti al servizio** , uno o più progetti della libreria di servizi WCF nella soluzione non vengono visualizzati nell'elenco dei servizi. Questo problema può verificarsi se una libreria di servizi è stata aggiunta alla soluzione, ma non è ancora stata compilata.

Per correggere l'errore:

- In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto libreria di servizi WCF e scegliere **Compila**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Errore durante l'accesso a un servizio su un desktop remoto

Quando un utente accede a un servizio WCF ospitato sul Web tramite una connessione Desktop remoto e l'utente non dispone di autorizzazioni amministrative, viene utilizzata l'autenticazione NTLM. Se l'utente non dispone di autorizzazioni amministrative, l'utente potrebbe ricevere il messaggio di errore seguente: "la richiesta HTTP non è autorizzata con lo schema di autenticazione client ' Anonymous '. L'intestazione di autenticazione ricevuta dal server è' NTLM ' ".

Per correggere l'errore:

1. Nel progetto sito Web, aprire le pagine delle **Proprietà** .

2. Nella scheda **Opzioni di avvio** deselezionare la casella di controllo **autenticazione NTLM** .

    > [!NOTE]
    > È consigliabile disattivare l'autenticazione NTLM solo per i siti Web che contengono esclusivamente servizi WCF. La protezione per i servizi WCF viene gestita tramite la configurazione nel file *Web. config* . Questa operazione rende superflua l'autenticazione NTLM.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>L'impostazione del livello di accesso per le classi generate non ha alcun effetto

L'impostazione dell'opzione **livello di accesso per le classi generate** nella finestra di dialogo **Configura riferimenti al servizio** su **interno** o su **Friend** potrebbe non funzionare sempre. Anche se l'opzione sembra essere impostata nella finestra di dialogo, le classi di supporto risultanti vengono generate con un livello di accesso di `Public`.

Si tratta di un limite noto di determinati tipi, ad esempio quelli serializzati utilizzando la <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Errore durante il debug del codice del servizio

Quando si esegue un'istruzione nel codice per un servizio WCF dal codice client, è possibile che venga visualizzato un errore relativo ai simboli mancanti. Questo problema può verificarsi quando un servizio che fa parte della soluzione è stato spostato o rimosso dalla soluzione.

Quando si aggiunge per la prima volta un riferimento a un servizio WCF che fa parte della soluzione corrente, viene aggiunta una dipendenza di compilazione esplicita tra il progetto del servizio e il progetto client del servizio. Ciò garantisce che il client acceda sempre ai file binari di servizio aggiornati, che è particolarmente importante per gli scenari di debug, ad esempio l'esecuzione di un codice client nel codice del servizio.

Se il progetto di servizio viene rimosso dalla soluzione, la dipendenza di compilazione esplicita viene invalidata. Visual Studio non è più in grado di garantire che il progetto di servizio venga ricompilato secondo necessità.

Per correggere l'errore, è necessario ricompilare manualmente il progetto di servizio:

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Nella finestra di dialogo **Opzioni** espandere **progetti e soluzioni**e quindi selezionare **generale**.

3. Verificare che la casella di controllo **Mostra configurazioni di compilazione avanzate** sia selezionata, quindi fare clic su **OK**.

4. Caricare il progetto del servizio WCF.

5. Nella finestra di dialogo **Configuration Manager** impostare la **configurazione della soluzione attiva** su **debug**. Per altre informazioni, vedere [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md).

6. In **Esplora soluzioni**selezionare il progetto del servizio WCF.

7. Scegliere **ricompila** dal menu **Compila** per ricompilare il progetto del servizio WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services non vengono visualizzati nel browser

Quando tenta di visualizzare una rappresentazione XML dei dati in una [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer può interpretare erroneamente i dati come feed RSS. Assicurarsi che l'opzione per visualizzare i feed RSS sia disabilitata.

Per correggere l'errore, disabilitare i feed RSS:

1. In Internet Explorer scegliere **Opzioni Internet** dal menu **Strumenti**.

2. Nella sezione **feed** della scheda **contenuto** fare clic su **Impostazioni**.

3. Nella finestra di dialogo **Impostazioni feed** deselezionare la casella di controllo **Attiva visualizzazione di lettura feed** , quindi fare clic su **OK**.

4. Scegliere **OK** per chiudere la finestra di dialogo **Opzioni Internet**.

## <a name="see-also"></a>Vedere anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)