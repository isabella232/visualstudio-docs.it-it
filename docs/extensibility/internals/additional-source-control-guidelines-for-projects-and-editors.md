---
title: Linee guida per il controllo del codice sorgente per progetti ed editor
description: Informazioni sulle linee guida che i progetti e gli editor devono rispettare per supportare il controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8bdd0439b51f0dc1a636eafb5732223316bc1226
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711767"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Linee guida aggiuntive per il controllo del codice sorgente per progetti ed editor
Esistono alcune linee guida a cui devono attenersi progetti ed editor per supportare il controllo del codice sorgente.

## <a name="guidelines"></a>Indicazioni
 Il progetto o l'editor deve anche eseguire le operazioni seguenti per supportare il controllo del codice sorgente:

|Area|Project|Editor|Dettagli|
|----------|-------------|------------|-------------|
|Copie private dei file|X||L'ambiente supporta copie private di file. In altri, ogni persona integrata nel progetto ha la propria copia privata dei file in tale progetto.|
|Persistenza ANSI/Unicode|X|X|Se si scrive il codice di persistenza, rendere persistenti i file nel formato ANSI perché la maggior parte dei programmi di controllo del codice sorgente non supporta attualmente Unicode.|
|Enumerare i file|X||Il progetto deve contenere un elenco specifico di tutti i file al suo interno e deve essere in grado di enumerare l'elenco di file usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Il progetto deve anche esporre i nomi degli elementi tramite l'implementazione e supportare la ricerca dei nomi (inclusi i file <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> speciali) tramite la relativa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementazione.|
|Formato testo|X|X|Quando possibile, i file devono essere in formato testo per supportare l'unione di versioni diverse. I file non in formato testo non possono essere uniti ad altre versioni del file in un secondo momento. Il formato di testo preferito è XML.|
|Basato su riferimento|X||I progetti basati su riferimento sono facilmente supportati nel controllo del codice sorgente. Tuttavia, i progetti basati su directory sono supportati anche dal controllo del codice sorgente, purché il progetto possa produrre un elenco dei file su richiesta, indipendentemente dal fatto che tali file esistano su disco. Quando si apre un progetto dal controllo del codice sorgente, il file di progetto viene arrestato prima di qualsiasi file.|
|Rendere persistenti oggetti e proprietà in ordine stimabile|X|X|Rendere persistenti i file in un ordine prevedibile, ad esempio in ordine alfabetico, per facilitare l'unione.|
|Ricarica|X|X|Quando un file viene modificato su disco, l'editor deve essere in grado di ricaricarlo. Quando si partecipa al controllo del codice sorgente, l'ambiente ricarica automaticamente i dati chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> l'implementazione. Il caso di ricaricamento più difficile è quando si verifica un'estrazione quando si chiama IVsQueryEditQuerySave:: <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e si elaborano le informazioni. Tuttavia, il codice di ricaricamento deve essere in grado di essere eseguito in questa situazione.<br /><br /> L'ambiente ricarica automaticamente i file di progetto. Tuttavia, un progetto deve implementare se ha gerarchie annidate per supportare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> ricaricamento dei file di progetto annidati.|

## <a name="see-also"></a>Vedi anche
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
