---
title: Fornire l'automazione per il codice | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: 57d5337ae088560bb94a6af39902e90b6af02686
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060965"
---
# <a name="providing-automation-for-code"></a>Automazione per il codice
La creazione di un modello di automazione per il codice non è obbligatoria. L'SDK dell'ambiente non fornisce un esempio per questa operazione. Per informazioni dettagliate sui modelli di codice, vedere l' <xref:EnvDTE.CodeModel> oggetto.

 Per implementare un modello di codice, è necessario implementare le interfacce determinate dalla struttura dei dati interna. Gli oggetti devono essere derivati dalla `IDispatch` classe.

 Gli oggetti estesi, <xref:EnvDTE.CodeModel> e <xref:EnvDTE.FileCodeModel> , sono disponibili dall' <xref:EnvDTE.Project> oggetto e hanno un aspetto simile al seguente:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 È possibile scegliere di implementare solo l' `CodeModel` interfaccia o `FileCodeModel` nell'oggetto restituito dagli `Project` <xref:EnvDTE.ProjectItem> oggetti e. Fornire tutte le funzionalità di questa interfaccia appropriate per il sistema del progetto.

 Se si desidera aggiungere funzionalità, ad esempio metodi o proprietà, che non sono disponibili dalle `CodeModel` interfacce standard e `FileCodeModel` , creare una propria interfaccia che erediti dallo standard. Assicurarsi di documentarlo con il sistema di progetto in modo che gli utenti finali conoscano la ricerca. Viene restituita l'interfaccia standard, ma l'utente può chiamare il `QueryInterface` metodo o eseguire il cast all'interfaccia se è noto.

## <a name="see-also"></a>Vedi anche
- [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)
