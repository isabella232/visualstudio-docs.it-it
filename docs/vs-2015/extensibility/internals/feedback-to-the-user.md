---
title: Commenti e suggerimenti per l'utente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7773c611733ccec525fc25264311e72c1dfe36e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537680"
---
# <a name="feedback-to-the-user"></a>Commenti e suggerimenti per l'utente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrated Development Environment (IDE), il feedback visivo relativo alla funzionalità disponibile si basa sulla selezione corrente dell'utente e sul contesto di selezione globale. Nella tabella seguente sono elencate le funzionalità disponibili in diversi contesti di selezione.  
  
|Contesto di selezione|Funzionalità disponibili|  
|-----------------------|-----------------------------|  
|IDE|Globale|  
|Set di prodotti corrente|Specifico del prodotto|  
|Gerarchia attiva|Specifico del tipo di gerarchia|  
|Elemento della gerarchia attiva|Specifico del tipo di elemento della gerarchia|  
|Documento attivo|Specifico del tipo di documento|  
|Finestra interfaccia a documenti multipli (MDI) in primo piano|Specifico del tipo di finestra|  
|Contesto di selezione corrente|Specifico del contesto di selezione|  
  
 Se si rilevano solo le funzionalità necessarie agli utenti e si forniscono continuamente Commenti coerenti per la selezione e il contesto dell'ambiente, è possibile ridurre la complessità nell'IDE. Le regole seguenti si applicano ogni volta che una finestra viene aperta nell'IDE:  
  
- Se la finestra cambia il contesto di selezione, il feedback della selezione è chiaramente indicato nella finestra e la finestra Guida dinamica, se visualizzata, viene aggiornata per riflettere il contesto corrente.  
  
- Se la finestra modifica il contesto di selezione globale, tutti i menu specifici del contesto, la finestra gerarchia attiva e la barra del titolo dell'applicazione vengono aggiornati per riflettere il contesto corrente.  
  
- La finestra deve visualizzare le proprietà della selezione corrente nella finestra **Proprietà** e, facoltativamente, se visualizzata, la finestra di dialogo **pagine delle proprietà** .  
  
- Se la finestra non è visibile o modifica il contesto di selezione globale, il feedback della selezione non deve rimanere nella finestra quando non è più la finestra attiva nell'IDE.  
  
- Tutte le finestre degli strumenti specifiche del documento dovrebbero riflettere continuamente il documento attivo.  
  
- I menu, le barre degli strumenti e la barra del titolo dell'applicazione devono riflettere la finestra del client di interfaccia a documenti multipli (MDI) più in alto.  
  
  Ad esempio, quando viene aperta la visualizzazione HTML di un Web Form all'interno di un progetto di applicazione Web Visual Basic e l'utente seleziona un `<td>` tag, il feedback viene fornito nel modo seguente:  
  
- La selezione è indicata nella finestra attiva e viene riflessa nella finestra **Proprietà** .  
  
- La **casella degli strumenti** specifica del documento viene aggiornata per riflettere il documento attivo.  
  
- Vengono visualizzati la barra degli strumenti dell' **Editor** e il menu **tabella** e la barra del titolo viene aggiornata per riflettere la finestra del modulo Web.  
  
- La finestra gerarchia attiva, che in genere si **Esplora soluzioni**, e l'aggiornamento della relativa barra del titolo per riflettere il contesto corrente e i comandi di menu del **progetto** sensibili al contesto sono ora applicabili al progetto di applicazione Web attivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Oggetti contesto selezione](../../extensibility/internals/selection-context-objects.md)   
 [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)
