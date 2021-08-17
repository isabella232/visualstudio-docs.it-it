---
title: Debug di estensioni per SharePoint tools in Visual Studio | Microsoft Docs
description: Eseguire il debug delle estensioni SharePoint strumenti in Visual Studio. Eseguire il SharePoint delle estensioni degli strumenti nell'istanza sperimentale o nell'istanza normale di Visual Studio.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 11cfbc1386ccd7994e2594f8ddde4a1add3613d27c0fcf1782a3d9dd2a1ed13a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121353046"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Eseguire il debug delle estensioni per SharePoint strumenti in Visual Studio
  È possibile eseguire il debug SharePoint estensioni degli strumenti nell'istanza sperimentale o nell'istanza normale di Visual Studio. Se è necessario risolvere i problemi relativi al comportamento di un'estensione, è anche possibile modificare i valori del Registro di sistema per visualizzare informazioni aggiuntive sugli errori e per configurare la modalità Visual Studio esecuzione SharePoint comandi.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Eseguire il debug delle estensioni nell'istanza sperimentale di Visual Studio
 Per proteggere l'ambiente di sviluppo Visual Studio da danneggiamento accidentale da estensioni non testate, Visual Studio SDK fornisce un'istanza di Visual Studio alternativa, denominata istanza sperimentale *,* che è possibile usare per installare e testare le estensioni. Si sviluppano nuove estensioni usando l'istanza regolare di Visual Studio, ma si esegue il debug e l'esecuzione nell'istanza sperimentale. Per altre informazioni, vedere [Istanza sperimentale.](../extensibility/the-experimental-instance.md)

 Se si usa un progetto VSIX per distribuire l'estensione e il progetto VSIX è il progetto di avvio nella soluzione, Visual Studio installa ed esegue automaticamente l'estensione nell'istanza sperimentale quando si esegue il debug della soluzione. Il progetto di avvio è il progetto che viene avviato quando si esegue il debug di una soluzione che contiene più progetti. Per altre informazioni sull'uso di un progetto VSIX per distribuire l'estensione, vedere Deploy [extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Per esempi che illustrano come eseguire il debug di vari tipi di estensioni nell'istanza sperimentale di Visual Studio, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: Estendere un tipo SharePoint di elemento di progetto](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [Procedura dettagliata: Creare un passaggio di distribuzione personalizzato per SharePoint progetti](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [Procedura dettagliata: Estendere Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [Procedura dettagliata: Chiamare nel modello SharePoint a oggetti client in un'Esplora server predefinita](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Eseguire il debug delle estensioni nell'istanza regolare di Visual Studio
 Se si vuole eseguire il debug del progetto di estensione nell'istanza regolare di Visual Studio, installare prima l'estensione nell'istanza normale. Collegare quindi il debugger a un secondo Visual Studio processo. Al termine, è possibile rimuovere l'estensione in modo che non sia più caricata nel computer di sviluppo.

#### <a name="to-install-the-extension"></a>Per installare l'estensione

1. Chiudere tutte le istanze di Visual Studio.

2. Nella cartella dell'output di compilazione per il progetto di estensione aprire il file con estensione *vsix* facendo doppio clic su di esso o aprendo il relativo menu di scelta rapida e quindi **scegliendo Apri:**

3. Nella finestra **Visual Studio programma** di installazione dell'estensione scegliere l'edizione di Visual Studio in cui si vuole installare l'estensione e quindi scegliere **il pulsante** Installa.

     Visual Studio i file di estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions versione del nome dell'estensione del nome \\  \\  \\ *dell'autore.* Le ultime tre cartelle in questo percorso vengono costruite dagli elementi , e nel `Author` `Name` file `Version` *extension.vsixmanifest* per l'estensione.

4. Dopo Visual Studio l'estensione, scegliere il **pulsante** Chiudi.

#### <a name="to-debug-the-extension"></a>Per eseguire il debug dell'estensione

1. Aprire Visual Studio con privilegi di amministratore e aprire il progetto di estensione. I passaggi seguenti fanno riferimento a questa istanza di Visual Studio come *prima istanza di*.

2. Avviare un'altra istanza Visual Studio con privilegi di amministratore. I passaggi seguenti fanno riferimento a questa istanza di Visual Studio come *seconda istanza* di .

3. Passare alla prima istanza di Visual Studio.

4. Sulla barra dei menu scegliere **Debug**, **Collega a processo**.

5. **Nell'elenco Processi disponibili** scegliere *devenv.exe*. Questa voce fa riferimento alla seconda istanza di Visual Studio; si tratta dell'istanza in cui si vuole eseguire il debug dell'estensione di progetto.

6. Scegliere il **pulsante Allega.**

     Visual Studio esegue il progetto di estensione in modalità di debug.

7. Passare alla seconda istanza di Visual Studio.

8. Creare un nuovo progetto SharePoint che carica l'estensione. Ad esempio, se si esegue il debug di un'estensione per gli elementi di progetto di definizione dell'elenco, creare un **progetto Definizione** elenco.

9. Eseguire i passaggi necessari per testare il codice dell'estensione.

10. Al termine del debug dell'estensione, chiudere la seconda istanza di Visual Studio.

#### <a name="to-remove-the-extension"></a>Per rimuovere l'estensione

1. Nella Visual Studio menu scegliere Strumenti **,** Estensioni e **aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere il nome dell'estensione e quindi scegliere il **pulsante Disinstalla.**

3. Nella finestra di dialogo visualizzata scegliere il **pulsante Sì** per confermare che si vuole disinstallare l'estensione.

4. Scegliere il **pulsante Riavvia** ora per completare la disinstallazione.

## <a name="debug-sharepoint-commands"></a>Eseguire il debug SharePoint comandi
 Se si desidera eseguire il debug di un comando SharePoint che fa parte di un'estensione degli strumenti di SharePoint, è necessario collegare il debugger al *vssphost4.exe* processo. Si tratta del processo host a 64 bit che esegue SharePoint comandi. Per altre informazioni sui comandi SharePoint e *vssphost4.exe*, vedere [Chiamare i modelli SharePoint a oggetti.](../sharepoint/calling-into-the-sharepoint-object-models.md)

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Per collegare il debugger al processo vssphost4.exe corrente

1. Avviare il debug dell'estensione nell'istanza sperimentale di Visual Studio o nell'istanza normale di Visual Studio seguendo le istruzioni precedenti.

2. Nell'istanza Visual Studio in cui si esegue il debugger, nella barra dei menu scegliere **Debug**, **Associa a processo**.

3. **Nell'elenco Processi disponibili** scegliere *vssphost.exe*.

    > [!NOTE]
    > Se vssphost.exe non viene visualizzato nell'elenco, è necessario avviare il processo *vssphost4.exe* nell'istanza di Visual Studio in cui si esegue l'estensione. In genere, questa operazione viene eseguita eseguendo un'azione che Visual Studio connettersi al sito SharePoint nel computer di sviluppo. Ad esempio, Visual Studio  avvia *vssphost4.exe* quando si espande un nodo di connessione del sito (un nodo che visualizza un URL del sito) nel nodo Connessioni **SharePoint** nella finestra  **di Esplora server** o quando si aggiungono determinati elementi del progetto SharePoint, ad esempio elementi istanza elenco o ricevitore di eventi, a un progetto SharePoint.

4. Scegliere il **pulsante Allega.**

5. Nell'istanza di Visual Studio di cui è in corso il debug, eseguire i passaggi necessari per eseguire il comando.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Modificare i valori del Registro di sistema per facilitare il debug SharePoint estensioni degli strumenti
 Quando si esegue il debug di un'estensione degli strumenti SharePoint in Visual Studio, è possibile modificare i valori nel Registro di sistema per risolvere i problemi dell'estensione. I valori sono presenti sotto **laHKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** chiave. Questi valori non esistono per impostazione predefinita.

 Per risolvere i problemi relativi a qualsiasi estensione SharePoint, è possibile creare e impostare il valore EnableDiagnostics. Nella tabella seguente viene descritto questo valore.

|Valore|Descrizione|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD che specifica se i messaggi di diagnostica vengono visualizzati nella finestra **Output.**<br /><br /> Per visualizzare i messaggi di diagnostica, impostare questo valore su 1. Per interrompere la visualizzazione dei messaggi, impostare questo valore su 0 o eliminare questo valore.<br /><br /> Per scrivere messaggi nella finestra **Output** da un'estensione degli strumenti SharePoint, usare il SharePoint servizio di progetto. Per altre informazioni, vedere [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md).|

 Se l'estensione include un SharePoint, è possibile creare e impostare valori aggiuntivi per risolvere i problemi del comando. Nella tabella seguente vengono descritti questi valori.

|Valore|Descrizione|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD specifica se visualizzare una finestra di dialogo che consente di collegare il debuggervssphost4.exe *non* appena viene avviato. Ciò è utile se il comando di cui si vuole eseguire il debug viene eseguito da vssphost.exe immediatamente dopo l'avvio e non è disponibile tempo sufficiente per collegare manualmente il debugger prima dell'esecuzione del comando. Per visualizzare la finestra di dialogo, *vssphost4.exe* chiama <xref:System.Diagnostics.Debugger.Break%2A> il metodo all'avvio.<br /><br /> Per abilitare questo comportamento, impostare questo valore su 1. Per disattivare questo comportamento, impostare questo valore su 0 o eliminare questo valore.<br /><br /> Se si imposta questo valore su 1, è anche possibile aumentare il valore hostProcessStartupTimeout per concedere tempo sufficiente per collegare il debugger prima che Visual Studio si aspetti che *vssphost4.exe* segnali che è stato avviato correttamente.|
|ChannelOperationTimeout|REG_DWORD che specifica il tempo, in secondi, di attesa Visual Studio un comando SharePoint esecuzione. Se il comando non viene eseguito in tempo, viene <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> generata un'eccezione .<br /><br /> Il valore predefinito è 120 secondi.|
|HostProcessStartupTimeout|REG_DWORD che specifica il tempo, in secondi, di attesa  Visual Studio attesavssphost4.exeper segnalare che è stato avviato correttamente. Se *vssphost4.exe* non segnala un avvio corretto nel tempo, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> viene generata un'eccezione .<br /><br /> Il valore predefinito è 60 secondi.|
|MaxReceivedMessageSize|REG_DWORD che specifica la dimensione massima consentita, in byte, dei messaggi WCF passati tra Visual Studio e *vssphost4.exe*.<br /><br /> Il valore predefinito è 1.048.576 byte (1 MB).|
|MaxStringContentLength|REG_DWORD che specifica le dimensioni massime consentite, in byte, delle stringhe passate tra Visual Studio e *vssphost4.exe*.<br /><br /> Il valore predefinito è 1.048.576 byte (1 MB).|

## <a name="see-also"></a>Vedi anche

- [Estendere gli SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Distribuire estensioni per gli strumenti SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
