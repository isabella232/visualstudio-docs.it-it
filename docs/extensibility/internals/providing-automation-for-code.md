---
title: Fornire l'automazione per l'| Microsoft Docs
description: Informazioni sull'implementazione di un modello di codice, che richiede l'implementazione di interfacce determinate dalla struttura dei dati interna.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 705fa036bdb0d76d02e9d4fcd540c3f3450c4f06
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636083"
---
# <a name="providing-automation-for-code"></a>Automazione per il codice
La creazione di un modello di automazione per il codice non è necessaria. Environment SDK non fornisce un esempio per questa operazione. Per informazioni dettagliate sui modelli di codice, vedere <xref:EnvDTE.CodeModel> l'oggetto .

 Per implementare un modello di codice, è necessario implementare tutte le interfacce determinate dalla struttura dei dati interna. Gli oggetti devono essere derivati dalla `IDispatch` classe .

 Gli oggetti che si estendono, e , sono <xref:EnvDTE.CodeModel> <xref:EnvDTE.FileCodeModel> disponibili <xref:EnvDTE.Project> dall'oggetto e hanno un aspetto simile al seguente:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 È possibile scegliere di implementare solo `CodeModel` l'interfaccia o `FileCodeModel` nell'oggetto restituito dagli `Project` oggetti e <xref:EnvDTE.ProjectItem> . Fornire qualsiasi funzionalità di questa interfaccia appropriata per il sistema del progetto.

 Se si desidera aggiungere funzionalità, ad esempio metodi o proprietà, che non sono disponibili dalle interfacce e standard, creare un'interfaccia personalizzata che eredita `CodeModel` `FileCodeModel` dallo standard. Assicurarsi di documentarlo con il sistema del progetto in modo che gli utenti finali sappiano cercarlo. Viene restituita l'interfaccia standard, ma l'utente può chiamare il metodo o eseguire il cast all'interfaccia se è `QueryInterface` noto che esiste.

## <a name="see-also"></a>Vedi anche
- [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)
