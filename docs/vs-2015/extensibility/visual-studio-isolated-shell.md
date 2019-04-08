---
title: Visual Studio Isolated Shell | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59ecd079b7e95d86ab85eb9e5e36fcf938f99f58
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967608"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La shell isolata di Visual Studio consente di creare applicazioni autonome che è possono eseguire side-by-side con altre versioni di Visual Studio. È usato principalmente per ospitare strumenti specializzati che è possono usare i servizi di Visual Studio ma anche avere un aspetto personalizzato e personalizzazione. Funzionalità di Visual Studio e gruppi di comandi di menu possono facilmente essere attivati e disattivata. I titoli di applicazioni, applicazione icone e schermate iniziali sono completamente personalizzabili. Per un elenco delle funzionalità personalizzabili, vedere [personalizzazione della Shell isolata](../extensibility/customizing-the-isolated-shell.md).  
  
 Per usare un progetto di shell isolata, è necessario installare Visual Studio SDK. A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Per creare un'applicazione shell isolata, iniziare con un progetto di Visual Studio Shell isolata. Questo progetto contiene tutto ciò che occorre per sviluppare e testare un'applicazione shell isolata. Quando si è pronti a scrivere il programma di installazione che consente di distribuire l'applicazione, è necessario ottenere il pacchetto ridistribuibile di shell isolata dal [Microsoft Visual Studio Shell (Isolated) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Prima di poter accedere il pacchetto ridistribuibile di shell isolata, verrà richiesto a un cliente breve sondaggio.  Dopo aver compilato il sondaggio, si verrà indirizzati a una pagina con collegamenti ai download del pacchetto ridistribuibile Visual Studio Connect.  È possibile trovare collegamenti per il download nelle visite successive al sito di Visual Studio Connect con la **programmi &#124; VISUAL STUDIO 2015 integrata e isolata SHELL** scheda.  
  
> [!NOTE]
>  Per altre informazioni su come distribuire un'applicazione basata su shell isolata, vedere [procedura dettagliata: Creazione di una semplice applicazione Shell isolata](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Utilizzo della shell isolata  
 Un'applicazione shell isolata di Visual Studio ha accesso completo a servizi di Visual Studio e supporta la personalizzazione particolare e personalizzazione. Esistono diversi modi per personalizzare un'applicazione shell isolata:  
  
- È possibile usare i pacchetti VSPackage e Managed Extensibility Framework (MEF) parti di componente per estendere un'applicazione shell isolata esattamente come utilizzarli in un'altra estensione di Visual Studio. Per altre informazioni, vedere [estensione della Shell isolata](../extensibility/extending-the-isolated-shell.md).  
  
- Per rendere le funzionalità di Visual Studio e gruppi di comandi di menu disponibili o non è disponibile, aggiornare il file con estensione vsct nel progetto dell'interfaccia utente dell'applicazione.  
  
- Per rimuovere **opzioni** pagine o altri componenti di Visual Studio shell dell'applicazione, aggiornare il file con estensione pkgundef dell'applicazione.  
  
- Per modificare il comportamento della shell o altri aspetti dell'aspetto, aggiornare il file pkgdef dell'applicazione.  
  
- Alcuni aspetti della shell possono essere specificati anche quando l'applicazione viene avviata. A tale scopo, aggiornare i parametri nella chiamata al punto di ingresso di avvio del appenvstub.dll.  
  
  Per altre informazioni sui diversi elementi che è possibile personalizzare, vedere [gli elementi della Shell isolata](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Funzionalità standard della Shell isolata  
 Le funzionalità seguenti sono standard per tutte le edizioni di Visual Studio.  
  
|Categoria funzionalità|Funzionalità|  
|----------------------|-------------|  
|Funzionalità dell'IDE|Le impostazioni di importazione/esportazione<br /><br /> Programma di installazione di controllo della casella degli strumenti<br /><br /> Elenco attività ed elenco errori<br /><br /> Finestra di output<br /><br /> Pagina iniziale<br /><br /> Finestra Proprietà<br /><br /> Casella degli strumenti<br /><br /> Esplora soluzioni<br /><br /> Finestra Segnalibro<br /><br /> Visualizzazione classi<br /><br /> Visualizzatore oggetti<br /><br /> Finestra di comando<br /><br /> Struttura documento<br /><br /> Visualizzazione risorse<br /><br /> Strumento esterno<br /><br /> Windows Communication Foundation (WCF) Aggiungi riferimento al servizio<br /><br /> Language Integrated Query (LINQ) supporto|  
|Editor/Designer|Esplorazione degli strumenti (ricerca unificata, definizione dell'origine, ereditarietà) del codice<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Gestione frammenti di codice<br /><br /> Frammenti di codice<br /><br /> Refactoring<br /><br /> Riformatta il listato<br /><br /> Filtro di IntelliSense<br /><br /> Finestra Definizione codice<br /><br /> Progettazione applicazioni<br /><br /> Progettazione Windows Form<br /><br /> Windows Presentation Foundation (WPF) Designer|  
|Debug|Analizzatore di espressioni C#<br /><br /> Il debug locale<br /><br /> Il debug gestito<br /><br /> Modifica e continuazione<br /><br /> Debug di cross-thread<br /><br /> Visualizzazioni<br /><br /> DataTips<br /><br /> Debug nativo<br /><br /> Debug degli script<br /><br /> Debug di interoperabilità<br /><br /> Debug Just-in-time (JIT)<br /><br /> Debug multiprocesso<br /><br /> Debug XSLT<br /><br /> Connetti a processo locale<br /><br /> Punti di traccia<br /><br /> Vincoli di punto di interruzione|  
|Dati|Esplora server (semplificato - solo i dati)<br /><br /> Eseguire l'associazione dati ai dati locali (. File MDF o. MDB)<br /><br /> Associare i dati oggetto<br /><br /> Associare i dati al servizio Web<br /><br /> Set completo di controlli dati<br /><br /> Editor XML<br /><br /> Data Binding al server di database locale<br /><br /> Finestra Origini dati|  
|Web|Editor HTML<br /><br /> Web browser<br /><br /> Progettazione Web Form<br /><br /> Progetto di sito Web<br /><br /> Progetto di applicazione Web|  
|Estendibilità|Utilizza i componenti MEF e i pacchetti VSPackage|  
  
## <a name="see-also"></a>Vedere anche  
 [Shell (isolata o integrata)](../extensibility/shell-isolated-or-integrated.md)
