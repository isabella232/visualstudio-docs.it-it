---
title: Commenti e suggerimenti all'utente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9213440d0c3c3dbaa7c95e45bbf61386b60ff46
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016187"
---
# <a name="feedback-to-the-user"></a>Commenti e suggerimenti all'utente
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE), un feedback visivo relative alle funzionalità disponibili è basata sulla selezione corrente dell'utente e il contesto di selezione globale. La tabella seguente elenca le funzionalità disponibili in contesti differenti.  
  
|Contesto di selezione|Funzionalità disponibili|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Set di prodotti corrente|Prodotto specifico|  
|Gerarchia attiva|Specifica tipo di gerarchia|  
|Elemento della gerarchia attivo|Specifiche di tipo elemento di gerarchia|  
|Documento attivo|Specifica tipo di documento|  
|Finestra di interfaccia a documenti multipli (MDI) in primo piano|Specifica tipo di finestra|  
|Contesto della selezione corrente|Contesto di selezione specifico|  
  
 Se si della superficie di attacco solo le funzionalità necessarie agli utenti e offrono continuamente selezione coerente e commenti e suggerimenti contesto di ambiente, si riduce la complessità dell'IDE. Le regole seguenti si applicano ogni volta che viene aperta una finestra dell'IDE:  
  
- Se la finestra viene modificato il contesto di selezione, il feedback della selezione è indicata chiaramente nella finestra di e il **Guida dinamica** finestra, se visualizzata, viene aggiornato per riflettere il contesto corrente.  
  
- Se la finestra viene modificato il contesto di selezione globale, tutti i menu specifici del contesto, la finestra gerarchia attivo e la barra del titolo dell'applicazione vengono aggiornate per riflettere il contesto corrente.  
  
- La finestra dovrebbe segnalare le proprietà per la selezione corrente nella **delle proprietà** finestra e, facoltativamente, se visualizzata, il **pagine delle proprietà** nella finestra di dialogo.  
  
- Se la finestra non le proprietà della superficie di attacco o modificare il contesto di selezione globale, commenti e suggerimenti di selezione non devono rimanere nella finestra quando non è più la finestra attiva nell'IDE.  
  
- Tutte le finestre degli strumenti specifici del documento devono riflettere continuamente il documento attivo.  
  
- Menu, barre degli strumenti e la barra del titolo dell'applicazione deve riflettere la finestra client di livello più alto interfaccia a documenti multipli (MDI).  
  
  Ad esempio, quando il codice HTML Visualizza di un **Web Form** all'interno di un'applicazione Web di Visual Basic progetto è aperto e l'utente seleziona un `<td>` tag, viene fornito un feedback nel modo seguente:  
  
- La selezione è indicata nella finestra attiva e applicata le **proprietà** finestra.  
  
- La specifica del documento **casella degli strumenti** viene aggiornato per riflettere il documento attivo.  
  
- Il **Editor** sulla barra degli strumenti e **tabella** vengono visualizzati menu e la barra del titolo aggiorna in modo da riflettere la finestra del Web Form.  
  
- La finestra gerarchia attiva in cui è in genere **Esplora soluzioni**e l'aggiornamento della barra del titolo in modo da riflettere il contesto corrente e il sensibile al contesto **progetto** i comandi di menu ora applicano al Web attivo Progetto di applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Oggetti di contesto di selezione](../../extensibility/internals/selection-context-objects.md)   
 [Le gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)