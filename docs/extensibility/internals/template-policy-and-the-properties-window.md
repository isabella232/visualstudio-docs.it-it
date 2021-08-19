---
title: Criteri modello e finestra Proprietà | Microsoft Docs
description: Informazioni sull'uso dei criteri di modello per impostare i valori predefiniti per le proprietà, nascondere le proprietà e aggiungere proprietà nel Finestra Proprietà.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 84f08740ac47701506f37e3e3aababa329f1ef61
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158801"
---
# <a name="template-policy-and-the-properties-window"></a>Criteri dei modelli e finestra Proprietà
Quando un progetto è contenuto all'interno di un progetto modello Enterprise, tale progetto può applicare i criteri. I criteri modello diventano un sistema di vincoli che può essere usato per impostare i valori predefiniti per le proprietà, nascondere le proprietà, aggiungere proprietà e così via.

 L'uso dei criteri di modello per controllare la visualizzazione delle informazioni nella **finestra** Proprietà è diverso dall'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> gestisce le proprietà degli oggetti a livello di componente, mentre i criteri del modello possono essere usati per vincolare le proprietà degli oggetti a livello di soluzione o di progetto. In altre parole

- Implementare i metodi su per determinare ciò che <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> viene visualizzato nella finestra **Proprietà** per oggetti specifici

- Usare i criteri di modello a livello di soluzione e di progetto per determinare ciò che viene visualizzato nella finestra **Proprietà** per gli oggetti specificati in precedenza

  L'uso dei criteri di modello per  vincolare in modo selettivo proprietà specifiche nella finestra Proprietà quando un elemento di progetto di un tipo specificato viene selezionato in **Esplora soluzioni** può essere utile per tutti i membri del team di sviluppo che lavorano a un progetto. Ad esempio, usando i criteri di modello, è possibile configurare tutte le informazioni sulla stringa di connessione in un database per gli sviluppatori e rendere la stringa di connessione di sola lettura. In questo modo, è possibile fornire un modo semplice per garantire che ogni sviluppatore usi il percorso corretto per l'accesso ai dati.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
