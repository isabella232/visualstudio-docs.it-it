---
title: Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 38374893aea62af1b664065edf0ca9195f3dd301
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540712"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [finestra di dialogo Opzioni, progetti e soluzioni, compila ed Esegui](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run).  
  
  
In questa finestra di dialogo, è possibile specificare il numero massimo di progetti Visual C++ o Visual C# che è possibile compilare allo stesso tempo, determinati comportamenti di compilazione predefiniti e alcune impostazioni del log di compilazione. Per aprire il **opzioni** finestra di dialogo, scegliere **Tools**, **opzioni** nella barra dei menu. Per accedere a questo set di opzioni, espandere **progetti e soluzioni**, quindi scegliere **compila ed Esegui**.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **numero massimo di compilazioni di progetto parallele**  
 Specifica il numero massimo di progetti Visual C++ e Visual C# che è possibile compilare contemporaneamente. Per ottimizzare il processo di compilazione, il numero massimo di compilazioni di progetti in parallelo viene impostato automaticamente sul numero di CPU del computer. Il numero massimo è 32.  
  
 **Compila progetti di avvio e dipendenze solo in fase di esecuzione**  
 Il progetto di avvio e le relative dipendenze sono create se questa casella di controllo è selezionata quando si sceglie il tasto F5; Scegliere **Debug**, **avviare** dal menu oppure **compilare**, **compilare** nella barra dei menu. Tutti i progetti, dipendenze e i file della soluzione vengono compilati se questa casella di controllo è deselezionata quando si sceglie il tasto F5; Scegliere **Debug**, **avviare** dal menu oppure **compilare**, **compilare** nella barra dei menu. Per impostazione predefinita, questa opzione è deselezionata.  
  
 **Durante l'esecuzione, quando i progetti non sono aggiornati**  
 > [!NOTE]
>  Questo elenco si applica solo ai progetti [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 Per impostazione predefinita, viene visualizzato un messaggio se una configurazione di progetto non è aggiornata quando preme il tasto F5 o si sceglie **Debug**, **avviare** nella barra dei menu. È possibile specificare se generare comunque il progetto e se viene visualizzato il messaggio. Usare questa opzione per specificare se viene visualizzato il messaggio e quale deve essere il comportamento di compilazione se non viene visualizzato il messaggio.  
  
 **Compila sempre**  
 Non viene visualizzata la finestra di messaggio e il progetto viene compilato nonostante la configurazione non aggiornata. Questa opzione viene impostata quando seleziona il **non visualizzare più questa finestra di dialogo** nel messaggio e quindi selezionare la **Yes** pulsante.  
  
 **Non compilare mai**  
 Non viene visualizzata la finestra di messaggio e il progetto non viene compilato. Questa opzione viene impostata quando seleziona il **non visualizzare più questa finestra di dialogo** nel messaggio e quindi selezionare la **No** pulsante.  
  
 **Richiedi compilazione**  
 Mostra la finestra di messaggio ogni volta che una configurazione del progetto non è aggiornata.  
  
 **Durante l'esecuzione, quando si verificano errori di compilazione o distribuzione**  
 Se si verificano errori di compilazione quando si avvia una compilazione dal **compilazione** menu, viene visualizzato un messaggio. È possibile specificare se continuare avviando l'applicazione e se il messaggio viene visualizzato ogni volta che si verificano errori di compilazione. Usare questa opzione per specificare se viene visualizzato il messaggio e quale deve essere il comportamento se non viene visualizzato il messaggio.  
  
> [!NOTE]
>  Questa opzione si applica solo ai progetti [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 **Richiedi avvio**  
 Mostra una finestra di messaggio ogni volta che si verificano errori di compilazione.  
  
 **Non avviare**  
 Non viene visualizzata la finestra di messaggio e l'applicazione non viene avviata. Questa opzione viene impostata quando seleziona il **non visualizzare più questa finestra di dialogo** casella di controllo nella finestra di messaggio e quindi scegliere il **No** pulsante.  
  
 **Avvia versione precedente**  
 Non viene visualizzata la finestra di messaggio e la versione dell'applicazione appena compilata non viene avviata. Questa opzione viene impostata quando seleziona il **non visualizzare più questa finestra di dialogo** casella di controllo nella finestra di messaggio e quindi scegliere il **Yes** pulsante.  
  
 **Per nuove soluzioni utilizza il progetto selezionato come progetto di avvio**  
 Se questa casella di controllo è selezionata, le nuove soluzioni usano il progetto selezionato come progetto di avvio.  
  
 **Livello di dettaglio output in compilazione progetto MSBuild**  
 Determina la quantità di informazioni visualizzata nella finestra **Output** per la compilazione.  
  
 **Livello di dettaglio file di log di compilazione progetto MSBuild**  
 > [!NOTE]
>  Questa opzione si applica solo ai progetti Visual C++.  
  
 Determina la quantità di informazioni scritta nel file di log di compilazione che si trova in \\...\\*ProjectName*\Debug\\*ProjectName*.log.  
  
## <a name="see-also"></a>Vedere anche  
 [Compiling and Building](../../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)



