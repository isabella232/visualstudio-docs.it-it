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
ms.openlocfilehash: 68934fb67ff1bd4f17507ac4af72c0aaf113816c6b6ff643c9f49bbb40698e81
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414688"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Linee guida aggiuntive sul controllo del codice sorgente per progetti ed editor
Per supportare il controllo del codice sorgente, sono disponibili alcune linee guida a cui devono attenersi i progetti e gli editor.

## <a name="guidelines"></a>Indicazioni
 Anche il progetto o l'editor deve eseguire le operazioni seguenti per supportare il controllo del codice sorgente:

|Area|Project|Editor|Dettagli|
|----------|-------------|------------|-------------|
|Copie private dei file|X||L'ambiente supporta copie private dei file. Ciò significa che ogni persona integrata nel progetto ha la propria copia privata dei file in tale progetto.|
|Persistenza ANSI/Unicode|X|X|Se si scrive il codice di persistenza, rendere persistenti i file nel formato ANSI perché la maggior parte dei programmi di controllo del codice sorgente attualmente non supporta Unicode.|
|Enumerare i file|X||Il progetto deve contenere un elenco specifico di tutti i file al suo interno e deve essere in grado di enumerare l'elenco di file usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Il progetto deve inoltre esporre i nomi degli elementi tramite la relativa implementazione e supportare la ricerca dei nomi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> (inclusi i file speciali) tramite la relativa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementazione.|
|Formato testo|X|X|Quando possibile, i file devono essere in formato testo per supportare l'unione di versioni diverse. I file che non sono in formato testo non possono essere uniti con altre versioni del file in un secondo momento. Il formato di testo preferito è XML.|
|Basato sui riferimenti|X||I progetti basati su riferimenti sono immediatamente supportati nel controllo del codice sorgente. Tuttavia, i progetti basati su directory sono supportati anche dal controllo del codice sorgente, purché il progetto possa produrre un elenco dei file su richiesta, indipendentemente dal fatto che tali file esistano su disco. Quando si apre un progetto dal controllo del codice sorgente, il file di progetto viene arrestato prima di qualsiasi file.|
|Rendere persistenti oggetti e proprietà in ordine prevedibile|X|X|Rendere persistenti i file in un ordine prevedibile, ad esempio in ordine alfabetico, per facilitare l'unione.|
|Ricarica|X|X|Quando un file viene modificato su disco, l'editor deve essere in grado di ricaricarlo. Quando si partecipa al controllo del codice sorgente, l'ambiente ricarica automaticamente i dati chiamando l'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> di . Il caso di ricaricamento più difficile è quando si verifica un'estrazione quando si chiama IVsQueryEditQuerySave:: <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e si elaborano le informazioni. Tuttavia, il codice di ricaricamento deve essere in grado di essere eseguito in questa situazione.<br /><br /> L'ambiente ricarica automaticamente i file di progetto. Tuttavia, un progetto deve implementare se dispone di gerarchie annidate per supportare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> il ricaricamento dei file di progetto annidati.|

## <a name="see-also"></a>Vedi anche
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
