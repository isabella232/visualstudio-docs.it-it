---
title: Debug delle estensioni per gli strumenti di SharePoint in Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f838363b52a85faff022f49542fcc2fcc7e450d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950816"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Eseguire il debug delle estensioni per gli strumenti di SharePoint in Visual Studio
  È possibile eseguire il debug di estensioni degli strumenti di SharePoint nell'istanza sperimentale o nell'istanza normale di Visual Studio. Se è necessario risolvere i problemi il comportamento di un'estensione, è inoltre possibile modificare i valori del Registro di sistema per visualizzare informazioni aggiuntive sull'errore e per configurare la modalità di esecuzione dei comandi di SharePoint in Visual Studio.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Eseguire il debug delle estensioni nell'istanza sperimentale di Visual Studio
 Per proteggere l'ambiente di sviluppo di Visual Studio dal danneggiamento accidentale da estensioni non testate, Visual Studio SDK fornisce un'istanza alternativa di Visual Studio, denominata la *istanza sperimentale*, che è possibile usare installare e testare le estensioni. Per sviluppare nuove estensioni usando l'istanza di Visual Studio regolare, ma è eseguire il debug ed eseguirli nell'istanza sperimentale. Per altre informazioni, vedere [il processo dell'istanza sperimentale](../extensibility/the-experimental-instance.md).

 Se si usa un progetto VSIX per la distribuzione dell'estensione e il progetto VSIX sia il progetto di avvio nella soluzione, Visual Studio automaticamente Installa ed esegue l'estensione nell'istanza sperimentale, quando si esegue il debug della soluzione. Il progetto di avvio è il progetto che viene avviato quando si esegue il debug di una soluzione che contiene più progetti. Per altre informazioni sull'uso di un progetto VSIX per la distribuzione dell'estensione, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Per esempi che illustrano come eseguire il debug di diversi tipi di estensioni nell'istanza sperimentale di Visual Studio, vedere le procedure dettagliate seguenti:

-   [Procedura dettagliata: Estendere un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

-   [Procedura dettagliata: Crea elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

-   [Procedura dettagliata: Creare un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

-   [Procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

-   [Procedura dettagliata: Chiamare il modello a oggetti client SharePoint in un'estensione di Esplora Server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Eseguire il debug delle estensioni nell'istanza di regolare di Visual Studio
 Se si desidera eseguire il debug del progetto di estensione nell'istanza di regolare di Visual Studio, prima di tutto installare l'estensione nell'istanza di regolare. Quindi, collegare il debugger a un secondo processo di Visual Studio. Dopo aver completato, è possibile rimuovere l'estensione in modo che venga non caricato non è più nel computer di sviluppo.

#### <a name="to-install-the-extension"></a>Per installare l'estensione

1.  Chiudere tutte le istanze di Visual Studio.

2.  Nella cartella di output di compilazione per il progetto di estensione, aprire il *VSIX* file facendovi doppio clic oppure aprendo il relativo menu di scelta rapida e scegliendo **aprire**:

3.  Nel **Visual Studio Extension Installer** finestra di dialogo, scegliere l'edizione di Visual Studio a cui si desidera installare l'estensione e quindi scegliere il **installare** pulsante.

     Visual Studio installa i file di estensione per %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*il nome dell'autore*\\*nome estensione* \\ *versione*. Le ultime tre cartelle in questo percorso vengono costruite dal `Author`, `Name`, e `Version` elementi nel *Extension. vsixmanifest* file per l'estensione.

4.  Dopo che Visual Studio installa l'estensione, scegliere il **Chiudi** pulsante.

#### <a name="to-debug-the-extension"></a>Per eseguire il debug dell'estensione

1.  Avviare Visual Studio con privilegi di amministratore e aprire il progetto di estensione. I passaggi seguenti fanno riferimento a questa istanza di Visual Studio come le *prima di istanze*.

2.  Avviare un'altra istanza di Visual Studio con privilegi di amministratore. I passaggi seguenti fanno riferimento a questa istanza di Visual Studio come le *seconda istanza*.

3.  Passare alla prima istanza di Visual Studio.

4.  Nella barra dei menu, scegliere **Debug**, **Connetti a processo**.

5.  Nel **processi disponibili** casella di riepilogo *devenv.exe*. Si riferisce questa voce per la seconda istanza di Visual Studio. si tratta dell'istanza che si desidera eseguire il debug dell'estensione di progetto in.

6.  Scegliere il **Attach** pulsante.

     Visual Studio esegue il progetto di estensione in modalità di debug.

7.  Passare alla seconda istanza di Visual Studio.

8.  Creare un nuovo progetto di SharePoint che consente di caricare l'estensione. Ad esempio, se si esegue il debug di un'estensione per gli elementi di progetto di definizione di elenco, creare un **definizione di elenco** progetto.

9. Eseguire tutti i passaggi necessari per testare il codice dell'estensione.

10. Quando si è terminato il debug dell'estensione, chiudere la seconda istanza di Visual Studio.

#### <a name="to-remove-the-extension"></a>Per rimuovere l'estensione

1.  In Visual Studio, sulla barra dei menu, scegliere **degli strumenti**, **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2.  Nell'elenco delle estensioni, scegliere il nome dell'estensione e quindi scegliere il **Disinstalla** pulsante.

3.  Nella finestra di dialogo visualizzata, scegliere il **Sì** per confermare che si desidera disinstallare l'estensione.

4.  Scegliere il **Riavvia ora** pulsante per completare la disinstallazione.

## <a name="debug-sharepoint-commands"></a>Eseguire il debug dei comandi di SharePoint
 Se si desidera eseguire il debug di un comando di SharePoint che fa parte di un'estensione degli strumenti di SharePoint, è necessario collegare il debugger per il *vssphost4.exe* processo. Questo è il processo host a 64 bit che esegue i comandi di SharePoint. Per altre informazioni sui comandi di SharePoint e *vssphost4.exe*, vedere [chiamare i modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Per collegare il debugger al processo di vssphost4.exe

1.  Avviare il debug dell'estensione nell'istanza sperimentale di Visual Studio o l'istanza normale di Visual Studio seguendo le istruzioni riportate sopra.

2.  Nell'istanza di Visual Studio in cui in esecuzione il debugger, nella barra dei menu, scegliere **Debug**, **Connetti a processo**.

3.  Nel **processi disponibili** casella di riepilogo *vssphost.exe*.

    > [!NOTE]
    >  Se vssphost.exe non viene visualizzato nell'elenco, è necessario avviare il *vssphost4.exe* processi nell'istanza di Visual Studio in cui si esegue l'estensione. In genere, è possibile eseguire un'azione che fa in modo che Visual Studio per connettersi al sito di SharePoint nel computer di sviluppo. Ad esempio, Visual Studio avvia *vssphost4.exe* quando si espande un nodo di connessione del sito (un nodo viene visualizzato un URL del sito) sotto il **connessioni di SharePoint** nodo nel **Esplora Server**  finestra, o quando si aggiungono alcuni elementi di progetto SharePoint, ad esempio **List Instance** oppure **ricevitore di eventi** elementi, a un progetto SharePoint.

4.  Scegliere il **Attach** pulsante.

5.  Nell'istanza di Visual Studio in fase di debug, eseguire i passaggi necessari per eseguire il comando.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Modificare i valori del Registro di sistema per eseguire il debug delle estensioni di strumenti di SharePoint
 Quando si esegue il debug di un'estensione degli strumenti di SharePoint in Visual Studio, è possibile modificare i valori del Registro di sistema per risolvere i problemi dell'estensione. I valori esistenti con il **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** chiave. Questi valori non sono presenti per impostazione predefinita.

 Per risolvere qualsiasi estensione degli strumenti di SharePoint, è possibile creare e impostare il valore di EnableDiagnostics. La tabella seguente descrive questo valore.

|Valore|Descrizione|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD che specifica se i messaggi di diagnostica vengono visualizzati nei **Output** finestra.<br /><br /> Per visualizzare messaggi di diagnostica, impostare questo valore su 1. Per interrompere la visualizzazione dei messaggi, impostare questo valore su 0 o eliminare questo valore.<br /><br /> Per scrivere messaggi di **Output** estensione degli strumenti finestra di SharePoint, usare il servizio di progetto SharePoint. Per altre informazioni, vedere [usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|

 Se l'estensione include un comando di SharePoint, è possibile creare e impostare valori aggiuntivi per consentire di risolvere il comando. Nella tabella seguente vengono descritti questi valori.

|Value|Descrizione|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD che specifica se visualizzare una finestra di dialogo che consente di connettere il debugger *vssphost4.exe* , non appena viene avviato. Ciò è utile se il comando che si desidera eseguire il debug viene eseguito da vssphost.exe immediatamente dopo l'avvio e non esiste un tempo sufficiente per collegare manualmente il debugger prima dell'esecuzione del comando. Per visualizzare la finestra di dialogo *vssphost4.exe* chiama il <xref:System.Diagnostics.Debugger.Break%2A> metodo all'avvio.<br /><br /> Per abilitare questo comportamento, impostare questo valore su 1. Per disattivare questo comportamento, impostare questo valore su 0 o eliminare questo valore.<br /><br /> Se si imposta questo valore su 1, è anche possibile aumentare il valore HostProcessStartupTimeout per consentire un tempo sufficiente per collegare il debugger prima di Visual Studio si presuppone *vssphost4.exe* per segnalare che è stato avviato correttamente.|
|ChannelOperationTimeout|REG_DWORD che specifica il tempo, in secondi, da Visual Studio eseguire un comando di SharePoint. Se il comando non viene eseguito nel tempo, un <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> viene generata un'eccezione.<br /><br /> Il valore predefinito è 120 secondi.|
|HostProcessStartupTimeout|REG_DWORD che specifica il tempo, espresso in secondi, da Visual Studio attende *vssphost4.exe* per segnalare che è stato avviato correttamente. Se *vssphost4.exe* non segnala un avvio riuscito nel tempo, un <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> viene generata un'eccezione.<br /><br /> Il valore predefinito è 60 secondi.|
|MaxReceivedMessageSize|REG_DWORD che specifica la dimensione massima consentita, in byte, dei messaggi WCF che vengono passati tra Visual Studio e *vssphost4.exe*.<br /><br /> Il valore predefinito è 1.048.576 byte (1 MB).|
|MaxStringContentLength|REG_DWORD che specifica la dimensione massima consentita, in byte, di stringhe che vengono passate tra Visual Studio e *vssphost4.exe*.<br /><br /> Il valore predefinito è 1.048.576 byte (1 MB).|

## <a name="see-also"></a>Vedere anche

- [Estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Distribuire le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
