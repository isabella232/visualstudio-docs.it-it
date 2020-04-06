---
title: Criteri modello e la finestra Proprietà Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08ed6f416441d06767661e63b5e32454dbe07f93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704670"
---
# <a name="template-policy-and-the-properties-window"></a>Criteri dei modelli e finestra Proprietà
Quando un progetto è contenuto all'interno di un progetto modello enterprise, tale progetto può applicare criteri. I criteri modello diventano un sistema di vincolo che può essere utilizzato per impostare i valori predefiniti per le proprietà, nascondere le proprietà, aggiungere proprietà e così via.

 L'utilizzo dei criteri modello per **Properties** controllare la visualizzazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>delle informazioni nella finestra Proprietà è diverso dall'implementazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>gestisce le proprietà dell'oggetto a livello di componente, mentre i criteri del modello possono essere utilizzati per vincolare le proprietà dell'oggetto a livello di soluzione o di progetto. In altre parole

- Implementare i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> metodi per determinare ciò che viene visualizzato nella finestra **Proprietà** per oggetti specifici

- Usare i criteri modello a livello di soluzione e di progetto per determinare gli elementi visualizzati nella finestra Proprietà per gli oggetti specificati in precedenzaUse template policy at the solution and project level to determine what is displayed in the **Properties** window for previously specified objects

  L'utilizzo dei criteri di modello per vincolare in modo selettivo proprietà specifiche nella finestra **Proprietà** quando viene selezionato un elemento di progetto di un tipo specificato in **Esplora soluzioni** può essere utile per tutti i membri del team di sviluppo che lavorano su un progetto. Ad esempio, utilizzando i criteri di modello, è possibile impostare tutte le informazioni sulla stringa di connessione in un database per gli sviluppatori e rendere la stringa di connessione di sola lettura. In questo modo, è possibile fornire un modo semplice per garantire che ogni sviluppatore utilizzi il percorso corretto per l'accesso ai dati.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
