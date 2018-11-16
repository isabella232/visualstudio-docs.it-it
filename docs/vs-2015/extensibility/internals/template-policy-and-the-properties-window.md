---
title: Criteri dei modelli e la finestra proprietà | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 695b65d65d03717dd2c2579584d61227ecf447cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767316"
---
# <a name="template-policy-and-the-properties-window"></a>Criteri dei modelli e finestra Proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando un progetto è contenuto all'interno di un progetto di modello aziendale, tale progetto di modello dell'organizzazione possa applicare criteri. Criteri dei modelli diventa un sistema vincolante che può essere utilizzato per impostare i valori predefiniti per le proprietà, nascondere le proprietà, aggiungere le proprietà e così via.  
  
 Usando i criteri dei modelli per controllare la visualizzazione delle informazioni nel **delle proprietà** finestra è diversa dall'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> gestisce le proprietà dell'oggetto a livello di componente, mentre i criteri dei modelli può essere utilizzato per vincolare le proprietà dell'oggetto a livello di soluzione o progetto. In altre parole  
  
- Implementare i metodi sui <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> per determinare gli elementi visualizzati nei **proprietà** finestra per oggetti specifici  
  
- Usare i criteri dei modelli a livello di soluzione e progetto per determinare gli elementi visualizzati nei **proprietà** finestra per gli oggetti specificati in precedenza  
  
  Usando i criteri dei modelli per applicare un vincolo in modo selettivo le proprietà specifiche nel **delle proprietà** finestra quando un elemento del progetto di un tipo specificato viene selezionato in **Esplora soluzioni** può essere utile per tutti i membri di il team di sviluppo lavorando a un progetto. Usa i criteri dei modelli, ad esempio, è possibile configurare tutte le informazioni della stringa di connessione in un database per gli sviluppatori e rendere la stringa di connessione di sola lettura. In tal modo, è possibile fornire un modo semplice per garantire che ogni sviluppatore utilizza il percorso corretto per accedere ai dati.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)

