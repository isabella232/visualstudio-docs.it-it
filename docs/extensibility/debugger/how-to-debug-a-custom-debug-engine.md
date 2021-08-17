---
title: 'Procedura: Eseguire il debug di un motore di debug personalizzato | Microsoft Docs'
description: Informazioni sui passaggi che consentono di usare le Visual Studio eseguire il debug del motore di debug personalizzato o di un tipo di progetto personalizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ecaa14f0b9576ab805aa0a880f82766f6fe546c4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057876"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Procedura: Eseguire il debug di un motore di debug personalizzato
Un tipo di progetto avvia il motore di debug dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metodo . Ciò significa che de viene avviato sotto il controllo dell'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che controlla il tipo di progetto. Tuttavia, tale istanza di non [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] può eseguire il debug di DE. Di seguito sono riportati i passaggi che consentono di eseguire il debug di deretierazione personalizzata.

> [!NOTE]
> : nella procedura "Eseguire il debug di un motore di debug personalizzato", è necessario attendere l'avvio di DE prima di potersi collegare a esso. Se si posiziona una finestra di messaggio all'inizio di DE visualizzata all'avvio di DE, è possibile collegarsi a tale punto e quindi deselezionare la finestra di messaggio per continuare. In questo modo, è possibile intercettare tutti gli eventi DE.

> [!WARNING]
> È necessario che sia installato il debug remoto prima di provare le procedure seguenti. Per [informazioni dettagliate, vedere](../../debugger/remote-debugging.md) Debug remoto.

## <a name="debug-a-custom-debug-engine"></a>Eseguire il debug di un motore di debug personalizzato

1. Avviare *msvsmon.exe*, Remote Debug Monitor.

2. Dal menu **Strumenti** in *msvsmon.exe* selezionare **Opzioni per** aprire la finestra **di dialogo** Opzioni.

3. Selezionare l'opzione "nessuna autenticazione" e fare clic su **OK.**

4. Avviare un'istanza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di e aprire il progetto DE personalizzato.

5. Avviare una seconda istanza di e aprire il progetto personalizzato che avvia DE (per lo sviluppo, in genere si trova nell'hive del Registro di sistema sperimentale configurato quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSIP è installato).

6. In questa seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caricare un file di origine dal progetto personalizzato e avviare il programma di cui eseguire il debug. Attendere alcuni istanti per consentire il caricamento di DE o attendere fino a quando non viene raggiunto un punto di interruzione.

7. Nella prima istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (con il progetto DE) selezionare **Associa a processo** dal menu **Debug.**

8. Nella finestra **di dialogo Associa a** processo impostare Trasporto su Remoto **(solo nativo senza autenticazione)**. 

9. Modificare **qualificatore** con il nome del computer (si noti che è presente una cronologia di voci, quindi è necessario digitare questo nome una sola volta).

10. **Nell'elenco Processi disponibili** selezionare l'istanza di DE in esecuzione e fare clic sul **pulsante** Associa.

11. Dopo aver caricato i simboli in DE, inserire punti di interruzione nel codice DE.

12. Ogni volta che si arresta e quindi si riavvia il processo di debug, ripetere i passaggi da 6 a 10.

## <a name="debug-a-custom-project-type"></a>Eseguire il debug di un tipo di progetto personalizzato

1. Iniziare dall'hive del registro normale e caricare il progetto del tipo di progetto( ovvero l'origine del tipo di progetto, non la creazione di un'istanza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del tipo di progetto).

2. Aprire le Project e passare alla **pagina Debug.** Per **comando**, digitare il percorso dell'IDE (per impostazione predefinita, si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tratta di *[unità]* \Programmi\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. Per Argomenti **del comando** digitare per l'hive del Registro di sistema `/rootsuffix exp` sperimentale (creato durante l'installazione di VSIP).

4. Fai clic su **OK** per accettare le modifiche.

5. Avviare il tipo di progetto premendo **F5.** Verrà avviata una seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

6. A questo punto, è possibile inserire punti di interruzione nel codice sorgente del tipo di progetto.

7. Nella seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caricare o creare una nuova istanza del tipo di progetto. Durante il caricamento o la creazione, è possibile che i punti di interruzione siano stati raggiunto.

8. Eseguire il debug del tipo di progetto.

9. Se si sceglie di eseguire il debug del processo di avvio di un de, è possibile eseguire i passaggi della procedura "Eseguire il debug di un motore di debug personalizzato" per connettersi a DE dopo l'avvio. In questo modo sono disponibili tre istanze di in esecuzione: una per l'origine del tipo di progetto, una seconda per il tipo di progetto di cui è stata creata un'istanza e una terza associata al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de.

## <a name="see-also"></a>Vedi anche
- [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
