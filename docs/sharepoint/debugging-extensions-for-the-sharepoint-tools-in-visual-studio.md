---
title: Estensioni di debug per gli strumenti di SharePoint in Visual Studio | Microsoft Docs
description: Estensioni di debug per gli strumenti di SharePoint in Visual Studio. Eseguire il debug delle estensioni degli strumenti di SharePoint nell'istanza sperimentale o nell'istanza normale di VS.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ad95ce8b4ab9567f22748453ae59c258f24aa86
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671220"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Estensioni di debug per gli strumenti di SharePoint in Visual Studio
  È possibile eseguire il debug delle estensioni degli strumenti di SharePoint nell'istanza sperimentale o nell'istanza normale di Visual Studio. Se è necessario risolvere i problemi relativi al comportamento di un'estensione, è anche possibile modificare i valori del registro di sistema in modo da visualizzare informazioni aggiuntive sull'errore e configurare la modalità di esecuzione dei comandi di SharePoint in Visual Studio.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Estensioni di debug nell'istanza sperimentale di Visual Studio
 Per salvaguardare l'ambiente di sviluppo di Visual Studio da danneggiamenti accidentali da parte di estensioni non testate, Visual Studio SDK fornisce un'istanza alternativa di Visual Studio, denominata *istanza sperimentale*, che è possibile usare per installare e testare le estensioni. Per sviluppare nuove estensioni, è possibile usare l'istanza normale di Visual Studio, ma eseguirne il debug e l'esecuzione nell'istanza sperimentale. Per ulteriori informazioni, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).

 Se si usa un progetto VSIX per distribuire l'estensione e il progetto VSIX è il progetto di avvio nella soluzione, Visual Studio installa ed esegue automaticamente l'estensione nell'istanza sperimentale quando si esegue il debug della soluzione. Il progetto di avvio è il progetto che viene avviato quando si esegue il debug di una soluzione che contiene più progetti. Per altre informazioni sull'uso di un progetto VSIX per distribuire l'estensione, vedere [distribuire estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Per esempi che illustrano come eseguire il debug di diversi tipi di estensioni nell'istanza sperimentale di Visual Studio, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [Procedura dettagliata: creare un passaggio di distribuzione personalizzato per i progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [Procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [Procedura dettagliata: chiamare il modello a oggetti del client di SharePoint in un'estensione Esplora server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Estensioni di debug nell'istanza normale di Visual Studio
 Se si vuole eseguire il debug del progetto di estensione nell'istanza normale di Visual Studio, installare prima l'estensione nell'istanza normale. Quindi, alleghi il debugger a un secondo processo di Visual Studio. Al termine, è possibile rimuovere l'estensione in modo che non venga più caricata nel computer di sviluppo.

#### <a name="to-install-the-extension"></a>Per installare l'estensione

1. Chiudere tutte le istanze di Visual Studio.

2. Nella cartella di output di compilazione per il progetto di estensione, aprire il file *VSIX* facendo doppio clic su di esso oppure aprendo il menu di scelta rapida e scegliendo **Apri**:

3. Nella finestra di dialogo del **programma di installazione dell'estensione di Visual Studio** scegliere l'edizione di Visual Studio in cui si vuole installare l'estensione, quindi scegliere il pulsante **Installa** .

     Visual Studio installa i file di estensione nella \\ *author name* \\ versione del *nome dell'estensione*%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions Author \\ *version*. Le ultime tre cartelle in questo percorso sono costruite dagli `Author` `Name` elementi, e `Version` nel file *Extension. vsixmanifest* per l'estensione.

4. Dopo che Visual Studio ha installato l'estensione, scegliere il pulsante **Chiudi** .

#### <a name="to-debug-the-extension"></a>Per eseguire il debug dell'estensione

1. Aprire Visual Studio con privilegi di amministratore e aprire il progetto di estensione. I passaggi seguenti fanno riferimento a questa istanza di Visual Studio come *prima istanza*.

2. Avviare un'altra istanza di Visual Studio con privilegi di amministratore. I passaggi seguenti fanno riferimento a questa istanza di Visual Studio come *seconda istanza*.

3. Passare alla prima istanza di Visual Studio.

4. Sulla barra dei menu scegliere **debug**, **Connetti a processo**.

5. Nell'elenco **processi disponibili** scegliere *devenv.exe*. Questa voce si riferisce alla seconda istanza di Visual Studio. si tratta dell'istanza in cui si vuole eseguire il debug dell'estensione di progetto.

6. Scegliere il pulsante **Connetti** .

     Visual Studio esegue il progetto di estensione in modalità di debug.

7. Passa alla seconda istanza di Visual Studio.

8. Creare un nuovo progetto SharePoint che carica l'estensione. Se, ad esempio, si esegue il debug di un'estensione per gli elementi del progetto di definizione elenco, creare un progetto di **definizione di elenco** .

9. Eseguire tutti i passaggi necessari per testare il codice di estensione.

10. Al termine del debug dell'estensione, chiudere la seconda istanza di Visual Studio.

#### <a name="to-remove-the-extension"></a>Per rimuovere l'estensione

1. Nella barra dei menu di Visual Studio scegliere **strumenti**, **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere il nome dell'estensione, quindi scegliere il pulsante **Disinstalla** .

3. Nella finestra di dialogo visualizzata scegliere il pulsante **Sì** per confermare che si vuole disinstallare l'estensione.

4. Scegliere il pulsante **Riavvia ora** per completare la disinstallazione.

## <a name="debug-sharepoint-commands"></a>Debug di comandi di SharePoint
 Se si desidera eseguire il debug di un comando di SharePoint che fa parte di un'estensione degli strumenti di SharePoint, è necessario alleghi il debugger al processo *vssphost4.exe* . Si tratta del processo host a 64 bit che esegue i comandi di SharePoint. Per ulteriori informazioni sui comandi di SharePoint e *vssphost4.exe*, vedere la pagina relativa [alla chiamata nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Per alleghi il debugger al processo di vssphost4.exe

1. Avviare il debug dell'estensione nell'istanza sperimentale di Visual Studio o nell'istanza normale di Visual Studio seguendo le istruzioni riportate sopra.

2. Nell'istanza di Visual Studio in cui si esegue il debugger, sulla barra dei menu scegliere **debug**, **Connetti a processo**.

3. Nell'elenco **processi disponibili** scegliere *vssphost.exe*.

    > [!NOTE]
    > Se vssphost.exe non è presente nell'elenco, è necessario avviare il processo di *vssphost4.exe* nell'istanza di Visual Studio in cui si esegue l'estensione. Questa operazione viene in genere eseguita eseguendo un'azione che consente a Visual Studio di connettersi al sito di SharePoint nel computer di sviluppo. Ad esempio, Visual Studio avvia *vssphost4.exe* quando si espande un nodo di connessione al sito (un nodo che visualizza un URL del sito) nel nodo **connessioni di SharePoint** nella finestra di **Esplora server** o quando si aggiungono determinati elementi del progetto SharePoint, ad esempio l' **istanza di elenco** o gli elementi del ricevitore di **eventi** , a un progetto SharePoint.

4. Scegliere il pulsante **Connetti** .

5. Nell'istanza di Visual Studio di cui è in corso il debug eseguire i passaggi necessari per eseguire il comando.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Modificare i valori del registro di sistema per facilitare il debug delle estensioni degli strumenti SharePoint
 Quando si esegue il debug di un'estensione degli strumenti di SharePoint in Visual Studio, è possibile modificare i valori nel registro di sistema per facilitare la risoluzione dei problemi relativi all'estensione. I valori sono presenti nella chiave **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** . Questi valori non sono disponibili per impostazione predefinita.

 Per facilitare la risoluzione dei problemi di qualsiasi estensione degli strumenti di SharePoint, è possibile creare e impostare il valore EnableDiagnostics. Nella tabella seguente viene descritto questo valore.

|Valore|Descrizione|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD che specifica se i messaggi di diagnostica vengono visualizzati nella finestra di **output** .<br /><br /> Per visualizzare i messaggi di diagnostica, impostare questo valore su 1. Per arrestare la visualizzazione dei messaggi, impostare questo valore su 0 o eliminare questo valore.<br /><br /> Per scrivere messaggi nella finestra di **output** da un'estensione degli strumenti di SharePoint, utilizzare il servizio di progetto SharePoint. Per ulteriori informazioni, vedere [utilizzare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|

 Se l'estensione include un comando di SharePoint, è possibile creare e impostare valori aggiuntivi che consentono di risolvere i problemi relativi al comando. Nella tabella seguente vengono descritti questi valori.

|Valore|Descrizione|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD che specifica se visualizzare una finestra di dialogo che consente di alleghiare il debugger a *vssphost4.exe* non appena viene avviato. Questa operazione è utile se il comando di cui si desidera eseguire il debug viene eseguito da vssphost.exe immediatamente dopo l'avvio e non è disponibile un tempo sufficiente per l'associazione manuale del debugger prima dell'esecuzione del comando. Per visualizzare la finestra di dialogo, *vssphost4.exe* chiama il <xref:System.Diagnostics.Debugger.Break%2A> metodo all'avvio.<br /><br /> Per abilitare questo comportamento, impostare questo valore su 1. Per disattivare questo comportamento, impostare questo valore su 0 o eliminare questo valore.<br /><br /> Se si imposta questo valore su 1, è anche possibile aumentare il valore di HostProcessStartupTimeout per concedere a se stessi un tempo sufficiente per l'associazione del debugger prima che Visual Studio preveda che *vssphost4.exe* segnali che è stato avviato correttamente.|
|ChannelOperationTimeout|REG_DWORD che specifica l'intervallo di tempo, in secondi, in cui Visual Studio è in attesa dell'esecuzione di un comando di SharePoint. Se il comando non viene eseguito nel tempo, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> viene generata un'eccezione.<br /><br /> Il valore predefinito è 120 secondi.|
|HostProcessStartupTimeout|REG_DWORD che specifica il tempo, in secondi, in cui Visual Studio attende che *vssphost4.exe* segnali che è stato avviato correttamente. Se *vssphost4.exe* non segnala un inizio nel tempo, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> viene generata un'eccezione.<br /><br /> Il valore predefinito è 60 secondi.|
|MaxReceivedMessageSize|REG_DWORD che specifica la dimensione massima consentita, in byte, dei messaggi WCF passati tra Visual Studio e *vssphost4.exe*.<br /><br /> Il valore predefinito è 1.048.576 byte (1 MB).|
|MaxStringContentLength|REG_DWORD che specifica la dimensione massima consentita, in byte, delle stringhe passate tra Visual Studio e *vssphost4.exe*.<br /><br /> Il valore predefinito è 1.048.576 byte (1 MB).|

## <a name="see-also"></a>Vedere anche

- [Estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Distribuire estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
