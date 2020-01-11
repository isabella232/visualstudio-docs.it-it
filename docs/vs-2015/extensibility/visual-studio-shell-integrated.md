---
title: Visual Studio Shell (Integrated) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4f6e88e5c430129faa80f34a45f9b6620d5b0d13
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850366"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (Integrated)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La shell integrata di Visual Studio include l'ambiente di sviluppo integrato, il debugger, e l'integrazione per il controllo del codice sorgente. Non è incluso alcun linguaggio di programmazione. Tuttavia, la shell integrata fornisce un Framework che consente di aggiungere linguaggi di programmazione.  
  
 Visual Studio Integrated Shell è in realtà una combinazione di Visual Studio Isolated Shell, oltre a un'installazione aggiuntiva che include componenti specifici della shell integrata.  L'applicazione shell integrata deve includere sia il pacchetto ridistribuibile della shell isolata da [Microsoft Visual Studio Shell (isolated) pacchetto ridistribuibile](https://docs.microsoft.com/collaborate/connect-redirect?ProgramID=8963&InvitationID=VS15-2R69-RB8J) che il pacchetto ridistribuibile di Shell integrato da [Microsoft Visual Studio Shell (Integrated) pacchetto ridistribuibile](https://docs.microsoft.com/collaborate/connect-redirect?ProgramID=8963&InvitationID=VS15-2R69-RB8J).  
  
> [!NOTE]
> prima di accedere ai pacchetti ridistribuibili per la shell isolata e integrata, dovrai completare un breve sondaggio per i clienti.  Al termine del sondaggio, verrai reindirizzato a una pagina di Visual Studio Connect che include i collegamenti per il download dei pacchetti ridistribuibili.  È possibile trovare i collegamenti per il download nelle visite successive al sito di Visual Studio Connect nella scheda  **&#124; programmi Visual Studio 2015 Integrated and isolated shell** .  
  
 Se si installa l'applicazione shell integrata nello stesso computer della versione completa di Visual Studio, i componenti dell'applicazione verranno integrati direttamente in Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Funzionalità della shell integrata  
  
|||  
|-|-|  
|Area delle funzionalità|Caratteristica|  
|Supporto linguistico|-Nessuno|  
|IDE|<ul><li>Impostazioni<br /><br /> <ul><li>Crea impostazioni</li><li>Importare ed esportare le impostazioni</li><li>Reimpostare le impostazioni</li></ul></li><li>Integrazione della **casella degli strumenti**</li><li>Integrazione di **elenco attività**</li><li>Integrazione della Guida</li><li>Finestra di dialogo **Opzioni**</li><li>Gestione di tipi di carattere e colori</li><li>Finestra di **output**</li><li>Finestra di **comando**</li><li>Gestione delle finestre</li><li>Comandi, menu e tasti di scelta rapida</li><li>Runtime del linguaggio specifico di dominio (DSL)</li></ul>|  
|Tipi di progetto e di sistema del progetto|-Soluzioni e cartelle soluzione<br />-Gestione configurazione soluzioni<br />-Gestione degli elementi<br />-Soluzioni a progetto singolo e multiprogetto<br />-Progettazione applicazioni (proprietà del progetto semplificate)<br />-Aggiungi riferimento Web<br />-Aggiungi riferimento al servizio<br />-Singolo progetto<br />-Tipi di progetto di sito Web<br />-Progetti di applicazione Web|  
|Compila|-Passaggi di compilazione personalizzati nell'IDE<br />-Pre-compilazione per la protezione della proprietà intellettuale (IP)<br />-Firma codice<br />     MSBuild|  
|Editor|-Strumenti di esplorazione del codice (ricerca unificata, definizione di origine, ereditarietà)<br />-Navigazione del codice<br />-IntelliSense<br />-Degli smart tag<br />-Refactoring<br />-Bell'elenco<br />-Filtro IntelliSense<br />-   finestra **definizione codice**|  
|Designer|-Windows Presentation Foundation Designer<br />-Progettazione Windows Form<br />-Finestra di progettazione Web e editor HTML|  
|Data|-   **Esplora server** (semplificata: solo dati). Vedere la nota 1.<br />-   finestra **origini dati**<br />-Set completo di controlli dati<br />-Editor XML<br />-I dati vengono associati a un'origine dati locale (. MDF o. MDB<br />-Associazione dati a oggetto<br />-Associazione dati al servizio Web<br />-Data binding al server di database locale<br />-Data binding al server di database remoto<br />-Strumenti DDL per dati remoti<br />estendibilità di -   **Esplora server** (esempi di[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)])|  
|Debugger|-Debug locale. Vedere la nota 2.<br />-Debug gestito<br />-Debug locale<br />-Connetti a processo locale<br />-Connetti a processo remoto<br />-Delegato anonimo<br />-Domini applicazione<br />-Debug ASPX<br />-Attributi<br />-Break durante Func-EVAL<br />-Punti di interruzione<br />-Vincoli del punto di interruzione<br />-Stack<br />finestra di **comando** -   <br />-Debug tra thread<br />-Suggerimenti dati<br />-Visualizzatore dati<br />-Supporto del debugger per gli assistenti al debug gestito (MDA)<br />-Supporto del debugger per il server d'avanzamento del tipo<br />-Supporto DTEEvents per OTB<br />-Stepper Stepper<br />-Test AppID del debugger (DBGCLR)<br />-Profilo debugger<br />-Strumenti e opzioni del debugger<br />-Iteratore di debug<br />-Valutazione delle espressioni in fase di progettazione<br />- C# Analizzatore di espressioni<br />-Disassembly<br />-Modifica e continuazione<br />-Finestre dell'analizzatore di espressioni (espressioni di controllo, variabili locali, auto)<br />-Helper eccezioni<br />-Eccezioni<br />-Esecuzione<br />- Generics<br />-Recupero origine destra<br />-Debug HPC/cluster<br />-Debug multilingua integrato<br />-Debug di interoperabilità<br />-Debug just-in-Time<br />-Debug locale<br />-Debug gestito<br />-Controllo manuale (finestra processi)<br />-Memoria<br />-Supporto MiniDump<br />-Moduli<br />-Debug a più processi<br />-Debug nativo<br />-Nuovo supporto del motore di debug<br />-Debug del codice ottimizzato<br />-Filtro di output di Windows<br />-Processo di hosting per il debug gestito<br />-Processi<br />-Controllo immediato<br />-Registri<br />-Registri nello stack<br />-Debug remoto<br />-Valori restituiti<br />-Debug di script<br />-Supporto per il servizio di origine<br />-Sicurezza<br />-Side-by-side<br />-SQL<br />-Server di simboli<br />-Punti di traccia<br />-Thread<br />-Visualizzazioni<br />-Extensible Stylesheet Language Transformations debugger (XSLT)|  
|Supporto a 64-bit|-debug a 64 bit per codice gestito e nativo, tutti i linguaggi<br />-supporto nativo x64|  
|Controllo del codice sorgente (SCC)|-Integrazione SCC di base. Vedere la nota 3.<br />-Verifica strumenti e opzioni|  
|Extensibility|-Utilizzare VSPackage e componenti MEF|  
  
## <a name="notes"></a>Note  
  
#### <a name="1-data-tools"></a>1. Data Tools  
 La shell integrata include strumenti di sviluppo di database quali il supporto per l'estendibilità dei dati e il **Esplora soluzioni**semplificato. Tuttavia, SQL Server Express, report SQL e Crystal Reports non sono inclusi nella shell integrata.  
  
#### <a name="2-debugging-support"></a>2. supporto per il debug  
 La shell integrata include lo stesso motore di debug incluso nella versione community di Visual Studio. Il motore di debug include il debugger comune per il codice gestito e anche le funzionalità correlate, ad esempio l'esecuzione, la connessione, l'impostazione del punto di interruzione, la modifica e la continuazione e altre ancora. Tuttavia, il motore di debug non supporta SQL Server il debug del database.  
  
 Sebbene il supporto per il debug nativo sia incluso nel pacchetto di base del debugger, non è possibile estenderlo per supportare lingue aggiuntive.  
  
#### <a name="3-source-code-control-integration"></a>3. integrazione del controllo del codice sorgente  
 La shell integrata fornisce le API per l'implementazione del controllo del codice sorgente (SCC) e per fornire i componenti di integrazione comuni del controllo del codice sorgente basati su MSSCCI.  
  
 Sebbene l'integrazione di SCC non sia una funzionalità standard dell'edizione Pro di Visual Studio, l'integrazione di SCC è disponibile nella shell integrata.  
  
#### <a name="4-build-support"></a>4. supporto della compilazione  
 La shell integrata fornisce supporto per la compilazione. È possibile trovare informazioni sulle compilazioni nel [riferimento a MSBuild](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Funzionalità non incluse nella shell integrata  
 Di seguito è riportato un elenco di funzionalità che non sono incluse nella shell integrata:  
  
- Progettazione classi  
  
- PreEmptive Protection - Dotfuscator  
  
- Funzionalità del linguaggio  
  
- VSHost  
  
- Nella shell integrata non è incluso alcun linguaggio di Visual Studio né i modelli di progetto o i modelli di elementi di progetto associati. Non sono incluse implementazioni specifiche della lingua di altre funzionalità, ad esempio Visual Basic frammenti di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica sull'estensione di Visual Studio](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)
