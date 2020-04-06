---
title: Fornire l'automazione per il codice Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705989"
---
# <a name="providing-automation-for-code"></a>Automazione per il codice
La creazione di un modello di automazione per il codice non è necessaria. L'SDK dell'ambiente non fornisce un esempio per eseguire questa operazione. Per informazioni dettagliate sui <xref:EnvDTE.CodeModel> modelli di codice, vedere l'oggetto.

 Per implementare un modello di codice, è necessario implementare tutte le interfacce determinate dalla struttura di dati interna. Gli oggetti devono essere `IDispatch` derivati dalla classe .

 Gli oggetti che <xref:EnvDTE.CodeModel> si <xref:EnvDTE.FileCodeModel>estendono e <xref:EnvDTE.Project> , sono disponibili dall'oggetto ed è simile al seguente:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 È possibile scegliere di `CodeModel` implementare solo `FileCodeModel` l'interfaccia `Project` nell'oggetto restituito dagli oggetti e . <xref:EnvDTE.ProjectItem> Fornire tutte le funzionalità di questa interfaccia appropriata per il sistema del progetto.

 Se si desidera aggiungere funzionalità, ad esempio metodi o proprietà, che non sono disponibili dallo standard `CodeModel` e `FileCodeModel` dalle interfacce, creare un'interfaccia personalizzata che eredita dallo standard. Assicurarsi di documentarlo con il sistema del progetto in modo che gli utenti finali sappiano di cercarlo. Restituisce l'interfaccia standard, ma `QueryInterface` l'utente può chiamare il metodo o eseguire il cast all'interfaccia se è noto che esiste.

## <a name="see-also"></a>Vedere anche
- [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)
