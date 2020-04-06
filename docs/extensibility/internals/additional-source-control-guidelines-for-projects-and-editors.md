---
title: Linee guida aggiuntive per il controllo del codice sorgente per progetti ed editor . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181f6c10ff7ce95cd3a37151f117353d1bb47d41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710114"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Linee guida aggiuntive sul controllo del codice sorgente per progetti ed editorAdditional source control guidelines for projects and editors
Esistono una serie di linee guida che i progetti e gli editor devono rispettare per supportare il controllo del codice sorgente.

## <a name="guidelines"></a>Indicazioni
 Il progetto o l'editor deve inoltre eseguire le operazioni seguenti per supportare il controllo del codice sorgente:Your project or editor should also do the following to support source control:

|Area|Project|Editor|Dettagli|
|----------|-------------|------------|-------------|
|Copie private dei file|X||L'ambiente supporta copie private dei file. Ovvero, ogni persona arruolata nel progetto ha la propria copia privata dei file in quel progetto.|
|Persistenza ANSI/Unicode|X|X|Se si scrive il codice di persistenza, rendere persistenti i file nel modulo ANSI perché la maggior parte dei programmi di controllo del codice sorgente non supporta attualmente Unicode.If you write the persistence code, persist files in the ANSI form because most the source control programs do not currently support Unicode.|
|Enumerazione dei file|X||Il progetto deve contenere un elenco specifico di tutti i file al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> suo interno e deve essere in grado di enumerare l'elenco di file utilizzando il (VSH_PROPID_First_Child/Next_Sibling). Il progetto deve inoltre esporre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> i nomi degli elementi tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> l'implementazione e supportare la ricerca dei nomi (inclusi i file speciali) tramite l'implementazione.|
|Formato testo|X|X|Quando possibile, i file devono essere in formato testo per supportare l'unione di versioni diverse. I file che non sono in formato testo non possono essere uniti ad altre versioni del file in un secondo momento. Il formato di testo preferito è XML.|
|Basato su riferimento|X||I progetti basati su riferimenti sono facilmente supportati nel controllo del codice sorgente. Tuttavia, i progetti basati su directory sono supportati anche dal controllo del codice sorgente, purché il progetto possa produrre un elenco dei relativi file su richiesta, indipendentemente dal fatto che tali file esistano sul disco. Quando si apre un progetto dal controllo del codice sorgente, il file di progetto viene portato giù prima di uno qualsiasi dei relativi file.|
|Rendere persistenti oggetti e proprietà in ordine prevedibilePersist objects and properties in predictable order|X|X|Rendere persistenti i file in un ordine prevedibile, ad esempio in ordine alfabetico, per facilitare l'unione.|
|Ricarica|X|X|Quando un file viene modificato su disco, l'editor deve essere in grado di ricaricarlo. Quando si partecipa al controllo del codice sorgente, l'ambiente ricarica i dati chiamando l'implementazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Il caso di ricaricamento più difficile è quando si verifica un'estrazione quando si è chiamato IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e si elaborano le informazioni. Tuttavia, il codice di ricarica deve essere in grado di essere eseguito in questa situazione.<br /><br /> L'ambiente ricarica automaticamente i file di progetto. Tuttavia, un <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> progetto deve implementare se dispone di gerarchie annidate per supportare il ricaricamento dei file di progetto annidati.|

## <a name="see-also"></a>Vedere anche
- [Supporto del controllo del codice sorgenteSupport source control](../../extensibility/internals/supporting-source-control.md)
