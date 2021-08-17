---
title: Eseguire il debug Office progetti
description: Informazioni su come eseguire il debug Office progetti usando gli stessi strumenti Microsoft Visual Studio che si usano per altri Visual Studio progetto.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7289ade83f72d68d940aad979a1590b3740e1849
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026512"
---
# <a name="debug-office-projects"></a>Eseguire il debug Office progetti
  È possibile eseguire il debug di progetti di Office usando gli stessi strumenti di Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] che si usano per altri progetti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Le funzionalità del debugger, ad esempio la possibilità  di inserire punti di interruzione e visualizzare le variabili nella finestra Variabili locali, sono disponibili anche quando si esegue il debug Office progetti. Per altre informazioni sugli [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] strumenti di debug, vedere [Debug in Visual Studio](../debugger/debugger-feature-tour.md).

> [!TIP]
> Per semplificare il debug, chiudere tutte le istanze dell'applicazione di Office aperte, prima di generare ed eseguire il debug.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="start-and-stop-the-debugger"></a>Avviare e arrestare il debugger
 È possibile avviare il debug di Office progetto proprio come si avvia il debug di altri progetti. Ad esempio, è [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] possibile premere **F5.** Quando si avvia il debug di un progetto di componente aggiuntivo VSTO, viene avviato un nuovo processo per l'applicazione Office di destinazione e viene caricato VSTO componente aggiuntivo di VSTO.

 Quando si avvia il debug di un progetto a livello di documento, il documento o la cartella di lavoro viene aperta in un nuovo processo di Word o Excel.

 Quando si arresta il debugger, il debugger interrompe improvvisamente il processo di applicazione o viene disconnesso se il debugger è impostato per disconnettersi. Tutti gli altri documenti aperti nel processo dell'applicazione di Office terminata vengono chiusi senza avviso e le modifiche non salvate vengono perse. Questo potrebbe includere tutti i documenti o le cartelle di lavoro che vengono aperti durante l'esecuzione del debugger.

 In genere, si consiglia di disconnettersi dal processo prima di arrestare il debugger in modo da poter chiudere l'applicazione di Office in modo normale. È anche possibile disconnettersi dal processo per prima cosa se si desidera usare un documento o un foglio di lavoro aperto dopo l'arresto del debugger.

 Se si esegue il debug di una personalizzazione a livello di documento per Word, arrestando ripetutamente il debugger e causando la chiusura improvvisa di Word, si può danneggiare il modello Normale. In questo caso, è possibile eliminare il modello Normale danneggiato che verrà ricreato automaticamente alla successiva apertura di Word. Tuttavia, non vengono ricreate le macro che sono state archiviate nel modello Normale.

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Eseguire il debug dei componenti aggiuntivi VSTO di Office 2013 con Office 2013 o Office 2016
 Se si usa Visual Studio 2015 e si dispone di entrambe le versioni di Office installate side-by-side, Visual Studio a Office 2016. Se si usa un Visual Studio 2013, Visual Studio a Office 2013.

 Per eseguire il debug del componente aggiuntivo VSTO con una versione di Office diversa (2013 o 2016), aprire **Creazione progetti** e scegliere il pulsante di opzione **Avvia programma esterno** nella scheda **Debug** . Quindi, passare al percorso dell'eseguibile dell'applicazione di Office appropriata.

## <a name="f10-and-f11-behavior"></a>Comportamento di F10 e F11
 Quando si avvia il debug di un progetto Office, **F10** e **F11** non hanno lo stesso comportamento di quando si avvia il debug di altri progetti Visual Basic o C#. Nei progetti Visual Basic o C#, il debugger si arresta sulla funzione principale. Nei progetti di Office, Visual Studio non dispone di controllo sulla funzione principale dell'applicazione di Office. Durante il debug, **tuttavia, F10** e **F11** hanno le stesse funzioni dei progetti Visual Basic e C#.

