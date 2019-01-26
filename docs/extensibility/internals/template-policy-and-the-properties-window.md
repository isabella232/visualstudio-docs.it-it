---
title: Criteri dei modelli e la finestra proprietà | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b09d8dd21e65d1320aa6de78337ee8959fc42656
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001810"
---
# <a name="template-policy-and-the-properties-window"></a>Criteri dei modelli e finestra Proprietà
Quando un progetto è contenuto all'interno di un progetto di modello aziendale, tale progetto di modello dell'organizzazione possa applicare criteri. Criteri dei modelli diventa un sistema vincolante che può essere utilizzato per impostare i valori predefiniti per le proprietà, nascondere le proprietà, aggiungere le proprietà e così via.  
  
 Usando i criteri dei modelli per controllare la visualizzazione delle informazioni nel **delle proprietà** finestra è diversa dall'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> gestisce le proprietà dell'oggetto a livello di componente, mentre i criteri dei modelli può essere utilizzato per vincolare le proprietà dell'oggetto a livello di soluzione o progetto. In altre parole  
  
- Implementare i metodi sui <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> per determinare gli elementi visualizzati nei **proprietà** finestra per oggetti specifici  
  
- Usare i criteri dei modelli a livello di soluzione e progetto per determinare gli elementi visualizzati nei **proprietà** finestra per gli oggetti specificati in precedenza  
  
  Usando i criteri dei modelli per applicare un vincolo in modo selettivo le proprietà specifiche nel **delle proprietà** finestra quando un elemento del progetto di un tipo specificato viene selezionato in **Esplora soluzioni** può essere utile per tutti i membri di il team di sviluppo lavorando a un progetto. Usa i criteri dei modelli, ad esempio, è possibile configurare tutte le informazioni della stringa di connessione in un database per gli sviluppatori e rendere la stringa di connessione di sola lettura. In tal modo, è possibile fornire un modo semplice per garantire che ogni sviluppatore utilizza il percorso corretto per accedere ai dati.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)