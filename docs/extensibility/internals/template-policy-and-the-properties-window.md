---
title: Criteri dei modelli e finestra Proprietà | Microsoft Docs
description: Informazioni sull'uso dei criteri dei modelli per impostare i valori predefiniti per le proprietà, nascondere le proprietà e aggiungere proprietà nell'Finestra Proprietà.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40f29eb5da5c8377c31a39a1e55868bf89f444a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898249"
---
# <a name="template-policy-and-the-properties-window"></a>Criteri dei modelli e finestra Proprietà
Quando un progetto è contenuto all'interno di un progetto modello Enterprise, il progetto modello Enterprise può applicare i criteri. Il criterio dei modelli diventa un sistema vincolante che può essere usato per impostare i valori predefiniti per le proprietà, nascondere proprietà, aggiungere proprietà e così via.

 L'utilizzo di criteri modello per controllare la visualizzazione delle informazioni nella finestra **Proprietà** è diverso dall'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> gestisce le proprietà degli oggetti a livello di componente, mentre i criteri dei modelli possono essere usati per vincolare le proprietà dell'oggetto a livello di soluzione o di progetto. In altre parole

- Implementare i metodi su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> per determinare gli elementi visualizzati nella finestra **Proprietà** per oggetti specifici

- Usare i criteri dei modelli a livello di soluzione e di progetto per determinare gli elementi visualizzati nella finestra **Proprietà** per gli oggetti specificati in precedenza

  L'uso di criteri modello per vincolare selettivamente proprietà specifiche nella finestra **Proprietà** quando viene selezionato un elemento del progetto di un tipo specificato in **Esplora soluzioni** può essere utile per tutti i membri del team di sviluppo che lavorano su un progetto. Usando, ad esempio, i criteri dei modelli, è possibile configurare tutte le informazioni della stringa di connessione in un database per gli sviluppatori e rendere la stringa di connessione di sola lettura. In questo modo, è possibile fornire un modo semplice per assicurare che ogni sviluppatore usi il percorso corretto per l'accesso ai dati.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
