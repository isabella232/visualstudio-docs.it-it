---
title: Concetti di base del progetto Web | Microsoft Docs
description: Informazioni dettagliate interne sul funzionamento dei progetti Web in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bf16582cdc9bba6529d237d74d56ebded299fb9
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487920"
---
# <a name="web-project-essentials"></a>Nozioni fondamentali sui progetti Web
I progetti Web creano applicazioni Web. È possibile utilizzare un progetto Web per creare un'applicazione Web con pagine Web Smart. Una pagina Web intelligente dispone di codice sul lato server che esegue il rendering della pagina Web su richiesta.

 Utilizzando i linguaggi di programmazione tradizionali, ad esempio [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] , è possibile creare pagine Web intelligenti per raccogliere ed elaborare informazioni da un utente, archiviarle in un database e così via.

- Il modello code-behind associa i file di codice sorgente dipendenti alle pagine Web con estensione. aspx o. asmx. Ad esempio, Hello. aspx potrebbe avere il file di codice sorgente dipendente hello.aspx.cs.

- Il codice lato server associato a una pagina Web Smart viene compilato in un file eseguibile che si trova nella cartella/bin del sito Web.

- I file di codice sorgente aggiuntivi, ad esempio le classi helper non associate a una pagina Web specifica, si trovano nella cartella sito Web/App_Code.

  - Un progetto di sito Web (WSP) genera un file eseguibile per ogni pagina Web intelligente. I file eseguibili aggiuntivi vengono generati da qualsiasi file di codice sorgente nella cartella/App_Code.

  - Un progetto di applicazione Web (WAP) produce un singolo file eseguibile che combina il codice per tutte le pagine Web intelligenti, oltre a tutti i file di origine nella cartella/App_Code.

- Il file di soluzione per un progetto Web si trova separatamente dal sito Web stesso. Per impostazione predefinita, i file di soluzione si trovano in \Documents and Settings \\ *Accountpersonale*\My Documents \\ *\<Visual Studio ####>* \projects \\ *YourWebSite*.

  > [!NOTE]
  > Se si desidera che il file di soluzione venga mantenuto nel sito Web, è sufficiente spostarlo e riaprirlo.

- Se si apre un sito Web in cui non è presente alcun file di soluzione in Visual Studio, viene automaticamente generato un nuovo file di soluzione.

- I progetti Web non hanno file di progetto. Le informazioni sul progetto vengono archiviate nel file della soluzione, nel file di web.config e altrove.

- Se si aggiungono proprietà globali a un progetto Web, viene creato automaticamente un file di archiviazione nella cartella della soluzione del progetto Web.

- Una pagina Web intelligente può essere associata a un linguaggio di programmazione lato server usando la direttiva di pagina o il \<script runat="server"> tag.

- Inoltre, le pagine Web possono avere un numero qualsiasi di blocchi di scripting sul lato client scritti in qualsiasi linguaggio di scripting.

- Un sistema di progetto di sito Web viene implementato aggiungendo modelli di progetto e di elemento e la registrazione al [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto.

- Un sistema WAP viene implementato come sottotipo di progetto, detto anche versione del progetto. Il [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto viene aromatizzato dal sottotipo WAP per creare il sistema WAP. Per altre informazioni sui sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).

- Una pagina Web intelligente combina il codice HTML con un linguaggio di programmazione lato server. Il linguaggio del lato server è denominato linguaggio contenuto. Per supportare un linguaggio contenuto, il sistema del progetto Web deve implementare la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> famiglia di interfacce.

  - Per supportare il linguaggio contenuto in un editor, il servizio di linguaggio HTML deve rinviare la visualizzazione del codice della lingua contenuto a un servizio di linguaggio contenuto.

  - I marcatori di errore (linee ondulate indicano rosso) devono sempre essere creati nel buffer primario dell'editor di codice.

## <a name="see-also"></a>Vedere anche
- [Progetti Web](../../extensibility/internals/web-projects.md)
