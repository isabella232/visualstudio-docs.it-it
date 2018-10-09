---
title: Aggiornare progetti di unit test di Visual Studio 2010 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f1502b51-d6db-4894-9fbf-4a5723e4bb1a
caps.latest.revision: 8
ms.author: gewarren
manager: douge
ms.openlocfilehash: e06a58e6015a99db83bf729d16196551c5126d12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518170"
---
# <a name="upgrade-visual-studio-2010-unit-test-projects"></a>Aggiornare progetti di unit test di Visual Studio 2010
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] include la compatibilità dei progetti di test con i progetti di test di [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1. Ad esempio, i progetti di test creati con [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 possono essere aperti tramite [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] senza alcun aggiornamento. Il team può quindi usare sia [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 che [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] per lavorare sullo stesso progetto di test. Per altre informazioni, vedere [Aggiornamento dei test da Visual Studio 2010](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).  
  
 In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] sono state introdotte diverse modifiche per gli unit test. A causa di queste modifiche, è importante comprendere i problemi di compatibilità tra le versioni precedenti di Visual Studio e [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. Tra le modifiche apportate agli unit test, una delle più significative è il fatto che [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] include più modelli di progetto di test, tra cui un modello di progetto di unit test. Sono stati aggiunti nuovi unit test al modello di progetto per i nuovi unit test. Gli unit test possono essere inclusi anche in un altro nuovo modello di progetto di test, denominato modello di progetto di test codificato dell'interfaccia utente. Per altre informazioni sui nuovi modelli di progetto di test, vedere [Aggiornamento dei test da versioni precedenti di Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52). I nuovi progetti di unit test non includono più un file di impostazioni di test per impostazione predefinita. L'esclusione del file di impostazioni di test migliora le prestazioni degli unit test. Per garantire la compatibilità, è ancora possibile usare progetti di test esistenti creati mediante Visual Studio 2010. Per motivi di prestazioni, è tuttavia consigliabile rimuovere il file di impostazioni di test associato al progetto di test, a meno che non si abbia una specifica esigenza di usare il file di impostazioni di test. È ad esempio è possibile scegliere di mantenere il file di impostazioni test se gli unit test vengono eseguiti in un ambiente distribuito o se è necessario raccogliere specifici dati di diagnostica. Se si presenta un'esigenza analoga usando il nuovo modello di progetto di unit test o il modello di progetto di test codificati dell'interfaccia utente, è possibile aggiungere manualmente un file di impostazioni di test anche a tali elementi.  
  
> [!NOTE]
>  Gli unit test esistenti nei progetti di test di [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 funzioneranno senza problemi tra [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 e [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. Non vengono apportate modifiche ai file dei progetti di test quando si apre un progetto di test di Visual Studio 2010 contenente unit test in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] o viceversa.  
  
> [!CAUTION]
>  Visual Studio 2010 non è in grado di aprire un progetto C++/CLI destinato al set di strumenti 11.0, ovvero un progetto creato in Visual Studio 2012. Questa limitazione si applica a tutti i progetti C++/CLI, non solo a progetti di unit test C++/CLI.  
  
> [!NOTE]
>  È possibile eseguire di nuovo gli unit test usando vstest.console.exe dalla riga di comando. Per altre informazioni sull'uso di vstest.console.exe, vedere [Opzioni della riga di comando di VSTest.Console.exe](http://msdn.microsoft.com/library/52e1689d-b1a8-4589-bd98-99a55acd0a11) oppure eseguire il comando usando l'opzione per la Guida: **vstest.console.exe /?**. È possibile continuare a eseguire gli unit test esistenti usando MStest.exe. Per altre informazioni, vedere [Eseguire test automatizzati dalla riga di comando con MSTest](http://msdn.microsoft.com/library/39b61ad0-0055-44b5-963f-25d8a6b51581) e [Opzioni della riga di comando di MSTest.exe](http://msdn.microsoft.com/library/8813ba7f-e790-4e92-9f91-7080508a1c36).  
  
 Un'altra modifica significativa è il nuovo Esplora test. In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] sono state deprecate alcune delle finestre di test disponibili nelle versioni precedenti di Visual Studio, ad esempio la finestra Visualizzazione test. Esplora test è progettato per supportare meglio gli sviluppatori e i team che incorporano unit test nelle procedure di sviluppo del software. Per altre informazioni, vedere [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md).  
  
## <a name="compatibility-issues-between-visual-studio-2010-sp1-and-visual-studio-2012"></a>Problemi di compatibilità tra Visual Studio 2010 SP1 e Visual Studio 2012  
 Ecco alcuni problemi da tenere presente quando si esegue la migrazione di unit test tra Visual Studio 2010 SP1 e [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]:  
  
|Funzionalità di unit test|Problema|Soluzione|  
|-----------------------------|-----------|--------------|  
|Gli elenchi di test (file con estensione vsmdi) sono deprecati in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Non sarà più possibile creare nuovi elenchi di test (file con estensione vsmdi) o eseguire elenchi di test da Visual Studio. **Suggerimento:** le categorie di test offrono maggiore flessibilità rispetto agli elenchi di test delle versioni precedenti di Microsoft Visual Studio. È possibile usare operatori logici con le categorie per eseguire insieme test di più categorie oppure limitare i test a quelli che appartengono a più categorie. Le categorie di test sono facili da aggiungere man mano che si creano metodi di test e non è necessario mantenere elenchi di test dopo avere creato i metodi di test. Con l'uso delle categorie non è necessario archiviare ed estrarre il file **\<nome soluzione>.vsmdi** che gestisce gli elenchi di test. Per altre informazioni, vedere [Definizione di categorie per raggruppare i test](http://msdn.microsoft.com/library/2c26a648-f068-4d60-99b6-b9747b7bdbc9).|- Per mantenere la compatibilità con i progetti di test esistenti che usano elenchi di test, è ancora possibile modificare i file con estensione vsmdi tramite Visual Studio.<br />- Anche se non è possibile eseguire gli elenchi di test migrati con Visual Studio, è ancora possibile eseguirli usando mstest.exe dalla riga di comando. Per altre informazioni, vedere [Procedura: Eseguire test automatizzati dalla riga di comando con MSTest](http://msdn.microsoft.com/library/39b61ad0-0055-44b5-963f-25d8a6b51581)<br />-   Se si usa un elenco di test nella definizione di compilazione, è possibile continuare a usarlo. Per altre informazioni, vedere [Procedura: configurare ed eseguire test pianificati dopo avere compilato l'applicazione](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd) ed [Eseguire test nel processo di compilazione](http://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38).|  
|Le funzioni di accesso private sono deprecate in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].<br /><br /> Nelle versioni precedenti di Visual Studio è possibile usare Publicize per specificare un'API (Application Programming Interface) interna e creare API pubbliche equivalenti che è possibile chiamare nei test e che a loro volta chiameranno le API interne del prodotto. È quindi possibile usare la generazione di codice per creare test stub e generare il frammento di codice all'interno di tale stub.|Non sarà più possibile creare funzioni di accesso private.|<ul><li>I progetti di test di Visual Studio 2010 verranno compilati e funzioneranno in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. La compilazione includerà avvisi di output.</li><li>Se è comunque necessario testare le API interne, sono disponibili le opzioni seguenti:<br /><br /> <ul><li>Usare la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> per semplificare l'accesso alle API interne e private nel codice. Questo metodo è disponibile nell'assembly Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll.</li><li>Creare un framework di reflection in grado di effettuare la reflection del codice per l'accesso alle API interne o private.</li><li>Se il codice a cui si sta tentando di accedere è interno, si potrebbe essere in grado di accedere all'API tramite <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, in modo da garantire al codice di test l'accesso alle API interne.</li></ul></li></ul>|  
|Impatto test è stato rimosso|||  
|Condivisione dei risultati delle esecuzioni tramite log TRX da Esplora test.||È ancora possibile ottenere i log TRX sia dalla riga di comando che da Team Build.|  
  
## <a name="see-also"></a>Vedere anche  
 [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Eseguire unit test del codice](../test/unit-test-your-code.md)   
 [Aggiornamento dei test da versioni precedenti di Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [Aggiornamento dei test codificati dell'interfaccia utente da Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)