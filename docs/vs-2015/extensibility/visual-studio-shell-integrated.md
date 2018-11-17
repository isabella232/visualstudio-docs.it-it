---
title: Visual Studio Shell (integrata) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3eb0c8dd0588e1af9b3aad500c8bc9f899b44513
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765286"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (integrata)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La shell integrata di Visual Studio include l'ambiente di sviluppo integrato (IDE) debugger e integrazione del controllo codice sorgente. Non è incluso alcun linguaggio di programmazione. Tuttavia, la shell integrata forniscono un framework che consente di aggiungere i linguaggi di programmazione.  
  
 La shell integrata di Visual Studio è effettivamente una combinazione di shell isolata di Visual Studio e un'installazione aggiuntiva che includono componenti specifici di shell integrata.  L'applicazione di shell integrata deve includere sia il pacchetto ridistribuibile shell isolata dal [Microsoft Visual Studio Shell (Isolated) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022) , nonché il pacchetto ridistribuibile di shell integrata dal [Microsoft Visual Studio Shell (Integrated) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Prima di poter accedere i pacchetti ridistribuibili di shell isolata e integrata, verrà richiesto a un cliente breve sondaggio.  Dopo aver compilato il sondaggio, si verrà indirizzati a una pagina con collegamenti ai download del pacchetto ridistribuibile Visual Studio Connect.  È possibile trovare collegamenti per il download nelle visite successive al sito di Visual Studio Connect con la **programmi &#124; VISUAL STUDIO 2015 integrata e isolata SHELL** scheda.  
  
 Se si installa l'applicazione di shell integrata nello stesso computer di una versione completa di Visual Studio, i componenti dell'applicazione verranno integrati direttamente in Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Funzionalità nella Shell integrata  
  
|||  
|-|-|  
|Area funzionalità|Funzionalità|  
|Supporto per le lingue|-None|  
|IDE|<ul><li>Impostazioni<br /><br /> <ul><li>Creare le impostazioni</li><li>Importa / Esporta impostazioni</li><li>Reimpostare le impostazioni</li></ul></li><li>**Casella degli strumenti** integrazione</li><li>**Elenco delle attività** integrazione</li><li>Integrazione della Guida</li><li>**Opzioni** nella finestra di dialogo</li><li>Gestione tipi di carattere e colori</li><li>**Output** finestra</li><li>**Comando** finestra</li><li>Gestione delle finestre</li><li>I comandi, menu e tasti di scelta rapida</li><li>Runtime di linguaggio specifico di dominio (DSL)</li></ul>|  
|Sistema di progetto e tipi di progetto|-Soluzioni e le cartelle della soluzione<br />-Gestione configurazione soluzione<br />-Gestione elemento<br />-Soluzioni progetto singolo e più progetti<br />-Progettazione di applicazioni (proprietà del progetto semplificata)<br />-Aggiungi riferimento Web<br />-Aggiungi riferimento al servizio<br />Progetto singolo<br />: Tipi di progetto sito Web<br />-Progetti di applicazione web|  
|Compilazione|-Istruzioni di compilazione personalizzate nell'IDE<br />-Pre-compilazione per la protezione della proprietà intellettuale (IP)<br />-La firma del codice<br />     MSBuild|  
|Editor|-Esplorazione di strumenti (ricerca unificata, definizione dell'origine, ereditarietà) del codice<br />-Esplorazione del codice<br />-IntelliSense<br />-Degli smart tag<br />-Refactoring<br />-Riformatta il listato<br />: Filtro IntelliSense<br />-   **Definizione di codice** finestra|  
|Designer|-Windows Presentation Foundation Designer<br />-Windows Form Designer<br />-Finestra di progettazione e web Editor HTML|  
|Dati|-   **Esplora server** (semplificato: solo i dati). Vedere la nota 1.<br />-   **Zdroje dat** finestra<br />-Set completo di controlli dati<br />: Editor XML<br />-Data binding all'origine dati locale (. File MDF o. MDB)<br />-Associare i dati oggetto<br />-Data binding al servizio Web<br />-Data binding al server di database locale<br />-Data binding al server di database remoto<br />-Strumenti DDL per i dati remoti<br />-   **Esplora server** estendibilità ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] esempi)|  
|Debugger|-Debug locale. Vedere la nota 2.<br />-Il debug gestito<br />-Debug locale<br />-Connetti a processo locale<br />-Connettersi al processo remoto<br />-Delegato anonimo<br />-Domini dell'applicazione<br />-Debug ASPX<br />-Attributi<br />-Interrompere la funzione eval<br />-Punti di interruzione<br />-I vincoli punto di interruzione<br />-Stack di chiamate<br />-   **Comando** finestra<br />-Debug Cross-thread<br />-Suggerimenti sui dati<br />-Visualizzatore dati<br />-Supporto debugger per assistenti al debug gestiti (MDA)<br />-Supporto debugger per server d'inoltro<br />-Supporto DTEEvents per OTB<br />-Gestore di JMC istruzioni<br />-Test di AppID debugger (DBGCLR)<br />-Profilo debugger<br />-Del debugger strumenti e opzioni<br />-Debug iterator<br />-Valutazione dell'espressione design-time<br />-C# l'analizzatore di espressioni<br />-Disassembly<br />-Modifica e continuazione<br />-Windows dell'analizzatore di espressioni expression (espressione di controllo, variabili locali, Auto)<br />-Supporto eccezione<br />-Le eccezioni<br />-Execution<br />- Generics<br />-Recupero origine corretta<br />-Debug/Cluster HPC<br />-Multilingue debug integrato<br />-Debug interoperabilità<br />Debug just-in-time<br />-Debug locale<br />-Il debug gestito<br />-Controllo manuale (finestra processi)<br />-Memoria<br />-Supporto miniDump<br />-I moduli<br />-Debug a più processori<br />-Debug nativo<br />-Nuovo supporto di motore di debug<br />-Debug del codice ottimizzato<br />-La finestra di output applicazione di filtri<br />-Processo di hosting per il debug gestito<br />-Processi<br />-Controllo immediato<br />: Registra<br />-Registri nello stack<br />-Debug remoto<br />: Restituisce valori<br />: Debug degli script<br />-Supporto del servizio origine<br />-Sicurezza<br />Side-by-side<br />-SQL<br />: Server di simboli<br />: Punti di traccia<br />-Thread<br />-Visualizzazioni<br />-Debugger di extensible Stylesheet Language Transformations (XSLT)|  
|Supporto a 64 bit|-debug a 64 bit per codice gestito e nativo, tutte le lingue<br />-supporto x64 nativo|  
|Controllo del codice sorgente (SCC)|-L'integrazione di SCC di base. Vedere la nota 3.<br />-Strumenti e le opzioni di verifica|  
|Estendibilità|-Utilizzo di componenti MEF e i pacchetti VSPackage|  
  
## <a name="notes"></a>Note  
  
#### <a name="1-data-tools"></a>1. Strumenti dati  
 Shell integrata include strumenti di sviluppo di database, ad esempio il supporto di estendibilità di data e il semplificata **Esplora soluzioni**. SQL Server Express, SQL Reporting e Crystal Reports, tuttavia, non sono inclusi nella shell integrata.  
  
#### <a name="2-debugging-support"></a>2. Supporto per il debug  
 Shell integrata include lo stesso motore di debug che è incluso nella versione Community di Visual Studio. Il motore di debug include il debugger comune per il codice gestito, nonché le funzionalità correlate, ad esempio eseguire, Connetti, Imposta punto di interruzione, modifica e continuazione e altri. Tuttavia, il motore di debug non supporta il debug di database di SQL Server.  
  
 Anche se il supporto per il debug nativo viene incluso nel pacchetto di base del debugger, è possibile estendere in modo da supportare linguaggi aggiuntivi.  
  
#### <a name="3-source-code-control-integration"></a>3. Integrazione del controllo codice sorgente  
 Shell integrata fornisce API per l'implementazione del controllo del codice sorgente (SCC) e per fornire il controllo origine comune basato su MSSCCI i componenti di integrazione.  
  
 Anche se l'integrazione di controllo del codice sorgente non è una funzionalità normale dell'edizione Pro di Visual Studio, nella shell integrata viene offerta l'integrazione di SCC.  
  
#### <a name="4-build-support"></a>4. Supporto per la compilazione  
 Shell integrata fornisce supporto per la compilazione. È possibile trovare informazioni sulle compilazioni di [riferimenti a MSBuild](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Funzionalità non incluse nella Shell integrata  
 Di seguito è riportato un elenco delle funzionalità che non sono inclusi nella shell integrata:  
  
-   Progettazione classi  
  
-   DotFuscator preventiva  
  
-   Funzionalità del linguaggio  
  
-   VSHost  
  
-   Nessuna lingua di Visual Studio o i modelli di progetto associata o i modelli di progetto, sono inclusi nella shell integrata. Nessun implementazioni specifiche della lingua di altre funzionalità sono incluse, per i frammenti di codice di esempio Visual Basic.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di panoramica di Visual Studio](http://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)