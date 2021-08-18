---
title: Informazioni rapide in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sul supporto per l'operazione informazioni rapide di IntelliSense per la visualizzazione di informazioni su un identificatore.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2c8a9b09ac8ad7391336816f4416a25ebd98484badb21ff81e1ec4604784eead
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414467"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Informazioni rapide in un servizio di linguaggio legacy
Informazioni rapide di IntelliSense visualizza informazioni su un identificatore nell'origine quando l'utente posiziona il cursore nell'identificatore e seleziona Informazioni rapide dal menu **IntelliSense** o posiziona il cursore del mouse sull'identificatore.  In questo modo viene visualizzata una descrizione comando con informazioni sull'identificatore. Queste informazioni sono in genere costituite dal tipo di identificatore. Quando il motore di debug è attivo, queste informazioni potrebbero includere il valore corrente. Il motore di debug fornisce valori di espressione , mentre il servizio di linguaggio gestisce solo gli identificatori.

 I servizi di linguaggio legacy vengono implementati come parte di un PACCHETTO VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni, vedere [Procedura dettagliata: visualizzazione delle descrizioni comando di Informazioni rapide.](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare le nuove funzionalità dell'editor.

 Le classi del servizio di linguaggio MPF (Managed Package Framework) offrono supporto completo per la visualizzazione della descrizione comando Informazioni rapide di IntelliSense. È necessario solo specificare il testo da visualizzare e abilitare la funzionalità informazioni rapide.

 Il testo da visualizzare viene ottenuto chiamando il parser del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo con il valore del motivo di analisi <xref:Microsoft.VisualStudio.Package.ParseReason> . Questo motivo indica al parser di ottenere le informazioni sul tipo (o qualsiasi elemento appropriato da visualizzare nella descrizione comando Informazioni rapide) per l'identificatore nella posizione specificata <xref:Microsoft.VisualStudio.Package.ParseRequest> nell'oggetto . <xref:Microsoft.VisualStudio.Package.ParseRequest>L'oggetto è ciò che è stato passato al metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> .

 Il parser deve analizzare tutti gli elementi fino alla posizione nell'oggetto per <xref:Microsoft.VisualStudio.Package.ParseRequest> determinare i tipi di tutti gli identificatori. Il parser deve quindi ottenere l'identificatore nel percorso della richiesta di analisi. Infine, il parser deve passare i dati della descrizione comando associati a tale identificatore all'oggetto in modo che l'oggetto possa restituire <xref:Microsoft.VisualStudio.Package.AuthoringScope> il testo dal metodo <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> .

## <a name="enabling-the-quick-info-feature"></a>Abilitazione della funzionalità Informazioni rapide
 Per abilitare la funzionalità Informazioni rapide, è necessario impostare `CodeSense` i parametri denominati e di `QuickInfo` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Questi attributi impostano <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> le proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> e .

## <a name="implementing-the-quick-info-feature"></a>Implementazione della funzionalità Informazioni rapide
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe gestisce l'operazione informazioni rapide di IntelliSense. Quando la classe riceve il comando, la classe chiama il metodo con il motivo di analisi e la posizione del punto di ingresso al momento dell'invio <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando. Il parser del metodo deve quindi analizzare l'origine fino alla posizione specificata e quindi analizzare l'identificatore nella posizione specificata per determinare cosa visualizzare nella descrizione comando <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Informazioni rapide.

 La maggior parte dei parser esegue un'analisi iniziale dell'intero file di origine e archivia i risultati in un albero di analisi. L'analisi completa viene eseguita quando <xref:Microsoft.VisualStudio.Package.ParseReason> viene passato al metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Altri tipi di analisi possono quindi usare l'albero di analisi per ottenere le informazioni desiderate.

 Ad esempio, il valore del motivo di analisi di può trovare l'identificatore nel percorso di origine e cercarlo nell'albero di analisi <xref:Microsoft.VisualStudio.Package.ParseReason> per ottenere le informazioni sul tipo. Queste informazioni sul tipo vengono quindi passate alla <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe e restituite dal <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metodo .
