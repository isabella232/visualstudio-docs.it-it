---
redirect_url: shell/visual-studio-shell-integrated
title: Visual Studio Shell (integrata) | Documenti Microsoft
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b43e4ac1c8e40a9f4f378be42cc642767bee0777
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (integrata)
La shell integrata di Visual Studio include l'ambiente di sviluppo integrato (IDE), debugger e l'integrazione del controllo codice sorgente. Nessun linguaggio di programmazione è incluso. Tuttavia, la shell integrata fornisce un framework che consente di aggiungere i linguaggi di programmazione.  
  
 La shell di Visual Studio integrato è effettivamente una combinazione di shell di Visual Studio isolated più di un'installazione aggiuntiva che includono i componenti specifici di shell integrata.  L'applicazione shell integrata deve includere sia il pacchetto ridistribuibile shell isolata da [Microsoft Visual Studio Shell (Isolated) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022) nonché il pacchetto ridistribuibile shell integrata da [Microsoft Visual Studio Shell (Integrated) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Prima di poter accedere i pacchetti ridistribuibili shell isolata e integrata, verrà richiesto di compilare un'indagine breve.  Dopo aver compilato il sondaggio, si verrà reindirizzati a una pagina di Visual Studio connettersi con i collegamenti ai download pacchetto ridistribuibile.  È possibile trovare i collegamenti ai download nelle visite successive al sito in Visual Studio connettersi il **programmi &#124; VISUAL STUDIO 2015 integrata e SHELL isolata** scheda.  
  
 Se si installa l'applicazione shell integrata nello stesso computer come una versione completa di Visual Studio, i componenti dell'applicazione verranno integrati direttamente in Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Funzionalità nella Shell integrata  
  
|||  
|-|-|  
|Area funzionalità|Funzionalità|  
|Supporto per le lingue|-Nessuno|  
|IDE|<ul><li>Impostazioni<br /><br /> <ul><li>Creare le impostazioni</li><li>Importa / Esporta impostazioni</li><li>Impostazioni di ripristino</li></ul></li><li>**Casella degli strumenti** integrazione</li><li>**Elenco attività** integrazione</li><li>Integrazione della Guida</li><li>**Opzioni** la finestra di dialogo</li><li>Gestione dei tipi di carattere e colori</li><li>**Output** finestra</li><li>**Comando** finestra</li><li>Gestione delle finestre</li><li>I comandi, menu e tasti di scelta rapida</li><li>Runtime di linguaggio specifico di dominio (DSL)</li></ul>|  
|Sistema di progetto e i tipi di progetto|-Soluzioni e le cartelle della soluzione<br />-Gestione configurazione soluzione<br />-Gestione elemento<br />-Soluzioni progetto singolo e più progetti<br />-Finestra di progettazione applicazione (proprietà del progetto semplificata)<br />-Aggiungi riferimento Web<br />-Aggiungi riferimento al servizio<br />Progetto singolo<br />-Tipi di progetto di sito Web<br />: Progetti di applicazione web|  
|Compilazione|-Istruzioni di compilazione personalizzate nell'IDE<br />-Pre-compilazione per la protezione di proprietà intellettuale (IP)<br />-La firma del codice<br />     MSBuild|  
|Editor|-(Ricerca unificata, la definizione dell'origine, ereditarietà) di strumenti di esplorazione del codice<br />-Navigazione codice<br />-IntelliSense<br />-Degli smart tag<br />-Refactoring<br />-Elenco<br />-Filtro IntelliSense<br />-   **Definizione di codice** finestra|  
|Designer|-Progettazione Windows Presentation Foundation<br />-Windows Form Designer<br />-Finestra di progettazione e web Editor HTML|  
|Dati|-   **Esplora server** (semplificato: solo i dati). Vedere la nota 1.<br />-   **Origini dati** finestra<br />-Set completo di controlli dati<br />: Editor XML<br />-Data binding all'origine dati locale (. MDF o. MDB)<br />-L'associazione dati oggetto<br />-Dati l'associazione al servizio Web<br />-Data binding al server di database locale<br />-Data binding al server di database remoto<br />-Strumenti DDL per i dati remoti<br />-   **Esplora server** estendibilità ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] esempi)|  
|Debugger|-Debug locale. Vedere la nota 2.<br />-Il debug gestito<br />-Debug locale<br />-Connetti a processo locale<br />-Connetti a processo remoto<br />-Delegato anonimo<br />-Domini applicazione<br />-Debug ASPX<br />-Gli attributi<br />-Interrompere la valutazione con Func<br />-I punti di interruzione<br />-Vincoli punto di interruzione<br />-Stack di chiamate<br />-   **Comando** finestra<br />-Debug Cross-thread<br />-I suggerimenti dati<br />-Visualizzatore dati<br />-Supporto del debugger per assistenti al debug gestiti (MDA)<br />-Supporto del debugger per server d'inoltro<br />-Supporto DTEEvents per OTB<br />-Gestore di JMC istruzioni<br />-Test AppID debugger (DBGCLR)<br />-Profilo debugger<br />-Del debugger strumenti e opzioni<br />-Debug iteratore<br />-Valutazione delle espressioni fase di progettazione<br />-C# l'analizzatore di espressioni<br />-Disassembly<br />-Modifica e continuazione<br />-Windows dell'analizzatore di espressioni expression (espressioni di controllo, variabili locali, Auto)<br />-Supporto eccezioni<br />: Eccezioni<br />-Esecuzione<br />- Generics<br />-Recupero origine corretta<br />-Debug/Cluster HPC<br />-Integrato debug multilingue<br />-Debug interoperabilità<br />Debug just-in-time<br />-Debug locale<br />-Il debug gestito<br />-Controllo manuale (finestra processi)<br />-Memoria<br />-Supporto miniDump<br />-I moduli<br />-Debug multiprocesso<br />-Debug nativo<br />-Supporto del motore di debug nuovo<br />-Il debug del codice ottimizzato<br />-La finestra di output applicazione di filtri<br />-Processo di hosting per il debug gestito<br />-Processi<br />-Controllo immediato<br />-Registri<br />-Registri nello stack<br />-Debug remote<br />-I valori restituiti<br />: Il debug degli script<br />-Supporto del servizio origine<br />-Sicurezza<br />Side-by-side<br />-SQL<br />: Server di simboli<br />-Punti di traccia<br />-Thread<br />-Visualizzazioni<br />-Debugger di extensible Stylesheet Language Transformations (XSLT)|  
|Supporto a 64 bit|-debug a 64 bit per codice gestito e nativo, tutte le lingue<br />-supporto x64 nativo|  
|Controllo del codice sorgente (SCC)|-Integrazione di controllo del codice sorgente di base. Vedere la nota 3.<br />-Strumenti e le opzioni di verifica|  
|Estendibilità|-Utilizzo VSPackage e MEF componenti|  
  
## <a name="notes"></a>Note  
  
#### <a name="1-data-tools"></a>1. Strumenti dati  
 La shell integrata include gli strumenti di sviluppo di database, ad esempio semplificato e al supporto di estendibilità dati **Esplora**. Tuttavia, SQL Server Express, SQL Reporting e Crystal Reports non sono inclusi nella shell integrata.  
  
#### <a name="2-debugging-support"></a>2. Supporto per il debug  
 La shell integrata include lo stesso motore di debug che è incluso nella versione Community di Visual Studio. Il motore di debug include il debugger per codice gestito e la funzionalità correlate, comune come eseguire, collegamento, impostare punti di interruzione, modifica e continuazione e altri utenti. Tuttavia, il motore di debug non supporta il debug di database di SQL Server.  
  
 Anche se il supporto per il debug nativo è incluso nel pacchetto di base del debugger, non è possibile estendere in modo da supportare linguaggi aggiuntivi.  
  
#### <a name="3-source-code-control-integration"></a>3. Integrazione del controllo del codice sorgente  
 La shell integrata fornisce API per l'implementazione del controllo del codice sorgente (SCC) e per fornire il controllo origine comune MSSCCI basato su componenti di integrazione.  
  
 Sebbene l'integrazione di controllo del codice sorgente non è una funzionalità dell'edizione di Visual Studio Pro regolare, integrazione di controllo del codice sorgente viene fornito nella shell integrata.  
  
#### <a name="4-build-support"></a>4. Supporto per la compilazione  
 La shell integrata fornisce supporto per la compilazione. È possibile trovare informazioni sulle compilazioni nel [di riferimento su MSBuild](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Funzionalità non incluse nella Shell integrata  
 Di seguito è riportato un elenco delle funzionalità che non sono inclusi nella shell integrata:  
  
-   Progettazione classi  
  
-   [Protezione preEmptive - Dotfuscator](../ide/dotfuscator/index.md)  
  
-   Funzionalità del linguaggio  
  
-   VSHost  
  
-   Nessuna lingua di Visual Studio o i relativi modelli di progetto associato o i modelli di progetto, sono inclusi nella shell integrata. Nessuna implementazione specifica del linguaggio di altre funzionalità sono inclusa, per i frammenti di codice di esempio Visual Basic.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)