---
title: Informazioni rapide in un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc8bfff0903d2ed1554cfd8b3d5b1dcf5cf0fa8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839316"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Informazioni rapide in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Informazioni rapide di IntelliSense mostra informazioni su un identificatore nell'origine quando l'utente posiziona il punto di inserimento nell'identificatore e seleziona **informazioni rapide** dal menu di **IntelliSense** o posiziona il cursore del mouse sull'identificatore. In questo modo viene visualizzata una descrizione comando con informazioni sull'identificatore. Queste informazioni sono in genere costituite dal tipo di identificatore. Quando il motore di debug è attivo, queste informazioni possono includere il valore corrente. Il motore di debug fornisce valori di espressione, mentre il servizio di linguaggio gestisce solo gli identificatori.  
  
 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzazione di descrizioni comandi di informazioni rapide](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.  
  
 Le classi del servizio di linguaggio MPF (Managed Package Framework) forniscono supporto completo per la visualizzazione della descrizione comandi di informazioni rapide di IntelliSense. È sufficiente fornire il testo da visualizzare e abilitare la funzionalità informazioni rapide.  
  
 Il testo da visualizzare viene ottenuto chiamando il parser del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo con un valore dell'analisi motivo <xref:Microsoft.VisualStudio.Package.ParseReason> . Questo motivo indica al parser di ottenere le informazioni sul tipo (o qualsiasi altro oggetto appropriato da visualizzare nella descrizione comando informazioni rapide) per l'identificatore in corrispondenza della posizione specificata nell' <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. L' <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto è quello passato al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo.  
  
 Il parser deve analizzare tutti gli elementi fino alla posizione nell' <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto per determinare i tipi di tutti gli identificatori. Il parser deve quindi ottenere l'identificatore in corrispondenza della posizione della richiesta di analisi. Infine, il parser deve passare i dati delle descrizioni comandi associati a tale identificatore all' <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto in modo che l'oggetto possa restituire il testo dal <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metodo.  
  
## <a name="enabling-the-quick-info-feature"></a>Abilitazione della funzionalità informazioni rapide  
 Per abilitare la funzionalità informazioni rapide, è necessario impostare `CodeSense` i `QuickInfo` parametri denominati e di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Questi attributi impostano le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> proprietà e.  
  
## <a name="implementing-the-quick-info-feature"></a>Implementazione della funzionalità informazioni rapide  
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe gestisce l'operazione di informazioni rapide di IntelliSense. Quando la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe riceve il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando, la classe chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo con il motivo dell'analisi <xref:Microsoft.VisualStudio.Package.ParseReason> e la posizione del punto di inserimento al momento dell' <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> invio del comando. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser del metodo deve quindi analizzare l'origine fino al percorso specificato e quindi analizzare l'identificatore nella posizione specificata per determinare gli elementi da visualizzare nella descrizione comando informazioni rapide.  
  
 La maggior parte dei parser esegue un'analisi iniziale dell'intero file di origine e archivia i risultati in un albero di analisi. L'analisi completa viene eseguita quando <xref:Microsoft.VisualStudio.Package.ParseReason> viene passato al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo. Altri tipi di analisi possono quindi utilizzare l'albero di analisi per ottenere le informazioni desiderate.  
  
 Ad esempio, il valore del motivo dell'analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> può trovare l'identificatore nella posizione di origine e cercarlo nell'albero di analisi per ottenere le informazioni sul tipo. Queste informazioni sul tipo vengono quindi passate alla <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe e vengono restituite dal <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metodo.
