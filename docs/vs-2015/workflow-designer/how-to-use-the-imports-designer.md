---
title: 'Procedura: Utilizzare la finestra di progettazione importazioni | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c6eed27b9bfef272035f299af1a68a3788587f3c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955361"
---
# <a name="how-to-use-the-imports-designer"></a>Procedura: Usare la finestra di progettazione importazioni
La finestra di progettazione importazioni consente di immettere gli spazi dei nomi per i tipi usati nelle espressioni. In modo analogo i **importazioni** o **usando** parole chiave in Visual Basic .NET e C#, che specifica gli spazi dei nomi nella finestra di progettazione importazioni consentono di immettere semplicemente un nome di tipo nell'espressione anziché un nome completo nome del tipo di versione.  
  
 Sulla finestra di progettazione importazioni influiscono sia le modifiche all'interfaccia utente che quelle eseguite quando viene salvato il flusso di lavoro. Quando viene salvato il flusso di lavoro, alla finestra di progettazione importazioni è possibile aggiungere automaticamente spazi dei nomi, tra cui:  
  
- Spazi dei nomi per qualsiasi tipo usato nelle dichiarazioni di variabili e argomenti.  
  
- Spazi dei nomi per qualsiasi tipo usato nelle espressioni.  
  
- Qualsiasi altro spazio dei nomi necessario per la serializzazione del flusso di lavoro (ad esempio, gli spazi dei nomi usati da attività personalizzate rilasciate nel flusso di lavoro).  
  
  Quando viene salvato il flusso di lavoro, è possibile notare che alcuni spazi dei nomi eliminati manualmente sono stati aggiunti di nuovo automaticamente alla finestra di progettazione importazioni a causa della logica descritta nell'elenco precedente.  
  
### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Per aggiungere uno spazio dei nomi all'elenco degli spazi dei nomi importati  
  
1.  Aprire un'applicazione di servizi di flussi di lavoro WCF, un'applicazione console del flusso di lavoro o un progetto Libreria attività in [!INCLUDE[vs2010](../includes/vs2010-md.md)] o in un'applicazione flusso di lavoro riallocata.  
  
2.  Fare clic su **importazioni** nella parte inferiore dell'area di disegno principale. Verrà visualizzata la finestra di progettazione importazioni.  
  
3.  Immettere o selezionare uno spazio dei nomi dal controllo dell'elenco a discesa nella parte superiore della finestra di progettazione importazioni.  
  
     Mentre si digita, viene visualizzato un elenco degli spazi dei nomi validi che corrispondono ai caratteri tipizzati.  
  
4.  Premere **invio** per aggiungere lo spazio dei nomi all'elenco.  
  
5.  Se si desidera rimuovere uno spazio dei nomi nell'elenco, selezionare lo spazio dei nomi e quindi premere il **eliminare** sulla tastiera. Si noti che è possibile eliminare uno spazio dei nomi solo se non è valido per qualsiasi motivo, ad esempio se il progetto non fa più riferimento all'assembly che lo contiene.