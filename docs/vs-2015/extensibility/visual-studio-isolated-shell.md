---
title: Shell isolata di Visual Studio | Microsoft Docs
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
ms.openlocfilehash: 36491d9d590a45256e297654f71652ab5de5cd98
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299720"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La shell isolata di Visual Studio consente di creare applicazioni autonome che possono essere eseguite side-by-side con altre versioni di Visual Studio. Viene usato principalmente per ospitare strumenti specializzati che possono usare i servizi di Visual Studio, ma anche un aspetto personalizzato e una personalizzazione. Le funzionalità di Visual Studio e i gruppi di comandi di menu possono essere facilmente attivati e disattivati. I titoli delle applicazioni, le icone delle applicazioni e le schermate iniziali sono completamente personalizzabili. Per un elenco delle funzionalità personalizzabili, vedere [personalizzazione della shell isolata](../extensibility/customizing-the-isolated-shell.md).  
  
 Per usare un progetto shell isolata, è necessario installare Visual Studio SDK. A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Per creare un'applicazione shell isolata, iniziare con un progetto di Visual Studio Shell isolata. Questo progetto contiene tutto ciò che è necessario per sviluppare e testare un'applicazione shell isolata. Quando si è pronti a scrivere il programma di installazione che distribuisce l'applicazione, è necessario ottenere il pacchetto ridistribuibile di shell isolata da [Microsoft Visual Studio Shell (isolated) pacchetto ridistribuibile](https://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
> Prima di poter accedere al pacchetto ridistribuibile con isolamento Shell, verrà richiesto di compilare un breve sondaggio del cliente.  Dopo aver compilato il sondaggio, si verrà indirizzati a una pagina di Visual Studio Connect con i collegamenti di download dei pacchetti ridistribuibili.  È possibile trovare i collegamenti per il download nelle visite successive al sito di Visual Studio Connect nella scheda  **&#124; programmi Visual Studio 2015 Integrated and isolated shell** .  
  
> [!NOTE]
> Per altre informazioni su come distribuire un'applicazione basata su Shell isolata, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Uso della shell isolata  
 Un'applicazione shell isolata di Visual Studio ha accesso completo ai servizi di Visual Studio e supporta personalizzazione e personalizzazione speciali. È possibile personalizzare un'applicazione shell isolata in diversi modi:  
  
- È possibile usare le parti dei componenti VSPackage e Managed Extensibility Framework (MEF) per estendere un'applicazione shell isolata così come si userebbe in qualsiasi altra estensione di Visual Studio. Per ulteriori informazioni, vedere [estensione della shell isolata](../extensibility/extending-the-isolated-shell.md).  
  
- Per rendere disponibili o non disponibili le funzionalità di Visual Studio e i gruppi di comandi di menu, aggiornare il file con estensione vsct nel progetto dell'interfaccia utente (UI) dell'applicazione.  
  
- Per rimuovere le pagine di **Opzioni** o altri componenti della shell di Visual Studio dall'applicazione, aggiornare il file con estensione pkgundef dell'applicazione.  
  
- Per modificare altri aspetti dell'aspetto o del comportamento della shell, aggiornare il file con estensione pkgdef dell'applicazione.  
  
- Quando l'applicazione viene avviata, è inoltre possibile specificare alcuni aspetti della shell. A tale scopo, aggiornare i parametri nella chiamata al punto di ingresso iniziale di appenvstub. dll.  
  
  Per ulteriori informazioni sui diversi elementi che è possibile personalizzare, vedere [elementi della shell isolata](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Funzionalità standard della shell isolata  
 Le funzionalità seguenti sono standard per tutte le edizioni di Visual Studio.  
  
|Categoria funzionalità|Funzionalità|  
|----------------------|-------------|  
|Funzionalità IDE|Impostazioni di importazione/esportazione<br /><br /> Programma di installazione controllo della casella degli strumenti<br /><br /> Elenco attività & Elenco errori<br /><br /> Output (finestra)<br /><br /> Pagina iniziale<br /><br /> Finestra Proprietà<br /><br /> Casella degli strumenti<br /><br /> Esplora soluzioni<br /><br /> Finestra Segnalibro<br /><br /> Visualizzazione classi<br /><br /> Visualizzatore oggetti<br /><br /> Finestra di comando<br /><br /> Struttura documento<br /><br /> Visualizzazione risorse<br /><br /> Strumento esterno<br /><br /> Aggiungi riferimento al servizio Windows Communication Foundation (WCF)<br /><br /> Supporto LINQ (Language Integrated Query)|  
|Editor/finestra di progettazione|Strumenti di esplorazione del codice (ricerca unificata, definizione di origine, ereditarietà)<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Gestione frammenti di codice<br /><br /> Frammenti di codice<br /><br /> Refactoring<br /><br /> Elenco di belle<br /><br /> Filtro IntelliSense<br /><br /> Finestra Definizione codice<br /><br /> Progettazione applicazioni<br /><br /> Progettazione Windows Form<br /><br /> Progettazione Windows Presentation Foundation (WPF)|  
|Debug|C#Analizzatore di espressioni<br /><br /> Debug locale<br /><br /> Debug gestito<br /><br /> Modifica e continuazione<br /><br /> Debug tra thread<br /><br /> Visualizzazioni<br /><br /> DataTips<br /><br /> Debug nativo<br /><br /> Debug di script<br /><br /> Debug di interoperabilità<br /><br /> Debug JIT (just-in-Time)<br /><br /> Debug di più processi<br /><br /> Debug XSLT<br /><br /> Connetti al processo locale<br /><br /> Punti di traccia<br /><br /> Vincoli del punto di interruzione|  
|Dati|Esplora server (solo dati semplificati)<br /><br /> Data binding a dati locali (. MDF o. MDB<br /><br /> Associa dati a oggetto<br /><br /> Associazione dati al servizio Web<br /><br /> Set completo di controlli dati<br /><br /> Editor XML<br /><br /> Associa dati a server di database locale<br /><br /> Finestra Origini dati|  
|Web|Editor HTML<br /><br /> Web browser<br /><br /> Progettazione Web Form<br /><br /> Progetto sito Web<br /><br /> Progetto di applicazione Web|  
|Estendibilità|Utilizza VSPackage e componenti MEF|  
  
## <a name="see-also"></a>Vedere anche  
 [Shell (isolata o integrata)](../extensibility/shell-isolated-or-integrated.md)
