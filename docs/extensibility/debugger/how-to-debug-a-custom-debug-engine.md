---
title: 'Procedura: Eseguire il debug di un motore di debug personalizzato Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79790bfc9c9cd3767a453258b8c2d340f64d029
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738582"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Procedura: eseguire il debug di un motore di debug personalizzatoHow To: Debug a custom debug engine
Un tipo di progetto avvia il motore <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> di debug (DE) dal metodo. Ciò significa che il DE viene avviato sotto il controllo dell'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controllo del tipo di progetto. Tuttavia, tale [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] istanza di non può eseguire il debug di DE. Di seguito sono riportati i passaggi che consentono di eseguire il debug del DE personalizzato.

> [!NOTE]
> : nella procedura "Debug di un motore di debug personalizzato", è necessario attendere l'avvio del DE prima di potervi connettere. Se si inserisce una finestra di messaggio vicino all'inizio del DE che viene visualizzato all'avvio di DE, è possibile allegare in quel punto e quindi deselezionare la finestra di messaggio per continuare. In questo modo, è possibile intercettare tutti gli eventi DE.

> [!WARNING]
> È necessario disporre di debug remoto installato prima di tentare le procedure seguenti. Per informazioni [dettagliate,](../../debugger/remote-debugging.md) vedere Debug remoto.

## <a name="debug-a-custom-debug-engine"></a>Eseguire il debug di un motore di debug personalizzatoDebug a custom debug engine

1. Avviare *msvsmon.exe*, Remote Debug Monitor.

2. Dal menu **Strumenti** di *msvsmon.exe*, selezionare **Opzioni** per aprire la finestra di dialogo **Opzioni** .

3. Selezionare l'opzione "nessuna autenticazione" e fare clic su **OK**.

4. Avviare un'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e aprire il progetto DE personalizzato.

5. Avviare una [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seconda istanza di e aprire il progetto personalizzato che avvia il DE (per lo sviluppo, questo è in genere nell'hive del Registro di sistema sperimentale che viene impostato durante l'installazione di VSIP).

6. In questa seconda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]istanza di , caricare un file di origine dal progetto personalizzato e avviare il programma di cui eseguire il debug. Attendere alcuni istanti per consentire il DE caricare o attendere fino a quando non viene raggiunto un punto di interruzione.

7. Nella prima istanza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di (con il progetto DE), selezionare **Connetti a processo** dal Debug menu. **Debug**

8. Nella finestra di dialogo **Connetti a processo** modificare il **trasporto** in **remoto (solo nativo senza autenticazione)**.

9. Modificare il **qualificatore** con il nome della macchina (nota: c'è una cronologia delle voci, quindi è necessario digitare questo nome solo una volta).

10. Nell'elenco **Processi disponibili** selezionare l'istanza del DE in esecuzione e fare clic sul pulsante **Connetti.**

11. Dopo che i simboli sono stati caricati nel DE, inserire punti di interruzione nel codice DE.

12. Ogni volta che si interrompe e quindi si riavvia il processo di debug, ripetere i passaggi da 6 a 10.

## <a name="debug-a-custom-project-type"></a>Eseguire il debug di un tipo di progetto personalizzatoDebug a custom project type

1. Avviare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nell'hive del Registro di sistema normale e caricare il progetto di tipo di progetto (ovvero, l'origine al tipo di progetto, non un'istanza del tipo di progetto).

2. Aprire le proprietà del progetto e passare alla pagina **Debug.Open** the Project properties and go to the Debug page. Per il **comando**, digitare il percorso dell'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (per impostazione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] predefinita, si tratta di *[unità]*.

3. Per gli argomenti `/rootsuffix exp` del **comando**digitare per l'hive del Registro di sistema sperimentale (creato durante l'installazione di VSIP).

4. Fai clic su **OK** per accettare le modifiche.

5. Avviare il tipo di progetto premendo **F5**. Verrà avviata una seconda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]istanza di .

6. A questo punto, è possibile inserire punti di interruzione nel codice sorgente del tipo di progetto.

7. Nella seconda istanza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]di , caricare o creare una nuova istanza del tipo di progetto. Durante il caricamento o la creazione, i punti di interruzione possono essere raggiunti.

8. Eseguire il debug del tipo di progetto.

9. Se si sceglie di eseguire il debug del processo di avvio di un DE, è possibile eseguire i passaggi nella procedura "Debug di un motore di debug personalizzato" per connettersi al DE dopo l'avvio. Ciò fornisce tre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] istanze di esecuzione: uno per l'origine del tipo di progetto, un secondo per il tipo di progetto di cui è stata creata un'istanza e un terzo collegato al DE.

## <a name="see-also"></a>Vedere anche
- [Creazione di un motore di debug personalizzatoCreating a custom debug engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
