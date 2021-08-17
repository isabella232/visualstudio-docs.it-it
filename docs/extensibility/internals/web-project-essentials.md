---
title: Web Project Essentials | Microsoft Docs
description: Informazioni dettagliate interne sul funzionamento dei progetti Web in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 54888223ec789babd4af15c6b675a138bdb81520
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042010"
---
# <a name="web-project-essentials"></a>Nozioni fondamentali sui progetti Web
I progetti Web creano applicazioni Web. È possibile usare un progetto Web per creare un'applicazione Web con pagine Web intelligenti. Una pagina Web intelligente include codice lato server che esegue il rendering della pagina Web su richiesta.

 Usando i linguaggi di programmazione tradizionali, ad esempio o , è possibile creare pagine Web intelligenti per raccogliere ed elaborare informazioni da un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] utente, archiviarli in un database e così via.

- Il modello code-behind associa i file di codice sorgente dipendenti alle pagine Web con estensione aspx o asmx. Ad esempio, hello.aspx potrebbe avere il file di codice sorgente dipendente hello.aspx.cs.

- Il codice lato server associato a una pagina Web intelligente viene compilato in un file eseguibile che si trova nella cartella /bin del sito Web.

- Altri file di codice sorgente, ad esempio classi helper non associate a una pagina Web specifica, si trovano nella cartella /App_Code Web.

  - Un progetto di sito Web (WSP) genera un file eseguibile per ogni pagina Web intelligente. I file eseguibili aggiuntivi vengono generati da qualsiasi file di codice sorgente nella cartella /App_Code.

  - Un progetto di applicazione Web (WAP) produce un singolo file eseguibile che combina il codice per tutte le pagine Web intelligenti, nonché tutti i file di origine nella cartella /App_Code.

- Il file di soluzione per un progetto Web si trova separatamente dal sito Web stesso. Per impostazione predefinita, i file della soluzione si trovano in \Documents e Impostazioni \\ *YourAccount*\Documenti \\ *\<Visual Studio ####>* \Projects \\ *YourWebSite*.

  > [!NOTE]
  > Se si vuole mantenere il file della soluzione con il sito Web, è sufficiente spostarlo e riaprirlo.

- Se si apre un sito Web senza file di soluzione Visual Studio, viene generato automaticamente un nuovo file di soluzione.

- I progetti Web non hanno file di progetto. Project le informazioni vengono archiviate nel file di soluzione, nel file web.config e altrove.

- L'aggiunta di proprietà globali a un progetto Web crea automaticamente un file di archiviazione nella cartella della soluzione del progetto Web.

- Una pagina Web intelligente può essere associata a un linguaggio di programmazione lato server usando la direttiva Page o il \<script runat="server"> tag .

- Inoltre, le pagine Web possono avere un numero qualsiasi di blocchi di scripting sul lato client scritti in qualsiasi linguaggio di scripting.

- Un sistema di progetto di sito Web viene implementato aggiungendo modelli di progetto e di elemento e la registrazione al [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto.

- Un sistema WAP viene implementato come sottotipo di progetto, denominato anche progetto flavor. Il [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto viene creato dal sottotipo WAP per creare il sistema WAP. Per altre informazioni sui sottotipi di progetto, [vedere Project sottotipi](../../extensibility/internals/project-subtypes.md).

- Una pagina Web intelligente combina html con un linguaggio di programmazione lato server. Il linguaggio sul lato server è denominato linguaggio indipendente. Per supportare un linguaggio indipendente, il sistema del progetto Web deve implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> la famiglia di interfacce.

  - Per supportare il linguaggio contenuto in un editor, il servizio di linguaggio HTML deve rinviare la visualizzazione del codice del linguaggio contenuto a un servizio di linguaggio indipendente.

  - I marcatori di errore (squigglies rossi) devono sempre essere creati nel buffer primario dell'editor di codice.

## <a name="see-also"></a>Vedi anche
- [Progetti Web](../../extensibility/internals/web-projects.md)