## <a name="display-exceptions"></a>Visualizzare le eccezioni
 A causa del modo con cui il codice gestito interagisce con il codice non gestito, in Visual Studio non vengono visualizzati gli errori generati dalle applicazioni di Microsoft Office. Ad esempio, se un componente aggiuntivo VSTO creato usando gli strumenti di sviluppo Office in Visual Studio genera un'eccezione, l'applicazione Microsoft Office continua senza visualizzare un errore. Per visualizzare questi errori, impostare il debugger in modo che si interrompa in caso di eccezioni di Common Language Runtime. Per altre informazioni, vedere [Gestire le eccezioni con il debugger.](../debugger/managing-exceptions-with-the-debugger.md)

 Se si imposta il debugger per interrompere l'esecuzione in caso di eccezioni di Common Language Runtime, tutte le eccezioni a questo punto verranno interrotte nel debugger, incluse quelle gestite e alcune eccezioni first-chance del runtime stesso che potrebbero non essere rilevanti per il progetto. Gli errori che fanno riferimento a msosec non trovato, vengono visualizzati in ogni progetto, ma è possibile ignorarli. Queste eccezioni msosec non avranno effetto sulla soluzione.

 È inoltre possibile usare le istruzioni **Try...Catch** sui metodi per raccogliere le eccezioni.

 Per impostazione predefinita, in Visual Studio non vengono visualizzati gli errori di debug Just-In-Time per i progetti di Office. Tuttavia, è possibile abilitare questa funzionalità in modo da poter visualizzare gli errori che vengono generati. Per altre informazioni, vedere [Debug JIT in Visual Studio](../debugger/just-in-time-debugging-in-visual-studio.md).

## <a name="command-line-arguments"></a>Argomenti della riga di comando
 Se  l'azione  di avvio nella pagina delle proprietà Debug è impostata su Avvia **Project**, Visual Studio non usa argomenti della riga di comando durante il debug del progetto, anche se sono stati specificati argomenti della riga di comando come opzioni di avvio. Se si desidera utilizzare gli argomenti della riga di comando quando si avvia il debug, è necessario selezionare un'azione **di** avvio diversa da **Avvia Project**.

## <a name="source-control"></a>Controllo del codice sorgente
 Le proprietà del debug non sono condivise tra più utenti sotto il controllo del codice sorgente. I progetti Visual Basic e C# archiviano le proprietà di debug in un file specifico dell'utente (*NomeProgetto*.vbproj.user o *NomeProgetto*.csproj.user) e questo file non è incluso nel controllo del codice sorgente. Se più di una persona sta eseguendo il debug, è necessario che ciascuna immetta manualmente le proprietà di debug.

## <a name="debug-cached-datasets-in-a-document-level-project"></a>Eseguire il debug di set di dati memorizzati nella cache in un progetto a livello di documento
 Ogni volta che si compila un progetto, il dataset viene svuotato e ricreato. Se si desidera eseguire il debug di un dataset memorizzato nella cache, è necessario aprire il documento all'esterno di Visual Studio e quindi connettere il debugger.

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Eseguire il debug di progetti documento di Word basati sul formato documento di Word 97-2003 (*.doc)
 Per eseguire il debug di un progetto documento di Word basato sul formato Documento di Word 97-2003 (.doc*), è necessario aggiungere la cartella del progetto all'elenco */* di cartelle attendibili. Per altre informazioni su come eseguire questa operazione, vedere Concedere [l'attendibilità ai documenti.](../vsto/granting-trust-to-documents.md)

## <a name="debug-disabled-add-ins"></a>Eseguire il debug di componenti aggiuntivi disabilitati
 Le applicazioni di Microsoft Office possono disabilitare i componenti aggiuntivi VSTO che si comportano in modo imprevisto. Un'applicazione di Microsoft Office disabilita i componenti aggiuntivi VSTO per impedire che il codice con errori venga caricato ogni volta che viene avviata l'applicazione. Tuttavia, è anche facile causare un comportamento imprevisto durante il normale debug. Per informazioni su come ri enable VSTO Add-ins, vedere [Procedura:](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)Abilitare nuovamente un componente aggiuntivo VSTO disabilitato.

 Esistono due tipi di disabilitazione usati dalle applicazioni di Microsoft Office per i componenti aggiuntivi VSTO: disabilitazione che causa la chiusura imprevista dell'applicazione e disabilitazione che non causa la chiusura imprevista dell'applicazione.

