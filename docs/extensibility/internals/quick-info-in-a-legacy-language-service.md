---
title: Informazioni rapide in un servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705935"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Informazioni rapide in un servizio di linguaggio legacy
Informazioni rapide IntelliSense Mostra informazioni su un identificatore nell'origine quando l'utente posiziona il punto di inserimento nell'identificatore e seleziona **Informazioni rapide** dal menu **IntelliSense** o tiene il cursore del mouse sull'identificatore. In questo modo una descrizione comandi viene visualizzata con informazioni sull'identificatore. Queste informazioni sono in genere costituite dal tipo di identificatore. Quando il motore di debug è attivo, queste informazioni potrebbero includere il valore corrente. Il motore di debug fornisce valori di espressione , mentre il servizio di linguaggio gestisce solo gli identificatori.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni, vedere [Procedura dettagliata: visualizzazione delle descrizioni comandi di informazioni rapide](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

 Le classi del servizio di linguaggio MPF (Managed Package Framework) forniscono il supporto completo per la visualizzazione della descrizione comandi Informazioni rapide di IntelliSense.The managed package framework (MPF) language service classes provide full support for displaying the IntelliSense Quick Info tool tip. Tutto quello che dovete fare è fornire il testo da visualizzare e attivare la funzione di informazioni rapide.

 Il testo da visualizzare viene ottenuto chiamando il parser <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.ParseReason>del metodo con un valore di motivo di analisi di . Questo motivo indica al parser di ottenere le informazioni sul tipo (o qualsiasi elemento appropriato per essere <xref:Microsoft.VisualStudio.Package.ParseRequest> visualizzato nella descrizione comando Informazioni rapide) per l'identificatore nella posizione specificata nell'oggetto. L'oggetto <xref:Microsoft.VisualStudio.Package.ParseRequest> è ciò <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> che è stato passato al metodo.

 Il parser deve analizzare tutti <xref:Microsoft.VisualStudio.Package.ParseRequest> gli elementi fino alla posizione nell'oggetto per determinare i tipi di tutti gli identificatori. Il parser deve quindi ottenere l'identificatore nel percorso della richiesta di analisi. Infine, il parser deve passare i dati della <xref:Microsoft.VisualStudio.Package.AuthoringScope> descrizione comandi associati a tale <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> identificatore all'oggetto in modo che l'oggetto possa restituire il testo dal metodo.

## <a name="enabling-the-quick-info-feature"></a>Attivazione della funzione Informazioni rapide
 Per attivare la funzione Informazioni `CodeSense` rapide, è necessario impostare i parametri e `QuickInfo` denominati <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>del file . Questi attributi <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> impostano le proprietà e <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> .

## <a name="implementing-the-quick-info-feature"></a>Implementazione della funzionalità Informazioni rapide
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe gestisce l'operazione di informazioni rapide di IntelliSense.The class handles the IntelliSense Quick Info operation. Quando <xref:Microsoft.VisualStudio.Package.ViewFilter> la classe <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> riceve il comando, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> la classe chiama <xref:Microsoft.VisualStudio.Package.ParseReason> il metodo con il motivo <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> di analisi e la posizione del punto di inserimento nel momento in cui il comando è stato inviato. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser del metodo deve quindi analizzare l'origine fino alla posizione specificata e quindi analizzare l'identificatore nella posizione specificata per determinare cosa visualizzare nella descrizione comando Informazioni rapide.

 La maggior parte dei parser esegui un'analisi iniziale dell'intero file di origine e archivia i risultati in un albero di analisi. L'analisi completa viene <xref:Microsoft.VisualStudio.Package.ParseReason> eseguita <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> quando viene passata al metodo. Altri tipi di analisi possono quindi utilizzare l'albero di analisi per ottenere le informazioni desiderate.

 Ad esempio, il valore <xref:Microsoft.VisualStudio.Package.ParseReason> del motivo di analisi di può trovare l'identificatore nel percorso di origine e cercarlo nell'albero di analisi per ottenere le informazioni sul tipo. Queste informazioni sul tipo <xref:Microsoft.VisualStudio.Package.AuthoringScope> vengono quindi passate alla <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> classe e restituite dal metodo.
