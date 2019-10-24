---
title: Criteri dei modelli e finestra Proprietà | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7135a7c99f1566eaacb4079e9787cf2b5606682
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722686"
---
# <a name="template-policy-and-the-properties-window"></a>Criteri dei modelli e finestra Proprietà
Quando un progetto è contenuto all'interno di un progetto modello Enterprise, il progetto modello Enterprise può applicare i criteri. Il criterio dei modelli diventa un sistema vincolante che può essere usato per impostare i valori predefiniti per le proprietà, nascondere proprietà, aggiungere proprietà e così via.

 L'utilizzo di criteri modello per controllare la visualizzazione delle informazioni nella finestra **Proprietà** è diverso dall'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> gestisce le proprietà degli oggetti a livello di componente, mentre i criteri dei modelli possono essere usati per vincolare le proprietà degli oggetti a livello di soluzione o di progetto. In altre parole

- Implementare i metodi su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> per determinare gli elementi visualizzati nella finestra **Proprietà** per oggetti specifici

- Usare i criteri dei modelli a livello di soluzione e di progetto per determinare gli elementi visualizzati nella finestra **Proprietà** per gli oggetti specificati in precedenza

  L'uso di criteri modello per vincolare selettivamente proprietà specifiche nella finestra **Proprietà** quando viene selezionato un elemento del progetto di un tipo specificato in **Esplora soluzioni** può essere utile per tutti i membri del team di sviluppo che lavorano su un progetto. Usando, ad esempio, i criteri dei modelli, è possibile configurare tutte le informazioni della stringa di connessione in un database per gli sviluppatori e rendere la stringa di connessione di sola lettura. In questo modo, è possibile fornire un modo semplice per assicurare che ogni sviluppatore usi il percorso corretto per l'accesso ai dati.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)