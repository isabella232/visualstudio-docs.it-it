---
title: Informazioni di base sul progetto Web Documenti Microsoft
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
ms.openlocfilehash: 09e33248ca264fefa79a8d5d5fa5d0cfa3d2da1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703543"
---
# <a name="web-project-essentials"></a>Nozioni fondamentali sui progetti Web
I progetti Web creano applicazioni Web. È possibile utilizzare un progetto Web per creare un'applicazione Web con pagine Web intelligenti. Una pagina Web intelligente dispone di codice lato server che esegue il rendering della pagina Web su richiesta.

 Utilizzando i linguaggi di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]programmazione tradizionali, ad esempio o , è possibile creare pagine Web intelligenti per raccogliere ed elaborare informazioni da un utente, archiviarle in un database e così via.

- Il modello code-behind associa i file di codice sorgente dipendenti alle pagine Web con estensione aspx o asmx. Ad esempio, hello.aspx potrebbe avere il file di codice sorgente dipendente hello.aspx.cs.

- Il codice lato server associato a una pagina Web intelligente viene compilato in un file eseguibile che si trova nella cartella /bin del sito Web.

- I file di codice sorgente aggiuntivi, ad esempio le classi helper non associate a una pagina Web specifica, si trovano nella cartella /App_Code del sito Web.

  - Un progetto di sito Web (WSP) genera un file eseguibile per ogni pagina Web intelligente. Ulteriori file eseguibili vengono generati da qualsiasi file di codice sorgente nella cartella /App_Code.

  - Un progetto di applicazione Web (WAP) produce un singolo file eseguibile che combina il codice per tutte le pagine Web intelligenti, nonché tutti i file di origine nella cartella /App_Code.

- Il file di soluzione per un progetto Web si trova separatamente dal sito Web stesso. Per impostazione predefinita, i file\\della soluzione si trovano nel percorso "Documenti\\e impostazioni*AccountAccount"* di\\*\<Visual Studio .NET *Framework windows >"Progetti*sito Web".*

  > [!NOTE]
  > Se si desidera mantenere il file di soluzione con il sito Web, è sufficiente spostarlo e riaprirlo.

- Se si apre un sito Web che non dispone di alcun file di soluzione in Visual Studio, viene generato automaticamente un nuovo file di soluzione.

- I progetti Web non hanno file di progetto. Le informazioni sul progetto vengono archiviate nel file di soluzione, nel file web.config e altrove.

- L'aggiunta di proprietà globali a un progetto Web crea automaticamente un file di archiviazione nella cartella della soluzione del progetto Web.

- Una pagina Web intelligente può essere associata a un linguaggio \<di programmazione lato server utilizzando la direttiva Page o il tag script runat"server">.

- Inoltre, le pagine Web possono avere un numero qualsiasi di blocchi di script sul lato client scritti in qualsiasi linguaggio di scripting.

- Un sistema di progetto di sito Web viene implementato [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] aggiungendo modelli di progetto e elemento e la registrazione al progetto.

- Un sistema WAP è implementato come un sottotipo di progetto, chiamato anche sapore di progetto. Il [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto è aromatizzato dal sottotipo WAP per creare il sistema WAP. Per ulteriori informazioni sui sottotipi di progetto, vedere [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md).

- Una pagina Web intelligente combina HTML con un linguaggio di programmazione lato server. La lingua sul lato server è detta lingua contenuta. Per supportare un linguaggio indipendente, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> il sistema del progetto Web deve implementare la famiglia di interfacce.

  - Per supportare il linguaggio contenuto in un editor, il servizio di linguaggio HTML deve rinviare la visualizzazione del codice di linguaggio contenuto a un servizio di linguaggio contenuto.

  - I marcatori di errore (squigglies rossi) devono essere sempre creati nel buffer principale dell'editor di codice.

## <a name="see-also"></a>Vedere anche
- [Progetti Web](../../extensibility/internals/web-projects.md)
