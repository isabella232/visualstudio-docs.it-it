---
title: Criteri dei modelli e finestra Proprietà | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c67150c5a71a3d70df85669319795a405c60f4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156017"
---
# <a name="template-policy-and-the-properties-window"></a>Criteri dei modelli e finestra Proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando un progetto è contenuto all'interno di un progetto modello Enterprise, il progetto modello Enterprise può applicare i criteri. Il criterio dei modelli diventa un sistema vincolante che può essere usato per impostare i valori predefiniti per le proprietà, nascondere proprietà, aggiungere proprietà e così via.  
  
 L'utilizzo di criteri modello per controllare la visualizzazione delle informazioni nella finestra **Proprietà** è diverso dall'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> gestisce le proprietà degli oggetti a livello di componente, mentre i criteri dei modelli possono essere usati per vincolare le proprietà dell'oggetto a livello di soluzione o di progetto. In altre parole  
  
- Implementare i metodi su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> per determinare gli elementi visualizzati nella finestra **Proprietà** per oggetti specifici  
  
- Usare i criteri dei modelli a livello di soluzione e di progetto per determinare gli elementi visualizzati nella finestra **Proprietà** per gli oggetti specificati in precedenza  
  
  L'uso di criteri modello per vincolare selettivamente proprietà specifiche nella finestra **Proprietà** quando viene selezionato un elemento del progetto di un tipo specificato in **Esplora soluzioni** può essere utile per tutti i membri del team di sviluppo che lavorano su un progetto. Usando, ad esempio, i criteri dei modelli, è possibile configurare tutte le informazioni della stringa di connessione in un database per gli sviluppatori e rendere la stringa di connessione di sola lettura. In questo modo, è possibile fornire un modo semplice per assicurare che ogni sviluppatore usi il percorso corretto per l'accesso ai dati.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
