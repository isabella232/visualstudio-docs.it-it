---
title: Supporto degli strumenti di esplorazione dei simboli Documenti Microsoft
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704773"
---
# <a name="supporting-symbol-browsing-tools"></a>Supporto degli strumenti di esplorazione dei simboli
**Browser oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate** e Trova risultati **simbolo** forniscono funzionalità di esplorazione dei simboli in Visual Studio. Questi strumenti visualizzano le viste ad albero gerarchiche dei simboli e mostrano le relazioni tra i simboli nell'albero. I simboli possono rappresentare spazi dei nomi, oggetti, classi, membri di classi e altri elementi del linguaggio contenuti in vari componenti. I componenti includono progetti di Visual Studio, componenti esterni di .NET Framework e librerie di tipi (tlb). Per ulteriori informazioni, vedere [Visualizzazione della struttura del codice](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Librerie di esplorazione dei simboli
 In qualità di implementatore del linguaggio, è possibile estendere le funzionalità di esplorazione dei simboli di Visual Studio creando librerie che tengono traccia dei simboli nei componenti e forniscono gli elenchi di simboli al gestore di oggetti di Visual Studio tramite un set di interfacce. Una libreria è <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> descritta dall'interfaccia. Il gestore di oggetti di Visual Studio risponde alle richieste di nuovi dati dagli strumenti di esplorazione dei simboli ottenendo i dati dalle librerie e organizzandoli. Successivamente popola o aggiorna gli strumenti con i dati richiesti. Per ottenere un riferimento al gestore di oggetti di Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>passare l'ID del <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> servizio al `GetService` metodo .

 Ogni libreria deve registrarsi con il gestore di oggetti di Visual Studio, che raccoglie le informazioni in tutte le librerie. Per registrare una <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> libreria, chiamare il metodo . A seconda dello strumento che avvia la richiesta, il gestore di oggetti di Visual Studio trova la libreria appropriata e richiede i dati. I dati si spostano [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tra le librerie e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> il gestore di oggetti in elenchi di simboli descritti dall'interfaccia.

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestore di oggetti è responsabile dell'aggiornamento periodico degli strumenti di esplorazione dei simboli per riflettere i dati più aggiornati contenuti nelle librerie.

 Il diagramma seguente contiene un esempio di elementi chiave del processo di richiesta/scambio di dati tra una libreria e il gestore di oggetti di Visual Studio. Le interfacce nel diagramma fanno parte di un'applicazione di codice gestito.

 ![Flusso dei dati tra una libreria e il gestore oggetti](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram (Diagramma di CallBrowser)")

 Per fornire gli elenchi di simboli al gestore di oggetti di Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> è innanzitutto necessario registrare la libreria con il gestore di oggetti di Visual Studio chiamando il metodo . Dopo la registrazione della libreria, il gestore di oggetti di Visual Studio richiede alcune informazioni sulle funzionalità della libreria. Ad esempio, richiede i flag di libreria <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> e le categorie supportate chiamando i metodi e . A un certo punto, quando uno degli strumenti richiede dati da questa libreria, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> gestore di oggetti richiede l'elenco di primo livello dei simboli chiamando il metodo . In risposta, la libreria produce un elenco di simboli e lo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> espone al gestore di oggetti di Visual Studio tramite l'interfaccia. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestore di oggetti determina il numero <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> di elementi presenti nell'elenco chiamando il metodo . Tutte le richieste seguenti si riferiscono a un determinato elemento nell'elenco e forniscono il numero di indice dell'elemento in ogni richiesta. Il gestore di oggetti di Visual Studio procede a raccogliere le informazioni sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> tipo, l'accessibilità e altre proprietà dell'elemento chiamando il metodo .

 Determina il nome dell'elemento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> chiamando il metodo e richiede <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> le informazioni sull'icona chiamando il metodo . L'icona viene visualizzata a sinistra del nome dell'elemento e illustra il tipo di elemento, l'accessibilità e altre proprietà.

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestore <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> di oggetti chiama il metodo per determinare se un determinato elemento dell'elenco è espandibile e dispone di elementi figlio. Se l'interfaccia utente invia una richiesta per espandere un elemento, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> il gestore di oggetti richiede l'elenco figlio di simboli chiamando il metodo . Il processo continua con diverse parti dell'albero in fase di costruzione su richiesta.

> [!NOTE]
> Per implementare un provider di <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> simboli di codice nativo, utilizzare le interfacce e .

## <a name="see-also"></a>Vedere anche
- [Procedura: Registrare una libreria con il gestore degli oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Procedura: Esporre gli elenchi dei simboli forniti dalla libreria al gestore degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Procedura: Identificare i simboli in una libreria](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