### <a name="hard-disabling"></a>Disabilitazione rigida
 La disabilitazione rigida può verificarsi quando VSTO componente aggiuntivo causa la chiusura imprevista dell'applicazione. Si potrebbe verificare anche nel computer di sviluppo se si arresta il debugger durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> nel componente aggiuntivo VSTO. Quando un VSTO componente aggiuntivo è disabilitato, viene visualizzato **nell'elenco Elementi** disabilitati dell'applicazione.

 Se un'applicazione Office disabilita un componente aggiuntivo VSTO creato usando gli strumenti di sviluppo di Office in Visual Studio, l'applicazione disabilita solo il componente aggiuntivo VSTO che ha causato l'errore. Gli altri componenti aggiuntivi VSTO creati usando gli strumenti di sviluppo di Office in Visual Studio per l'applicazione di Office continueranno il caricamento.

### <a name="soft-disabling"></a>Disabilitazione temporanea
 La disabilitazione di tipo "soft" può verificarsi quando un componente aggiuntivo VSTO genera un errore che non causa la chiusura imprevista dell'applicazione. Ad esempio, un'applicazione potrebbe eseguire la disabilitazione di tipo "soft" di un componente aggiuntivo VSTO se viene generata un'eccezione non gestita durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> . Quando un componente aggiuntivo VSTO è disabilitato, viene visualizzato nell'elenco Componenti aggiuntivi **applicazione inattivi** nell'applicazione e l'applicazione modifica il valore della voce del Registro di sistema **LoadBehavior** per il componente aggiuntivo VSTO per indicare che è stato scaricato. Per altre informazioni sulla voce **del Registro di sistema LoadBehavior,** vedere Registry [entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Risolvere gli errori di installazione usando il Visualizzatore eventi
 Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] scrive i messaggi nel Visualizzatore eventi di Windows per tutte le eccezioni generate quando si installano o si disinstallano soluzioni Office. È possibile usare questi messaggi per risolvere i problemi di installazione e distribuzione.

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Risolvere gli errori di avvio usando un file di log e i messaggi di errore
 Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] può scrivere tutti gli errori che si verificano durante l'avvio in un file di log o visualizzare ciascun errore in una finestra di messaggio. Per impostazione predefinita, le opzioni sono disattivate. È possibile attivare le opzioni creando variabili di ambiente.

 Per visualizzare ogni errore in una finestra di messaggio, creare una variabile di ambiente denominata `VSTO_SUPPRESSDISPLAYALERTS` e impostarla su 0 (zero). È possibile eliminare i messaggi eliminando la variabile di ambiente o impostandola su 1 (uno).

 Per scrivere gli errori in un file di log, creare una variabile di ambiente denominata `VSTO_LOGALERTS` e impostarla su 1 (uno). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea il file di log nella cartella che contiene il manifesto della distribuzione per il componente aggiuntivo VSTO o nella cartella che contiene il documento o la cartella di lavoro associata alla personalizzazione. Se l'operazione non riesce, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea il file di log nella cartella *%TEMP%* locale. Per i componenti aggiuntivi VSTO a livello di applicazione, il nome predefinito è *nome componente aggiuntivo*.vsto.log. Per i progetti a livello di documento, il nome del file di log è *nome documento*.*estensione*.log, ad esempio ExcelWorkbook1.xlsx.log. Per arrestare la registrazione degli errori, eliminare la variabile di ambiente o impostarla su 0 (zero).

## <a name="see-also"></a>Vedi anche

- [Creare Office soluzioni](../vsto/building-office-solutions.md)
- [Procedura: Ri enable a VSTO add-in that has been disabled](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md)