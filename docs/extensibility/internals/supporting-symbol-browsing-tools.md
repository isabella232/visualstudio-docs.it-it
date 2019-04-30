---
title: Supporto di strumenti di esplorazione dei simboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 87612ebc9bbcaf14bdf25d91a4e5dbe018c22143
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428763"
---
# <a name="supporting-symbol-browsing-tools"></a>Supporto degli strumenti di esplorazione dei simboli
**Visualizzatore oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate** e **risultati ricerca simbolo** strumenti forniscono le funzionalità in Visual Studio di visualizzazione dei simboli. Questi strumenti visualizzare visualizzazioni dell'albero gerarchico dei simboli e mostrano le relazioni tra i simboli dell'albero. I simboli possono rappresentare gli spazi dei nomi, oggetti, classi, membri di classi e altri elementi del linguaggio contenuti nei vari componenti. I componenti includono progetti di Visual Studio, esterni [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] componenti e le librerie dei tipi (tlb). Per altre informazioni, vedere [Viewing the Structure of Code](../../ide/viewing-the-structure-of-code.md) (Visualizzazione della struttura del codice).

## <a name="symbol-browsing-libraries"></a>Librerie di esplorazione dei simboli
 Come responsabile dell'implementazione linguaggio, è possibile estendere le funzionalità di esplorazione dei simboli di Visual Studio tramite la creazione di librerie che traccia i simboli in componenti e forniscono gli elenchi dei simboli per il gestore oggetti di Visual Studio tramite un set di interfacce. Una libreria è descritta dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interfaccia. Il gestore oggetti di Visual Studio risponde alle richieste per i nuovi dati da strumenti di esplorazione dei simboli ottenendo i dati dalle librerie e organizzandoli. Successivamente compila o aggiorna gli strumenti con i dati richiesti. Per ottenere un riferimento al gestore oggetti, Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, passare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID al servizio il `GetService` (metodo).

 Ogni libreria è necessario registrare con il gestore oggetti di Visual Studio, che consente di raccogliere le informazioni su tutte le librerie. Per registrare una libreria, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> (metodo). A seconda di quale strumento avvia la richiesta, il gestore oggetti di Visual Studio consente di trovare la libreria appropriata e richiede i dati. I dati trasmessi tra le librerie e il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestione degli oggetti negli elenchi dei simboli descritti dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaccia.

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] object manager è responsabile dell'aggiornamento periodicamente gli strumenti di esplorazione dei simboli in modo da riflettere i dati più recenti contenuti nelle librerie.

 Il diagramma seguente contiene un esempio di elementi fondamentali del processo di scambio di richieste/data tra una libreria e la gestione di oggetti di Visual Studio. Le interfacce nel diagramma sono parte di un'applicazione di codice gestito.

 ![Flusso di dati tra una libreria e la gestione degli oggetti](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Per fornire gli elenchi dei simboli per il gestore oggetti di Visual Studio, è innanzitutto necessario registrare la libreria con il gestore oggetti di Visual Studio chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> (metodo). Dopo la registrazione della libreria, il gestore oggetti di Visual Studio richiede alcune informazioni sulle funzionalità della libreria. Ad esempio, richiede i flag della libreria e supportato categorie chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metodi. A un certo punto, quando uno degli strumenti richiede dati da questa libreria, il gestore oggetti richiede l'elenco principale di simboli chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> (metodo). In risposta, la libreria produce un elenco di simboli e lo espone al gestore oggetti Visual Studio tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaccia. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] manager di oggetto determina il numero di elementi incluse nell'elenco chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> (metodo). Tutte le richieste seguenti si riferiscono a un determinato elemento nell'elenco e forniscono il numero di indice di elemento in ogni richiesta. Il gestore oggetti di Visual Studio continua a raccogliere le informazioni sul tipo, l'accessibilità e altre proprietà dell'elemento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> (metodo).

 Determina il nome dell'elemento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metodo e richiede le informazioni sull'icona chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> (metodo). L'icona viene visualizzata a sinistra del nome dell'elemento e viene illustrato il tipo di elemento, l'accessibilità e altre proprietà.

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] object manager chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodo per determinare se un elemento di elenco specificato è espandibile e contiene gli elementi figlio. Se l'interfaccia utente invia una richiesta per espandere un elemento, il gestore oggetti richiede l'elenco figlio di simboli chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> (metodo). Il processo procede con le diverse parti della struttura ad albero viene compilato su richiesta.

> [!NOTE]
> Per implementare un provider di simboli di codice nativo, usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfacce.

## <a name="see-also"></a>Vedere anche
- [Procedura: registrare una libreria con il gestore degli oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Procedura: esporre gli elenchi dei simboli offerti dalla libreria al gestore degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Procedura: identificare i simboli in una libreria](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)