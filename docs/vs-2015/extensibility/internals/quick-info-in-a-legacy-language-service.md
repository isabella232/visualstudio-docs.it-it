---
title: Informazioni rapide in un servizio di linguaggio Legacy | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ba5d6d2c08d6b4d39efe9d662dda7a0e324cbf6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517305"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Informazioni rapide in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [informazioni rapide in un servizio di linguaggio Legacy](https://docs.microsoft.com/visualstudio/extensibility/internals/quick-info-in-a-legacy-language-service).  
  
Informazioni rapide di IntelliSense visualizza informazioni su un identificatore dell'origine quando l'utente posiziona il punto di inserimento nell'identificatore e seleziona **informazioni rapide** dalle **IntelliSense** menu o se mantiene il puntatore del mouse cursore sull'identificatore. In questo modo una descrizione comando venga visualizzato con le informazioni sull'identificatore. Queste informazioni consiste in genere il tipo di identificatore. Quando il motore di debug è attivo, tali informazioni possono includere il valore corrente. Il motore di debug fornisce i valori dell'espressione, mentre il servizio di linguaggio gestisce solo gli identificatori.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni, vedere [procedura dettagliata: visualizzazione di descrizioni comandi informazioni rapide](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 Le classi del servizio gestito del pacchetto framework (MPF) della lingua sono disponibili il supporto completo per visualizzare la descrizione comando informazioni rapide di IntelliSense. Tutto quello che devi fare è fornire il testo per visualizzare e abilitare la funzionalità informazioni rapide.  
  
 Il testo da visualizzare viene ottenuto chiamando il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser di metodo con un valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>. Questo motivo indica al parser di ottenere le informazioni sul tipo (o le informazioni appropriate da visualizzare nella descrizione comando informazioni rapide) per l'identificatore nella posizione specificata nel <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. Il <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto è ciò che è stato passato al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (metodo).  
  
 Il parser deve analizzare tutti gli elementi fino alla posizione nel <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto per determinare i tipi di tutti gli identificatori. Il parser deve quindi ottenere l'identificatore in corrispondenza della posizione di richiesta di analisi. Infine, il parser deve passare i dati di suggerimento dello strumento associati a tale identificatore per il <xref:Microsoft.VisualStudio.Package.AuthoringScope> dell'oggetto in modo che tale oggetto può restituire il testo dal <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> (metodo).  
  
## <a name="enabling-the-quick-info-feature"></a>L'abilitazione della funzionalità informazioni rapide  
 Per abilitare la funzionalità informazioni rapide, è necessario impostare il `CodeSense` e `QuickInfo` parametri di denominati il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Questi attributi impostati i <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> e <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> proprietà.  
  
## <a name="implementing-the-quick-info-feature"></a>Implementa la funzionalità informazioni rapide  
 Il <xref:Microsoft.VisualStudio.Package.ViewFilter> classe gestisce l'operazione di informazioni rapide di IntelliSense. Quando la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe riceve il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando, la classe chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo con il motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> e la posizione del punto di inserimento al momento il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando è stato inviato. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser metodo deve quindi analizzare l'origine fino alla posizione specificata e quindi analizzare l'identificatore nella posizione specificata per determinare quali elementi visualizzare nella descrizione comando informazioni rapide.  
  
 La maggior parte dei parser di eseguire un'analisi iniziale dell'intero file di origine e archiviare i risultati in un albero di analisi. L'analisi completa quando viene eseguita <xref:Microsoft.VisualStudio.Package.ParseReason> viene passato a <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (metodo). Altri tipi di analisi possono quindi usare l'albero di analisi per ottenere le informazioni desiderate.  
  
 Ad esempio, il valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> può trovare l'identificatore in corrispondenza della posizione di origine e cercare nell'albero di analisi per ottenere le informazioni sul tipo. Questo tipo di informazioni viene quindi passato per il <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe e viene restituito dal <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> (metodo).

